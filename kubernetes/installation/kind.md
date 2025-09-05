# Kind Cluster Setup - kind Setup Instructions (Docker Desktop)
This guide shows you how to use **Kind** on **Docker Desktop** to run your Kubernetes workloads locally.

---

## 🧱 Prerequisites
- Docker Desktop ✅
- `kind` CLI installed ✅
- `kubectl` installed ✅

---

## 🏗️ 1. Create a Cluster
```bash
kind create cluster --name demo-cluster
```

## 🏗️ 2. Install NGINX Ingress Controller
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.1/deploy/static/provider/kind/deploy.yaml
```
```bash
kubectl wait --namespace ingress-nginx \
  --for=condition=Ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s
```

## 🏗️ 3. Apply Your Kubernetes Resources
```bash
kubectl apply -f k8s-resources/
```

## 🏗️ 4. Accessing the App in Kind
Use port-forwarding (since Kind doesn't expose services outside Docker):
```bash
kubectl port-forward svc/frontend-service 8080:80 -n demo-app
kubectl port-forward svc/backend-service 8081:80 -n demo-app
```
