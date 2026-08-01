# Microservices Kubernetes Deployment Assessment

This repository contains the complete Kubernetes configuration manifests and documentation for deploying a multi-container Node.js microservices architecture using Minikube.

## Application Architecture & Components
* **User Service**: Port `3000` (Manages user profiles and authentication routes)
* **Product Service**: Port `3001` (Manages product catalog and inventory routes)
* **Order Service**: Port `3002` (Manages customer orders and checkout routes)
* **Gateway Service**: Port `3003` (Acts as the API gateway proxy routing traffic to backend microservices)

---

## Folder Structure
```text
submission/
├── deployments/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── services/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── ingress/
│   └── ingress.yaml
├── screenshots/
│   ├── pods.png
│   ├── logs.png
│   └── service-test.png
└── README.md

## Setup & Deployment

1. **Start Minikube**:
   ```bash
   minikube start --driver=docker

Load Docker Images:

minikube image load user-service:latest
minikube image load product-service:latest
minikube image load order-service:latest
minikube image load gateway-service:latest

Deploy Manifests:

kubectl apply -f deployments/
kubectl apply -f services/
kubectl apply -f ingress/

Testing
Check Pods:
kubectl get pods

Test via Port Forwarding:
kubectl port-forward svc/gateway-service 3003:3003

curl http://localhost:3003/health