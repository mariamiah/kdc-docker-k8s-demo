# 🚀 Minikube Setup Guide (Docker Desktop)

This guide helps you set up a local Kubernetes cluster using Minikube with Docker as the driver.

---

## 🧱 Prerequisites
- Docker Desktop ✅
- kubectl installed ✅
- Minikube installed ✅

---

## ⚙️ Step-by-Step Installation

### ✅ 1. Start Minikube with Docker
```bash
minikube start --driver=docker
```

### ✅ 2. Verify Cluster
```bash
kubectl get nodes
```

### ✅ 3. Enable Ingress Controller
```bash
minikube addons enable ingress
```

### ✅ 4. Enable Ingress Controller
```bash
kubectl apply -f k8s-resources/
```

### ✅ 5. Access your app
```bash
minikube tunnel
```

### ✅ 6. Minikube Dashboard
```bash
minikube dashboard
```



