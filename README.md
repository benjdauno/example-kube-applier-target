# Example Kube-Applier Target Repository

This repository serves as an example target for kube-applier, demonstrating how to organize Kubernetes manifests across different application tiers using commonly used technologies in Kubernetes demonstrations.

## Repository Structure

```
├── frontend/
│   ├── nginx-deployment.yaml
│   ├── nginx-service.yaml
│   └── nginx-configmap.yaml
├── backend/
│   ├── flask-deployment.yaml
│   ├── flask-service.yaml
│   └── flask-configmap.yaml
├── monitoring/
│   ├── nodejs-deployment.yaml
│   ├── nodejs-service.yaml
│   └── nodejs-configmap.yaml
└── README.md
```

## Application Tiers

### Frontend (`/frontend`) - Nginx
- **Purpose**: Web frontend service
- **Technology**: Nginx web server
- **Replicas**: 2
- **Resources**: 64Mi-128Mi memory, 250m-500m CPU
- **Features**: Static content serving with health check endpoint

### Backend (`/backend`) - Python Flask
- **Purpose**: API backend service
- **Technology**: Python Flask web framework
- **Replicas**: 3
- **Resources**: 128Mi-256Mi memory, 500m-1000m CPU
- **Features**: REST API endpoints (`/api`, `/health`), JSON responses

### Monitoring (`/monitoring`) - Node.js
- **Purpose**: Monitoring and metrics service
- **Technology**: Node.js with Express
- **Replicas**: 1
- **Resources**: 64Mi-128Mi memory, 100m-200m CPU
- **Features**: Prometheus metrics (`/metrics`), health checks, service statistics

## Kube-Applier Configuration

Each folder can be configured as a separate kube-applier target:

```yaml
# Example kube-applier configuration
targets:
  - name: frontend
    path: ./frontend
    namespace: frontend
  - name: backend
    path: ./backend
    namespace: backend
  - name: monitoring
    path: ./monitoring
    namespace: monitoring
```

## Resources Included

Each tier contains:
- **Deployment**: Application-specific container with tier-appropriate configuration
- **Service**: ClusterIP service for internal communication
- **ConfigMap**: Application code and configuration files

## Technologies Demonstrated

- **Nginx**: Industry-standard web server for static content
- **Python Flask**: Lightweight web framework for REST APIs
- **Node.js + Express**: JavaScript runtime for monitoring and metrics services

These technologies are commonly used in Kubernetes demonstrations and represent real-world application patterns.

## Usage

This repository is designed to be used as a target for kube-applier, which will automatically apply these manifests to your Kubernetes cluster based on your kube-applier configuration.
