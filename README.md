
# 🚀 Cloud-Native App Deployment on AWS EKS with Docker & Kubernetes

A complete DevOps pipeline project focused on building, containerizing, and deploying a Python-based application using modern cloud-native tools and infrastructure. This project demonstrates end-to-end deployment using **Docker**, **AWS ECR**, **Kubernetes**, and **Amazon EKS**, with additional automation via **Python SDKs**.

---

## 💡 Project Objective

This project is designed to showcase a **DevOps-first approach** to deploying microservices in the cloud using container orchestration and AWS-native services. While the sample application is built in Python using Flask, the **primary focus is on the DevOps toolchain and deployment lifecycle**.

---

## 🧰 Tools & Technologies

| Category      | Tools/Services Used                                 |
|---------------|------------------------------------------------------|
| Containerization | Docker                                              |
| Container Registry | AWS Elastic Container Registry (ECR)               |
| Orchestration | Kubernetes, AWS Elastic Kubernetes Service (EKS)    |
| IaC/Automation | Python SDKs: `boto3` (for AWS), `kubernetes` (for K8s) |
| Monitoring App | Flask + psutil (for generating system metrics UI)  |
| CLI Tools | AWS CLI, kubectl                                        |

---

## 🛠️ What You'll Learn

- How to **containerize** an app with Docker
- Push container images to **Amazon ECR**
- Create and manage **Amazon EKS clusters** using AWS CLI
- Automate **Kubernetes deployments and services** using Python
- Use `kubectl` to manage and inspect running pods, services, and deployments
- Perform **port forwarding** and access services running inside a K8s cluster

---

## 🧱 Architecture Overview

```
[ Flask App ] --> [ Docker Image ] --> [ Amazon ECR ]
                                         |
                                         v
                              [ Amazon EKS Cluster ]
                                     |
                             [ Kubernetes Deployment ]
                                     |
                             [ Load-balanced Service ]
```

---

## 📦 Docker Image Creation

```bash
# Build the Docker image
docker build -t resource-monitor .

# Run it locally
docker run -p 5000:5000 resource-monitor
```

---

## ☁️ Push to AWS ECR

```python
# Python script to create ECR repo
import boto3

ecr = boto3.client('ecr')
repo = ecr.create_repository(repositoryName='resource-monitor')
print("ECR URI:", repo['repository']['repositoryUri'])
```

Then:

```bash
docker tag resource-monitor <ecr-uri>:latest
docker push <ecr-uri>:latest
```

---

## ☸️ Kubernetes Deployment on Amazon EKS

- A Kubernetes cluster is created on **Amazon EKS**
- Node groups are attached
- A deployment and service are created programmatically using Python's Kubernetes client

```python
# eks_deploy.py (sample snippet)
from kubernetes import client, config
config.load_kube_config()

# Deployment and Service objects defined here...
```

```bash
python eks_deploy.py
```

---

## 🧪 Verifying the Setup

```bash
kubectl get deployment
kubectl get pods
kubectl get service
kubectl port-forward service/<service-name> 5000:5000
```

---

## 📌 Requirements

- ✅ AWS Account & CLI configured
- ✅ Docker
- ✅ kubectl
- ✅ Python 3.x
- ✅ IAM permissions for ECR & EKS
- ✅ VPC and networking for EKS cluster

---

## 🎯 Why This Project Matters

This project is ideal for anyone looking to:

- Practice **cloud-native app deployment**
- Gain **hands-on experience with AWS EKS**
- Learn how to manage **Kubernetes clusters** and workloads
- Understand **Docker and container orchestration**
- Use **Python SDKs for DevOps automation**

It’s not about the app — it's about the deployment.

---

## 📜 License

Licensed under the [MIT License](LICENSE).
