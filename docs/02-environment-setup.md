# Environment Setup

## Local Tools

The workstation was prepared with:

- Terraform
- Git
- AWS CLI
- Visual Studio Code
- AWS Session Manager Plugin

## AWS Authentication

An IAM user was configured for AWS CLI access.

AWS CLI credentials were configured locally and verified with:

aws sts get-caller-identity

The AWS region used for the project is:

us-east-2

## Terraform Project

Project directory:

C:\aws-terraform-web-infrastructure

Terraform initialization:

terraform init

Configuration validation:

terraform validate

Git was initialized to provide version control for the Terraform configuration.

Sensitive Terraform files are excluded using `.gitignore`.