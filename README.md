# Brain Tasks App - Production Deployment

This project demonstrates deploying a React application to a production-ready environment using Docker, AWS ECR, Kubernetes (EKS), and a CI/CD pipeline with AWS CodeBuild, CodeDeploy, and CodePipeline.

## Table of Contents

- [Project Overview](#project-overview)
- [Setup Instructions](#setup-instructions)
- [Dockerization](#dockerization)
- [AWS ECR](#aws-ecr)
- [Kubernetes (EKS)](#kubernetes-eks)
- [CI/CD Pipeline](#cicd-pipeline)
- [Monitoring](#monitoring)
- [Submission](#submission)

---

## Project Overview

- Clone and run the React application on port 3000.
- Dockerize the application.
- Push Docker image to AWS ECR.
- Deploy to AWS EKS using Kubernetes manifests.
- Automate build and deployment using AWS CodeBuild, CodeDeploy, and CodePipeline.
- Monitor using CloudWatch Logs.

---

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Vennilavan12/Brain-Tasks-App.git
   cd Brain-Tasks-App
   ```

2. **Run Locally**
   ```bash
   npm install
   npm start
   # App runs on http://localhost:3000
   ```

---

## Dockerization

1. **Build Docker Image**
   ```bash
   docker build -t brain-tasks-app .
   ```

2. **Run Docker Container**
   ```bash
   docker run -p 3000:3000 brain-tasks-app
   ```

---

## AWS ECR

1. **Create ECR Repository**
   ```bash
   aws ecr create-repository --repository-name brain-tasks-app
   ```

2. **Push Docker Image**
   ```bash
   aws ecr get-login-password | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com
   docker tag brain-tasks-app:latest <account-id>.dkr.ecr.<region>.amazonaws.com/brain-tasks-app:latest
   docker push <account-id>.dkr.ecr.<region>.amazonaws.com/brain-tasks-app:latest
   ```

---

## Kubernetes (EKS)

1. **Setup EKS Cluster**  
   Create an EKS cluster using AWS Console or CLI.

2. **Apply Kubernetes Manifests**
   ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

3. **Get LoadBalancer Details**
   ```bash
   kubectl get svc
   ```

---

## CI/CD Pipeline

- **CodeBuild:** Connect to GitHub, use managed image, define build steps in `buildspec.yml`.
- **CodeDeploy:** Create application, define deployment steps in `appspec.yml`.
- **CodePipeline:** Source from GitHub, build with CodeBuild, deploy with CodeDeploy or EKS.

---

## Monitoring

- Use AWS CloudWatch Logs to monitor build, deployment, and application logs.

---

## Submission

- **GitHub Link:** [Your repository URL]
- **README:** This file with setup instructions and pipeline explanation.
- **Application LoadBalancer ARN:**  
  ```
  <Your LoadBalancer ARN>
  ```
