# StartTech Infrastructure as Code
A comprehensive Terraform-based infrastructure deployment for a scalable web application on AWS.

## Overview
This repository contains Infrastructure as Code (IaC) for deploying a complete web application stack on AWS with auto-scaling, high availability, and comprehensive monitoring.

## Architecture
- **Frontend**: S3 + CloudFront for global static content delivery
- **Backend**: Auto Scaling Group of EC2 instances behind Application Load Balancer
- **Caching**: ElastiCache Redis cluster
- **Monitoring**: CloudWatch for logs, metrics, and alarms
- **Security**: IAM roles and security groups with least-privilege principles

## Prerequisites
- AWS Account with appropriate permissions
- Terraform v1.10.0 or higher
- AWS CLI v2.0 or higher
- GitHub Actions (for CI/CD pipeline)

## Directory Structure
```mermaid
starttech-infra/
├── .github/              # GitHub Actions workflows
├── monitoring/           # Monitoring configurations
├── scripts/              # Deployment and utility scripts
├── terraform/            # Terraform configurations
│   ├── modules/          # Reusable Terraform modules
│   ├── main.tf           # Root module configuration
│   ├── variables.tf      # Input variables
│   └── outputs.tf        # Output values
├── .gitignore            # Github ignore configuration
├── README.md             # Repository guide
└── documentation/        # Project documentation
```

---

## Quick Start
1. Clone Repository
```bash
git clone https://github.com/PeterOyelegbin/starttech-infra.git
cd starttech-infra
```

2. Configure AWS Credentials
```bash
aws configure

# Or set environment variables:
export AWS_ACCESS_KEY_ID="your-access-key"
export AWS_SECRET_ACCESS_KEY="your-secret-key"
export AWS_REGION="us-east-1"
```

3. Initialize Terraform
```bash
cd terraform
terraform init
```

4. Configure Variables
```bash
cp terraform.tfvars.example terraform.tfvars
```
**Note:** Update terraform.tfvars with your values

5. Deploy Infrastructure
```bash
# Plan deployment
terraform plan

# Apply deployment
terraform apply -auto-approve

# For manual deployment
./scripts/deploy-infrastructure.sh
```

---

## Clean Up
```bash
# Destroy deployment
terraform destroy -auto-approve

# For manual cleanup
./scripts/destroy-infrastructure.sh
```

---

## GitHub Actions CI/CD
Infrastructure changes are automatically deployed via GitHub Actions:
- Push to main branch triggers deployment
- Pull requests to destroy branch triggers terraform-destroy

## Important Files
- terraform/main.tf - Main infrastructure definition
- terraform/terraform.tfvars.example - Configuration template
- scripts/deploy-infrastructure.sh - Manual deployment script
- scripts/destroy-infrastructure.sh - Manual destroy script
- .github/workflows/infrastructure-deploy.yml - CI/CD pipeline

## Security Notes
- Never commit terraform.tfvars to version control
- Rotate IAM credentials regularly
- Review security group rules before production deployment
- Enable MFA for AWS root account

## Support
For issues and questions:
- Check existing documentation
- Review Terraform state for current configuration
- Contact infrastructure team
