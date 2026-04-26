# 🔄 Argo Workflows & Events CI/CD

Event-driven CI/CD pipeline using Argo Workflows and Argo Events. Triggers automated build, test, and deploy workflows from GitHub webhooks.

## Flow

```
GitHub Push → Argo Events (EventSource) → Sensor → Trigger → Argo Workflow
                                                              ├── Build Docker Image
                                                              ├── Push to ECR
                                                              └── Deploy to K8s
```

## Setup

```bash
# Install Argo Workflows
kubectl create namespace argo
kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/latest/download/install.yaml

# Install Argo Events
kubectl create namespace argo-events
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-events/stable/manifests/install.yaml

# Apply our configs
kubectl apply -f events/
kubectl apply -f workflows/
```

## Tech Stack
`Argo Workflows` `Argo Events` `Kubernetes` `Docker` `AWS ECR`
