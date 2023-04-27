# Introduction to Azure Kubernetes Service (AKS)

**Lesson Duration**: 1 week (5 sessions)

**Lesson Objectives**:
1. Understand the fundamentals of Kubernetes and container orchestration.
2. Learn about Azure Kubernetes Service (AKS) and its features.
3. Set up and deploy a basic AKS cluster.
4. Manage and scale an AKS cluster.
5. Implement best practices for monitoring and securing AKS clusters.

## Lesson Plan

### Session 1: Introduction to Kubernetes and Container Orchestration

1. **Introduction** 
   - Brief overview of cloud computing and containerization
   - Importance of container orchestration

2. **Kubernetes Fundamentals** 
   - Basic architecture and components (Nodes, Pods, Services, etc.)
   - Key concepts (Deployments, ReplicaSets, ConfigMaps, etc.)

3. **Kubernetes Orchestration** 
   - Scheduling and load balancing
   - Rolling updates and rollbacks
   - Self-healing

### Session 2: Azure Kubernetes Service 

1. **Introduction to AKS** 
   - Overview and benefits of AKS

2. **AKS Features** 
   - Managed Kubernetes control plane
   - Simplified cluster upgrades
   - Azure Active Directory integration
   - Advanced networking and monitoring

3. **AKS Pricing** 
   - Pay-as-you-go model
   - Understanding AKS costs and optimizing resources

### Session 3: Setting Up and Deploying an AKS Cluster

1. **Prerequisites and Tools** 
   - Azure subscription, Azure CLI, and kubectl

2. **Creating an AKS Cluster** 
   - Step-by-step demonstration and hands-on practice
   - Configuring the cluster and nodes

3. **Deploying Applications to AKS** (20 minutes)
   - Creating and managing deployments
   - Exposing applications using services

### Session 4: Managing and Scaling an AKS Cluster

1. **Cluster Management** )
   - Upgrading and scaling the cluster
   - Monitoring cluster health

2. **Application Scaling** 
   - Scaling deployments using ReplicaSets
   - Implementing Horizontal Pod Autoscaling

3. **Persistent Storage** 
   - Understanding Persistent Volumes and Persistent Volume Claims
   - Configuring storage classes in AKS

### Session 5: Monitoring and Securing AKS Clusters

1. **Monitoring AKS Clusters** 
   - Azure Monitor for containers
   - Log analytics and metrics

2. **Securing AKS Clusters** 
   - Network security and isolation
   - Role-based access control (RBAC) with Azure AD
   - Pod security policies
   - Review key concepts and best practices
   - Address any questions and concerns


### How to Setup  AKS  Cluster for LMS application 

   - Create ACR
   - Create AKS
   - Create a VM
   - Install Docker 
   - Post Install Steps
   - Install Kubectl
      sudo snap install kubectl --classic
   - Setup Code form GITHUB or Azure Repos
      git clone https://github.com/digitaledify/lms-public.git
      cd lms-public
      git checkout features/lms-aks-ingress-tls
   - Build FrontEnd Image with Docker
      cd webapp
      docker build -t lms-public-frontend .
   - Build BackEnd Image with Docker
      cd ../api
      docker build -t lms-public-backend .
   - install Azure Cli
      sudo apt install azure-cli
   - Login to Azure Cli - Azure Login
      az login
   - connect to AKS Cluster
      Get details from AKS Cluster 
      click on connect button
      copy the command and run in the terminal
   - Connect to ACR and Push Images
      az acr login --name lmsacrreg
      Tag Docker images
      docker tag lms-public-frontend lmsacrreg.azurecr.io/lms-public-frontend
      docker tag lms-public-backend lmsacrreg.azurecr.io/lms-public-backend
      Push Docker images to ACR
      docker push lmsacrreg.azurecr.io/lms-public-frontend
      docker push lmsacrreg.azurecr.io/lms-public-backend

   - use kubectl to deploy the application in AKS
      kubectl apply -f kubernetes/
   - Get the Public IP of the Load Balancer
      kubectl get svc
   - Access the application using the Public IP
