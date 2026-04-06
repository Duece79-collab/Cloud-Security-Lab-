# Secure Cloud Web App on AWS

A hands-on cloud engineering project built to demonstrate production-style AWS architecture, security controls, infrastructure as code, and CI/CD.

## What this project shows

- VPC design with public and private subnets
- Internet Gateway and NAT Gateway routing
- Application Load Balancer in public subnets
- Private EC2 application server
- Private RDS PostgreSQL database
- Security groups with least-access network paths
- IAM role for EC2 with AWS Systems Manager access
- CloudWatch logs and alarms
- Terraform for reproducible infrastructure
- GitHub Actions for deployment workflow

## Architecture

User request flows through an Application Load Balancer in public subnets.  
Traffic is forwarded to a backend application running on EC2 in private subnets.  
The application connects to PostgreSQL in private DB subnets.  
The database is not publicly reachable.

## Security decisions

- Database placed in private subnets only
- No direct inbound internet access to app server
- Security groups restricted by source security group, not broad CIDR where possible
- IAM role used instead of hardcoded AWS credentials
- Systems Manager can replace SSH for administrative access
- Encrypted RDS storage
- CloudWatch monitoring for visibility

## Folder structure

```text
cloud-secure-app/
├── terraform/
├── app/
├── frontend/
├── .github/workflows/



#How to deploy
cd terraform
terraform init
terraform plan
terraform apply


└── README.md
After apply, Terraform will output the ALB DNS name.
============================================================

Build plan
7-day version

Day 1: Repo setup, architecture diagram, Terraform init
Day 2: VPC, subnets, route tables, IGW, NAT
Day 3: Security groups, IAM role, EC2 bootstrap
Day 4: ALB, target group, listener, health check
Day 5: RDS PostgreSQL, DB subnet group, app connectivity
Day 6: CloudWatch logs and alarms, GitHub Actions
Day 7: Polish README, screenshots, resume bullets, LinkedIn post

10-day version

Day 1: Scope, repo, diagram, naming standard
Day 2: VPC and subnet design
Day 3: Routing and NAT
Day 4: Security groups and IAM role
Day 5: Flask app and Dockerfile
Day 6: EC2 deployment and app validation
Day 7: ALB and health checks
Day 8: RDS and database security
Day 9: Monitoring, WAF, Secrets Manager planning
Day 10: CI/CD, screenshots, final documentation, resume updates

Resume-ready value

This project demonstrates cloud networking, compute, storage, monitoring, IAM, and security fundamentals in a single deployable environment.

Next improvements
Add HTTPS listener with ACM certificate
Add Route 53 custom domain
Store DB password in Secrets Manager
Replace direct EC2 bootstrapping with Launch Template and Auto Scaling Group
Add AWS WAF to protect the ALB
Add S3 + CloudFront frontend

============================
script
#!/usr/bin/env bash
set -euo pipefail

PROJECT="cloud-secure-app"

mkdir -p "$PROJECT"/terraform
mkdir -p "$PROJECT"/app
mkdir -p "$PROJECT"/frontend
mkdir -p "$PROJECT"/.github/workflows

cat > "$PROJECT/README.md" <<'EOF'
# Secure Cloud Web App on AWS

A hands-on cloud engineering project built to demonstrate production-style AWS architecture, security controls, infrastructure as code, and CI/CD.

## What this project shows

- VPC design with public and private subnets
- Internet Gateway and NAT Gateway routing
- Application Load Balancer in public subnets
- Private EC2 application server
- Private RDS PostgreSQL database
- Security groups with least-access network paths
- IAM role for EC2 with AWS Systems Manager access
- CloudWatch logs and alarms
- Terraform for reproducible infrastructure
- GitHub Actions for deployment workflow

## Architecture

User request flows through an Application Load Balancer in public subnets.  
Traffic is forwarded to a backend application running on EC2 in private subnets.  
The application connects to PostgreSQL in private DB subnets.  
The database is not publicly reachable.

## Security decisions

- Database placed in private subnets only
- No direct inbound internet access to app server
- Security groups restricted by source security group, not broad CIDR where possible
- IAM role used instead of hardcoded AWS credentials
- Systems Manager can replace SSH for administrative access
- Encrypted RDS storage
- CloudWatch monitoring for visibility

## Folder structure

```text
cloud-secure-app/
├── terraform/
├── app/
├── frontend/
├── .github/workflows/
└── README.md

Add ECS Fargate instead of EC2
