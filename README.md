# Time Web App

This Python application shows the current time in Toronto. I containerized the application using Docker and deployed it to a Kubernetes (K8S) cluster.

## Prerequisites

- Docker
- Kuberneter (Minikube, kubectl)

## Building & Running the Docker Container

Created the Docker file in the root project directory

1. **Build Docker image:**

   ```sh
   docker build -t clo835_prj2 .
2. **Run Docker container:**

    ```sh
    docker run -p 3030:3030 clo835_prj2
You can visit the application at http://localhost:3030.

## Deploying to Kubernetes Cluster

1. **Start Minikube:**

    ```sh
    minikube start
If you don't have minikube install it from this link: https://minikube.sigs.k8s.io/docs/start/

2. **Install kubectl:**

If you don't have kubectl install it from this link depending on your operating system: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

2. **Apply Deployment and Service manifests:**

    ```sh
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
3. **Verify deployment:**

    Run the below commands to check if the deployment & service are created successfully:

    ```sh
    kubectl get deployments
    kubectl get pods
    kubectl get services
We exposed the service using NodePort, we can access applications using any Kubernetes cluster nodes' IP addresses on the specified nodePort. 
We are using Minikube on the local cluster So you can run the below command to get the IP: 
  
    minikube ip
    
The application should now be accessible at http://{minikube-ip}:30000.

## Challenges and Troubleshooting
    
I faced a syntax error "metadata:name should be in lowercase because I used capitalize for the metadata:name" during the applying phase. 


