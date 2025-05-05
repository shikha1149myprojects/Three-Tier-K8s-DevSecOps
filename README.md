# Three-Tier-K8s-DevSecOps  

## Overview  
This project demonstrates the deployment of a secure, scalable, and efficient three-tier architecture using Kubernetes on AWS EKS. The setup incorporates DevSecOps principles, leveraging various tools and technologies for CI/CD pipelines, monitoring, and code quality assurance.  I have used MacOS for the same.

### Key Features  
- **Three-tier architecture**: Frontend (React), Backend (Django, Python), Database (PostgreSQL).  
- **DevSecOps pipeline**: Jenkins, SonarQube, ArgoCD for CI/CD.  
- **Monitoring and visualization**: Prometheus and Grafana.  
- **Cloud-native infrastructure**: AWS EKS, S3, DynamoDB, and IAM integration.  

---

## Tools Used  
### Cloud Services  
- **AWS EKS**: Kubernetes cluster orchestration.  
- **AWS EC2**: Jenkins server and SonarQube setup.  
- **AWS S3**: Storage for Terraform state files.  
- **AWS DynamoDB**: Lock files for Terraform state management.  
- **AWS IAM**: Role and policy management.  
- **AWS ECR**: Docker image repositories.  

### CI/CD Tools  
- **Jenkins**: CI/CD pipeline creation and integration.  
- **ArgoCD**: Kubernetes-native continuous deployment.  

### Monitoring and Visualization  
- **Prometheus**: Metrics and alerting.  
- **Grafana**: Visualization and dashboards.  

### Infrastructure as Code  
- **Terraform**: Automated infrastructure setup.
- **Helm**: Simplifies Kubernetes application deployments, such as load balancer controllers and Prometheus/Grafana setup.  

### Development Tools  
- **Git**: Version control.  
- **SonarQube**: Code quality assurance and analysis.
- **Trivy**: Security vulnerability scanning for container images.

---

## Step-by-Step Guide  

### 1. IAM User Setup  
- **User**: `KingOfPirates`.  
- **Permissions**: `AdministratorAccess`.  
- **Access Key**: ``.  
- **Secret Access Key**: ``.  

---

### 2. Terraform & AWS CLI Installation  
- Install **Terraform** and **AWS CLI** on Mac.

<img width="585" alt="terraform-and-aws-installed" src="https://github.com/user-attachments/assets/659907d9-7f07-461b-95c3-41aab6c2447a" />


---

### 3. Configure AWS CLI  
- Configure AWS  
- Provide access key, secret access key, and region

--- 

### 4. AWS S3 Bucket & DynamoDB Table
- Create S3 Bucket 
- Create DynamoDB Table
- Create Partition Key

---

### 5. Jenkins Server Setup
- Initialize Terraform
- Validate Terraform to check if there are no errors
- Create Key Pair 
- Create infrastructure for the Jenkins Server
<img width="585" alt="jenkins-server-browser-5" src="https://github.com/user-attachments/assets/c63f380e-8306-4c25-a137-fb4e9e8e2b74">
<img width="585" alt="jenkins-server-running-instance" src="https://github.com/user-attachments/assets/592392bc-2342-4161-9aac-29463d78c27a" />
---


### 6. SSH to EC2 Instance:

- SSH to EC2 Instance
- Configure AWS on Jenkins Server and Access Jenkins on Browser

--- 

### 7. Install Plugins on Jenkins
- Install the following plugins on Jenkins:
1. AWS Credentials
2. Pipeline AWS Steps
3. Docker
4. NodeJS
5. SonarQube Scanner
6. OWASP Dependency Check
7. Eclipse Temurin Installer

---

### 8. SonarQube Integration
- Access SonarQube on the Browser
- Create Projects for frontend and backend
- Integrate SonarQube with Jenkins for both frontend and backend
- Create Sonar Token
- Create Webhooks

<img width="585" alt="sonarqube-webhook" src="https://github.com/user-attachments/assets/6652826d-a7e1-4461-b159-18e3306070af" />

  
---

### 9. AWS ECR Setup
- Create 2 docker registries for frontend and backend Docker images on AWS Elastic Container Registry (ECR)
- Login as ECR

<img width="585" alt="aws-ecr-repositories" src="https://github.com/user-attachments/assets/a7440419-f68b-438d-a7e1-e3e76fed1031" />


---

### 10. Add Credentials on Jenkins
- Add credentials for the following on Jenkins:
1. AWS Credentials
2. GitHub Credentials
3. Sonar Token
4. ECR Repo Frontend
5. ECR Repo Backend
6. Account ID for AWS
 
---
  
### 11. Configure installed Jenkins Plugins
- Configure installed Jenkins Plugins
- Add SonarQube Server URL
- Done with Jenkins Configuration and Installation

---

### 12. AWS EKS Cluster Setup
- Create EKS Cluster 
- Configure Load Balancer on EKS
- Download IAM policy for Load Balancer
- Create IAM policy for the Load Balancer Controller
- Create OICD (OpenID Connect) Provider
- Create IAM Service Account for our Cluster
- Deploy AWS Load Balancer Controller using Helm.


<img width="585" alt="eks-cluster" src="https://github.com/user-attachments/assets/e5b0c68b-0a3a-48c5-9f96-d953bbb23946" />

---

### 13. Prometheus and Grafana Setup
- Deploy Prometheus and Grafana in the cluster.
- Expose services via a load balancer.
- Add Prometheus as a data source in Grafana.
- Import dashboards for cluster monitoring.

<img width="585" alt="prometheus-browser" src="https://github.com/user-attachments/assets/a9e9f2b9-b507-4c76-b4e7-0abe17c633f5" />

---

### 14. CI Pipeline on Jenkins
- Configure pipelines for frontend and backend builds.
- First, build backend
- Then, build frontend

<img width="585" alt="build-frontend-and-backend-jenkins" src="https://github.com/user-attachments/assets/21907df5-36e3-48e4-8eae-d746f0abf95b" />


---

### 15. ArgoCD Installation and Configuration
- Install ArgoCD
- Expose ArgoCD to a load balancer
- Connect Git Repository
- Configure ArgoCD to sync with a private Git repository

<img width="585" alt="argo-cd-browser-1" src="https://github.com/user-attachments/assets/720372d6-f310-4e4a-8b4e-ce7752592203" />


---

### 16. Application Deployment
- Deploy three apps (frontend, backend, database) using ArgoCD.
- Configure ingress for backend and frontend.

<img width="585" alt="argocd-threeapps-deployed" src="https://github.com/user-attachments/assets/0d1de918-c0dc-40ea-b852-80d3114f7fbf" />


---

### 17. CNAME/DNS Setup
- Configure domain and DNS using Cloudflare.

---

## Monitoring and Management
- Use Prometheus for metrics and alerts.
- Use Grafana for cluster health visualization and analysis.

<img width="1439" alt="postgresql-logs" src="https://github.com/user-attachments/assets/7d79d3e8-ed8f-42fa-9df5-b665b341bb2e" />
<img width="1439" alt="sonarqube-vulnerability-analysis-dashboard" src="https://github.com/user-attachments/assets/39972b36-60ee-4079-bc35-d1c17782c8b6" />
<img width="1440" alt="see-cluster-health-after" src="https://github.com/user-attachments/assets/cf0dceff-ac9a-4677-8015-9a0608be23e0" />



