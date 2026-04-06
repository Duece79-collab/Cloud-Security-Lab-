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
