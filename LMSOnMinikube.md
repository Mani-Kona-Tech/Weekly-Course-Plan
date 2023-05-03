# Setup LMS on Minikube

Login in to Azure Portal - New Version 
Create Azure VM
  - install Docker
    https://docs.docker.com/engine/install/ubuntu/
  - Post Install Steps
    https://docs.docker.com/engine/install/linux-postinstall/
    sudo usermod -aG docker $USER
    newgrp docker
  - install Kubectl
        sudo snap install kubectl --classic
  - install Minikube
        https://minikube.sigs.k8s.io/docs/start/  
        curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
        sudo dpkg -i minikube_latest_amd64.deb
  - minikube start 
    - minikube start
  - ingress addon
    - minikube addons enable ingress


  - clone the code from github
       git clone https://github.com/digitaledify/lms-public.git

    - Build FrontEnd Image with Docker
       cd webapp
       docker build -t lms-public-frontend .
    - Build BackEnd Image with Docker
         cd ../api
         docker build -t lms-public-backend .
Load Images to Minikube 
    - minikube image load lms-public-frontend
    - minikube image load lms-public-backend

Check images are loaded
    - minikube image list

    - use kubectl to deploy the application in AKS
       kubectl apply -f kubernetes

Test the cluster 
    - minikube service lms-public-frontend-service
    - minikube service lms-public-backend-service

    - minikube dashboard

    - minikube stop
    - minikube delete   

    
