# Multi-Service API App on Amazon EKS

This repository contains a multi-service API app with **auth**, **users**, and **tasks** services deployed on **Amazon EKS** using **Kubernetes**. Each service is defined in its own configuration file (`auth.yaml`, `tasks.yaml`, `users.yaml`).

## Architecture

- **Auth Service**: Handles user authentication and JWT management.
- **Users Service**: Provides CRUD operations for user profiles.
- **Tasks Service**: Manages tasks for authenticated users.

These services communicate internally via Kubernetes, with data persisted using **Amazon EBS**.

## Setup

### Prerequisites

- **Amazon EKS** for cluster management.
- **Kubernetes** for container orchestration.
- **Amazon EBS** for persistent storage.

### Deployment Steps

1. **Create an EKS Cluster** using AWS CLI:
    ```bash
    aws eks create-cluster --name my-cluster --role-arn <role-arn> --resources-vpc-config subnetIds=<subnet-ids>,securityGroupIds=<security-group-ids>
    ```

2. **Apply config files**:
    ```bash
    kubectl apply -f k8s/auth.yaml
    kubectl apply -f k8s/users.yaml
    kubectl apply -f k8s/tasks.yaml
    ```

## Technologies Used

- Amazon EKS (Kubernetes Cluster)
- Amazon EBS (Persistent Storage)
- Docker (Containerization)
- Node.js / Express (Backend Framework)
- PostgreSQL / MySQL (Database)

## Directory Structure

```bash
├── auth/                # Auth service
├── users/               # Users service
├── tasks/               # Tasks service
├── k8s/                 # Kubernetes YAML configs
├── README.md            # Documentation
└── Dockerfile           # Docker setup
