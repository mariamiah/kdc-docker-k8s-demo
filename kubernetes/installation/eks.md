## ✅ EKS Setup Instructions

This guide walks through deploying the same demo to an AWS-managed Kubernetes cluster using **EKS**.

---

## 🔧 Prerequisites

- AWS CLI configured with credentials
- `eksctl` installed
- `kubectl` installed
- IAM permissions for EKS

---

## 🚀 1. Create EKS Cluster

```bash
eksctl create cluster \
  --name demo-cluster \
  --region us-west-2 \
  --nodes 2
```

## 🚀 2. Build and Push Docker Images
Push your Docker images to Amazon ECR:
```bash
aws ecr create-repository --repository-name backend
docker tag backend:latest <aws_account_id>.dkr.ecr.<region>.amazonaws.com/backend
docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/backend
```

## 🚀 3. Configure kubectl
```bash
aws eks update-kubeconfig --name demo-cluster
kubectl get nodes
```

## 🚀 4. Apply Your Resources
```bash
kubectl apply -f k8s-resources/
```
