# Tekton CI/CD for Ruby on Rails App 

This repo sets up a simple Tekton pipeline to:
- Clone a Rails app from GitHub
- Build a Docker image
- Push it to Docker Hub

##  Prerequisites

- Kubernetes (Minikube, K3s, etc.)
- Tekton Pipelines + Dashboard
- Docker Hub account
- Rails app on GitHub (public)

##  Setup Instructions

1. **Install Tekton Pipelines & Dashboard**

```bash
kubectl apply -f https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
kubectl apply -f https://storage.googleapis.com/tekton-releases/dashboard/latest/release.yaml
kubectl port-forward svc/tekton-dashboard -n tekton-pipelines 9097:9097




#Create Docker Hub Secret

kubectl create secret docker-registry dockerhub-secret \
  --docker-username=<your-username> \
  --docker-password=<your-password> \
  --docker-email=<your-email>


#Apply the Tekton Pipeline

kubectl apply -f tekton-pipeline.yaml
