<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FullStack Blogging App - README</title>
</head>
<body>

    <h1>FullStack Blogging App</h1>

    <h2>Project Overview</h2>
    <p>
        This is a full-stack blogging application with a <b>CI/CD</b> pipeline for automated deployment. 
        The application allows users to register, log in, create blog posts, and explore content. 
        It is designed using modern web technologies and DevOps best practices.
    </p>

    <h2>📌 CI/CD Pipeline Architecture</h2>
    <p>Below is the CI/CD pipeline implemented for automated build, test, and deployment:</p>
    <img src="https://github.com/user-attachments/assets/55768031-94a3-462a-a328-7a79119f00ae" alt="CI/CD Pipeline" width="800">

    <hr>

    <h2>🛠️ Local Setup</h2>
    
    <h3>Prerequisites</h3>
    <p>Ensure you have the following installed on your local machine:</p>
    <ul>
        <li>Git</li>
        <li>Node.js & npm (for frontend)</li>
        <li>Java 17 & Maven (for backend)</li>
        <li>MySQL</li>
        <li>Docker (for containerization)</li>
    </ul>

    <h3>Steps to Run Locally</h3>

    <h4>Clone the Repository</h4>
    <pre><code>
git clone https://github.com/b-v-krishna/FullStack-Blogging-App.git
cd FullStack-Blogging-App
    </code></pre>

    <h4>Setup MySQL Database</h4>
    <p>Create a database in MySQL named <b>blogging_app</b>.</p>
    <p>Update the <b>application.properties</b> file in the backend with DB credentials.</p>

    <h4>Run the Backend (Spring Boot)</h4>
    <pre><code>
cd backend
mvn clean install
mvn spring-boot:run
    </code></pre>

    <h4>Run the Frontend (React.js)</h4>
    <pre><code>
cd frontend
npm install
npm start
    </code></pre>

    <h4>Access the Application</h4>
    <p>Frontend: <a href="http://localhost:3000">http://localhost:3000</a></p>
    <p>Backend API: <a href="http://localhost:8080">http://localhost:8080</a></p>

    <hr>

    <h2>🐳 Dockerizing the Application</h2>

    <h3>Build & Run with Docker</h3>

    <h4>Build Docker Images</h4>
    <pre><code>
docker build -t blogging-app-backend ./backend
docker build -t blogging-app-frontend ./frontend
    </code></pre>

    <h4>Run Containers</h4>
    <pre><code>
docker-compose up -d
    </code></pre>

    <hr>

    <h2>☸️ Kubernetes Deployment</h2>

    <h3>Deploying to AWS EKS</h3>

    <h4>Apply Kubernetes Manifests</h4>
    <pre><code>
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
    </code></pre>

    <h4>Check Running Pods & Services</h4>
    <pre><code>
kubectl get pods
kubectl get svc
    </code></pre>

    <h4>Access the Application</h4>
    <p>Retrieve the LoadBalancer URL:</p>
    <pre><code>
kubectl get svc
    </code></pre>

    <hr>

    <h2>⚙️ CI/CD Pipeline (Jenkins)</h2>

    <h3>Jenkins Pipeline Flow</h3>
    <p>📌 Code Push (GitHub) → Jenkins Trigger → Build & Test → SonarQube Analysis → Docker Image Build → Push to DockerHub → Kubernetes Deployment</p>

    <h3>Trigger Jenkins Pipeline</h3>
    <p>➡️ Go to <b>Jenkins Dashboard</b> → Start the pipeline manually OR set up a webhook from GitHub.</p>

    <hr>

    <h2>🧹 Destroy Resources</h2>
    <p>To remove all infrastructure and deployments:</p>
    <pre><code>
terraform destroy
kubectl delete -f k8s/
docker-compose down
    </code></pre>

</body>
</html>
