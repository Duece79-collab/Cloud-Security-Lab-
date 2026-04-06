# Cloud-Security-Lab-

# 🔐 Secure Cloud Web App on AWS

## 🚀 Overview
This project demonstrates a secure, production-style cloud architecture using AWS.

It includes:
- VPC with public/private subnets
- EC2 backend (or containerized app)
- RDS database
- S3 + CloudFront frontend
- IAM least privilege access
- AWS WAF protection
- Monitoring with CloudWatch
- CI/CD using GitHub Actions

---

## 🏗️ Architecture

Frontend (S3 + CloudFront)  
→ Application Load Balancer  
→ Backend (EC2 / Docker)  
→ RDS (Private Subnet)

---

## 🔐 Security Features

- Private subnets for backend + DB
- No public DB access
- IAM roles (no hardcoded creds)
- AWS WAF (SQLi, XSS protection)
- HTTPS via ACM
- Secrets Manager for credentials
- CloudWatch monitoring + alerts

---

## ⚙️ Tech Stack

- AWS
- Terraform
- Docker
- GitHub Actions
- CloudWatch

---

## 📅 10-Day Build Plan

### Day 1
- Setup repo
- Define architecture

### Day 2
- Create VPC, subnets, routing

### Day 3
- IAM roles + security groups

### Day 4
- Backend app + Docker

### Day 5
- Deploy backend (EC2/ECS) + ALB

### Day 6
- RDS + Secrets Manager

### Day 7
- Frontend (S3 + CloudFront)

### Day 8
- Monitoring (CloudWatch)

### Day 9
- WAF + GuardDuty + Security Hub

### Day 10
- CI/CD + polish + screenshots

---

## 🧪 How to Run

```bash
cd terraform
terraform init
terraform apply
#I will include screenshots every step of the way as I continue to build

folder strudture
cloud-secure-app/
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│
├── app/
│   └── app.py
│
├── frontend/
│   └── index.html
│
├── .github/workflows/
│   └── deploy.yml
│
└── README.md


FUTURE IMPROVEMENTS:
💡 Future Improvements
Auto-scaling
Zero-trust (SSM instead of SSH)
Kubernetes (EKS)



---

# 🧠 Starter Backend (app/app.py)

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Secure Cloud App Running 🚀"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
==============================
<!DOCTYPE html>
<html>
<head>
  <title>Cloud App</title>
</head>
<body>
  <h1>Secure Cloud App 🚀</h1>
  <p>If you see this, frontend is working.</p>
</body>
</html>
============================================

provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

🔁 GitHub Actions (CI/CD)
.github/workflows/deploy.yml

name: Deploy

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - name: Terraform Init
      run: terraform init
      working-directory: terraform

    - name: Terraform Apply
      run: terraform apply -auto-approve
      working-directory: terraform
