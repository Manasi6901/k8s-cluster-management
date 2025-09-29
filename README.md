🚀 Kubernetes Cluster Management Project
🎯 Objective

This project demonstrates end-to-end Kubernetes cluster management using a simple Nginx application. It covers:

Cluster setup with Minikube

Namespace management

ConfigMaps & Secrets

Deployments with liveness & readiness probes

Services & Ingress for external access

Horizontal Pod Autoscaler (HPA)

Monitoring & debugging

🛠 Prerequisites

Before running this project, install:

Docker

Minikube

kubectl

Metrics Server
 (for HPA)

Nginx Ingress Controller

📂 Project Structure
k8s-cluster-management/
│── README.md
│── manifests/
│   ├── namespace.yaml
│   ├── configmap.yaml
│   ├── secret.yaml
│   ├── nginx-deployment.yaml
│   ├── nginx-service.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml

⚡ Steps to Run
1. Start Minikube
minikube start --driver=docker
kubectl get nodes

2. Create Namespace
kubectl apply -f manifests/namespace.yaml
kubectl get ns

3. Apply ConfigMap & Secret
kubectl apply -f manifests/configmap.yaml
kubectl apply -f manifests/secret.yaml
kubectl get configmap -n demo-namespace
kubectl get secret -n demo-namespace

4. Deploy Nginx & Service
kubectl apply -f manifests/nginx-deployment.yaml
kubectl apply -f manifests/nginx-service.yaml
kubectl get pods -n demo-namespace
kubectl get svc -n demo-namespace

5. Scale Manually
kubectl scale deployment nginx-deployment --replicas=4 -n demo-namespace
kubectl get pods -n demo-namespace

6. Enable Autoscaling (HPA)
kubectl apply -f manifests/hpa.yaml
kubectl get hpa -n demo-namespace

7. Enable Ingress

Enable addon:

minikube addons enable ingress


Apply ingress:

kubectl apply -f manifests/ingress.yaml
kubectl get ingress -n demo-namespace


Update /etc/hosts (Linux/Mac) or C:\Windows\System32\drivers\etc\hosts (Windows):

127.0.0.1   nginx.local


Access app at: 👉 http://nginx.local

📸 Expected Outputs

kubectl get pods,svc,hpa -n demo-namespace shows running pods, services, autoscaler.

kubectl get ingress -n demo-namespace shows ingress resource.

Browser shows Nginx welcome page.
