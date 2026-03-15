
# Terraform EKS Cluster Deployment

## 📌 Project Overview

This project provisions an **Amazon EKS (Elastic Kubernetes Service) Cluster** using **Terraform**.
It automatically creates the required AWS infrastructure including **VPC, subnets, NAT gateway, and EKS cluster**, and then deploys a sample **NGINX application** on the Kubernetes cluster.

This project demonstrates **Infrastructure as Code (IaC)** using Terraform and Kubernetes deployment using kubectl.

---

## 🛠 Technologies Used

* Terraform
* AWS EKS
* AWS VPC
* Kubernetes
* kubectl
* Git & GitHub
* Ubuntu Linux

---

## 📁 Project Structure

```
EKS-using-terraform/
│
├── vpc.tf
├── eks-cluster.tf
├── variables.tf
├── outputs.tf
├── providers.tf
├── terraform.tfvars
└── README.md
```

---

## ⚙️ Prerequisites

Before running this project ensure the following tools are installed:

* AWS CLI
* Terraform
* kubectl
* Git

Configure AWS credentials:

```
aws configure
```

---

## 🚀 Steps to Deploy EKS Cluster

### 1️⃣ Clone Repository

```
git clone https://github.com/NishaMdevops/EKS-using-terraform.git
cd EKS-using-terraform
```

---

### 2️⃣ Initialize Terraform

```
terraform init
```

---

### 3️⃣ Validate Configuration

```
terraform validate
```

---

### 4️⃣ Check Terraform Plan

```
terraform plan
```

---

### 5️⃣ Create Infrastructure

```
terraform apply
```

Type:

```
yes
```

Terraform will create:

* VPC
* Public & Private Subnets
* NAT Gateway
* Internet Gateway
* Security Groups
* EKS Cluster

---

## 🔗 Configure kubectl for EKS

After cluster creation run:

```
aws eks update-kubeconfig --name <cluster-name> --region ap-south-1
```

Verify connection:

```
kubectl get nodes
```

---

## 📦 Deploy Sample Application

Create deployment file:

```
nano nginx-deployment.yaml
```

Example Deployment:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```

Apply deployment:

```
kubectl apply -f nginx-deployment.yaml
```

Check pods:

```
kubectl get pods
```

---

## 🌐 Expose Application

Create service:

```
kubectl expose deployment nginx-deployment --type=LoadBalancer --port=80
```

Check service:

```
kubectl get svc
```

You will receive an **AWS LoadBalancer DNS**.

Open it in browser to access the NGINX application.

---

## 🧹 Destroy Infrastructure

To remove all resources:

```
terraform destroy
```

---

## 📈 Skills Demonstrated

* Infrastructure as Code using Terraform
* AWS VPC Networking
* Kubernetes Cluster Deployment
* Containerized Application Deployment
* Git Version Control


