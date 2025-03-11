FullStack Blogging App
Project Overview
This is a full-stack blogging application with a** CI/CD** pipeline for automated deployment. The application allows users to register, log in, create blog posts, and explore content. It is designed using modern web technologies and DevOps best practices.

**CI/CD Pipeline Architecture**
Below is the CI/CD pipeline implemented for automated build, test, and deployment:
![image](https://github.com/user-attachments/assets/55768031-94a3-462a-a328-7a79119f00ae)


🛠️ Local Setup
Prerequisites
Ensure you have the following installed on your local machine:

<ul> <li>Git</li> <li>Node.js & npm (for frontend)</li> <li>Java 17 & Maven (for backend)</li> <li>MySQL</li> <li>Docker (for containerization)</li> </ul>
Steps to Run Locally
Clone the Repository
bash
Copy
Edit
git clone https://github.com/b-v-krishna/FullStack-Blogging-App.git
cd FullStack-Blogging-App
Setup MySQL Database
Create a database in MySQL named blogging_app
Update the application.properties file in the backend with DB credentials.
Run the Backend (Spring Boot)
bash
Copy
Edit
cd backend
mvn clean install
mvn spring-boot:run
Run the Frontend (React.js)
bash
Copy
Edit
cd frontend
npm install
npm start
Access the Application
Frontend: http://localhost:3000
Backend API: http://localhost:8080
🐳 Dockerizing the Application
Build & Run with Docker
Build Docker Images
bash
Copy
Edit
docker build -t blogging-app-backend ./backend
docker build -t blogging-app-frontend ./frontend
Run Containers
bash
Copy
Edit
docker-compose up -d
☸️ Kubernetes Deployment
Deploying to AWS EKS
Apply Kubernetes Manifests
bash
Copy
Edit
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
Check Running Pods & Services
bash
Copy
Edit
kubectl get pods
kubectl get svc
Access the Application
Retrieve the LoadBalancer URL:

bash
Copy
Edit
kubectl get svc
⚙️ CI/CD Pipeline (Jenkins)
Jenkins Pipeline Flow
📌 Code Push (GitHub) → Jenkins Trigger → Build & Test → SonarQube Analysis → Docker Image Build → Push to DockerHub → Kubernetes Deployment

Trigger Jenkins Pipeline
➡️ Go to Jenkins Dashboard → Start the pipeline manually OR set up a webhook from GitHub.

🧹 Destroy Resources
To remove all infrastructure and deployments:

bash
Copy
Edit
terraform destroy
kubectl delete -f k8s/
docker-compose down
