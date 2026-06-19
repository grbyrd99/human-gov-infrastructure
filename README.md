
HumanGov Infrastructure

Terraform infrastructure-as-code for the HumanGov application — a simulated multi-tenant SaaS platform for U.S. state government agencies running on AWS.

Overview

This repository manages all AWS infrastructure for the HumanGov application using Terraform. Infrastructure is provisioned as code to ensure consistency, repeatability, and auditability across environments. Each migration phase introduces new infrastructure components in response to requirements from the simulated CIO.

Infrastructure Evolution

PhaseWhat Was BuiltStatus1EC2 instance, VPC, Security GroupsComplete2Docker containerization, ECR repositoryComplete3ECS Cluster, ALB, per-tenant DynamoDB and S3, multi-tenant isolationComplete4EKS cluster, Kubernetes workloadsIn Progress

Current Infrastructure (Phase 3)

Multi-Tenant Architecture

Each state tenant is provisioned with isolated AWS resources to ensure data separation and independent scalability:


Amazon ECS — containerized application per tenant
Amazon ECR — Docker image registry
Application Load Balancer — routes traffic to tenant-specific ECS services
Amazon DynamoDB — per-tenant data store
Amazon S3 — per-tenant object storage
VPC — isolated network with public/private subnets, security groups


Terraform Structure

terraform/
├── main.tf          # Core infrastructure resources
├── variables.tf     # Input variables
├── outputs.tf       # Output values
└── ...

Technologies


IaC: Terraform (HCL)
Cloud Provider: AWS
Services: ECS, ECR, ALB, DynamoDB, S3, VPC, IAM


Usage

bash# Initialize Terraform
terraform init

# Preview changes
terraform plan

# Apply infrastructure
terraform apply

# Destroy infrastructure
terraform destroy

Related Repository

Application code: grbyrd99/human-gov-application

About This Project

Part of a hands-on DevOps and cloud engineering bootcamp simulating enterprise infrastructure evolution. Each phase is driven by a new CIO requirement, mirroring real-world cloud engineering engagements where infrastructure must evolve incrementally without disrupting existing workloads.
