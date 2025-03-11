pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME = tool 'sonar-scanner' 
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/b-v-krishna/FullStack-Blogging-App.git'
            }
        }
        stage('Compile') {
            steps {
                sh "mvn compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.host.url=http://172.31.16.125:9000 \
                    -Dsonar.projectKey=Blogging-app \
                    -Dsonar.projectName=Blogging-app \
                    -Dsonar.java.binaries=target
                    '''
                }
            }
        }
        stage('Maven Package') {
            steps {
                sh "mvn package"
            }
        }
        stage('Publish Artifacts') {
            steps {
                withMaven(globalMavenSettingsConfig: 'maven-settings', jdk: 'jdk17', maven: 'maven3', mavenSettingsConfig: '', traceability: true) {
                    sh "mvn deploy"
                }
            }
        }
stages {
        stage('Docker build & Tag') {
            steps {
                withDockerRegistry([credentialsId: 'docker-token', url: 'https://index.docker.io/v1/']) {
                    sh "docker build -t bvkrishnakaturi7844/blogging-app:latest ."
                }
            }
        }

        stage('Docker Push') {
            steps {
                withDockerRegistry([credentialsId: 'docker-token', url: 'https://index.docker.io/v1/']) {
                    sh "docker push bvkrishnakaturi7844/blogging-app:latest"
                }
            }
        }
stage('K8-Deploy') {
    steps {
        withKubeConfig(caCertificate: '', clusterName: 'devopsshack-cluster', contextName: '', credentialsId: 'k8-cred', namespace: 'web-apps') {
            sh "kubectl apply -f deployment-service.yml"
            sleep 20
        }
    }
}

stage('Verify the Deployment') {
    steps {
        withKubeConfig(caCertificate: '', clusterName: 'devopsshack-cluster', contextName: '', credentialsId: 'k8-cred', namespace: 'web-apps') {
            sh "kubectl get pods"
            sh "kubectl get svc"
        }
    }
}

    }
post {
    always {
        script {
            def jobName = env.JOB_NAME
            def buildNumber = env.BUILD_NUMBER
            def pipelineStatus = currentBuild.result ?: 'UNKNOWN'
            def bannerColor = pipelineStatus.toUpperCase() == 'SUCCESS' ? 'green' : 'red'

            def body = """
            <html>
            <body>
            <div style="border: 4px solid ${bannerColor}; padding: 10px;">
            <h2>${jobName} - Build ${buildNumber}</h2>
            <div style="background-color: ${bannerColor}; padding: 10px;">
            <h3 style="color: white;">Pipeline Status: ${pipelineStatus.toUpperCase()}</h3>
            </div>
            <p>Check the <a href="${BUILD_URL}">console output</a>.</p>
            </div>
            </body>
            </html>
            """
            
            emailext (
                subject: "${jobName} - Build ${buildNumber} - ${pipelineStatus.toUpperCase()}",
                body: body,
                to: 'bvkrishnakaturi7844@gmail.com',
                from: 'jenkins@example.com',
                replyTo: 'jenkins@example.com',
                mimeType: 'text/html',
            )
        }
    }
}

}
