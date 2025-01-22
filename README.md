# Sana Blog Application

This repository contains the source code and deployment scripts for the Sana Blog Application. The application can be deployed using Docker or Kubernetes.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/) (for Kubernetes deployment)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

## Deployment Instructions

### 1. Docker Deployment

To deploy the application using Docker, follow these steps:

1. Build the Docker image:
    ```sh
    docker build -t sana-blog-app .
    ```

2. Run the Docker container:
    ```sh
    docker run -p 5000:5000 sana-blog-app
    ```

The application should now be running locally at `http://localhost:5000`.

### 2. Kubernetes Deployment

To deploy the application using Kubernetes, follow these steps:

1. Start Minikube:
    ```sh
    minikube start
    ```

2. Verify the cluster information:
    ```sh
    kubectl cluster-info
    ```

3. Apply the Kubernetes deployment configuration:
    ```sh
    kubectl apply -f kubernetes/deployment.yaml
    ```

4. Apply the Kubernetes service configuration:
    ```sh
    kubectl apply -f kubernetes/service.yaml
    ```

5. Build the Docker image:
    ```sh
    docker build -t blog-app:latest .
    ```

6. Load the Docker image into Minikube:
    ```sh
    minikube image load blog-app:latest
    ```

7. Verify the deployment:
    ```sh
    kubectl get deployments
    kubectl get pods
    kubectl get svc
    ```

8. Access the service:
    ```sh
    minikube service blog-app-service
    ```

The application should now be accessible via the URL provided by the `minikube service` command.

## Directory Structure
