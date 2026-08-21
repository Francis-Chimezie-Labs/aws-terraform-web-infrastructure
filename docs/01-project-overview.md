# Project Overview

## Project Name

CloudNova AWS Web Infrastructure

## Objective

Design and deploy a production-style AWS web infrastructure using Terraform Infrastructure as Code.

## Business Requirements

The environment required:

- Dedicated AWS networking
- Public and private network separation
- A web server
- Controlled network access
- IAM Role-based permissions
- Private object storage
- Secure administrative access
- Infrastructure monitoring
- Email notification capability
- Repeatable deployment through Terraform

## AWS Services

The architecture uses:

- Amazon VPC
- Amazon EC2
- AWS IAM
- Amazon S3
- AWS Systems Manager
- Amazon CloudWatch
- Amazon SNS

## Infrastructure as Code

Terraform manages the AWS resources, enabling infrastructure configuration to be reviewed, reproduced, modified, and destroyed through code.