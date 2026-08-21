# Final Architecture

The CloudNova environment combines networking, compute, identity, storage, management, and monitoring.

## Request Flow

Internet
↓
Internet Gateway
↓
Public Route Table
↓
Public Subnet
↓
Security Group
↓
EC2 Web Server
↓
Nginx

## Administrative Access

Engineer Workstation
↓
AWS CLI
↓
AWS Systems Manager
↓
EC2
↓
ssm-user

## AWS Authorization

EC2
↓
Instance Profile
↓
cloudnova-ec2-role
↓
Temporary AWS credentials

## Storage Flow

EC2
↓
IAM Role
↓
S3 permissions
↓
Private S3 Bucket

## Monitoring Flow

EC2
↓
CloudWatch CPUUtilization
↓
CloudWatch Alarm
↓
SNS
↓
Email Notification

## Infrastructure Management

Terraform Configuration
↓
terraform plan
↓
Review
↓
terraform apply
↓
AWS Infrastructure
↓
Terraform State

## Version Control

Terraform Code
↓
Git
↓
GitHub
↓
Project Documentation