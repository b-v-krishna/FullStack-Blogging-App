# FullStack Blogging App

## Project Overview
This is a full-stack blogging application with a **CI/CD** pipeline for automated deployment. This application allows users to register, log in, create blog posts, and explore content.

## 🚀 CI/CD Pipeline Architecture
Below is the CI/CD pipeline implemented for automated build, test, and deployment:  

![CI/CD Pipeline](https://github.com/user-attachments/assets/55768031-94a3-462a-a328-7a79119f00ae)

---

## 🛠️ Local Setup

### Prerequisites
Ensure you have the following installed on your local machine:

- Git
- Node.js & npm (for frontend)
- Java 17 & Maven (for backend)
- MySQL
- Docker (for containerization)
- Kubectl (for Kubernetes)

### Steps to Run Locally

#### Clone the Repository
```bash
git clone https://github.com/b-v-krishna/FullStack-Blogging-App.git
cd FullStack-Blogging-App
```
**Setup MySQL Database**
Create a database in MySQL named blogging_app
Update the application.properties file in the backend with DB credentials.

**Run the Backend (Spring Boot)**
```
cd backend
mvn clean install
mvn spring-boot:run
```
**Run the Frontend (React.js)**
```
cd frontend
npm install
npm start
```
**Access the Application**
- Frontend: http://localhost:3000
- Backend API: http://localhost:8080

🚀 DevOps Tools Used

DevOps & Infrastructure
- Version Control: GitHub
- CI/CD Pipeline: Jenkins
- Infrastructure as Code (IaC): Terraform
- Containerization: Docker
- Orchestration: Kubernetes (AWS EKS)
- Security & Code Analysis: SonarQube
- Artifact Management: Nexus Repository
  
<h3>License</h3>

This project is licensed under the MIT License.
