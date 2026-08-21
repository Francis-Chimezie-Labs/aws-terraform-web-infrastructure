# Security and IAM

## Security Group

A dedicated web Security Group controls traffic reaching the EC2 instance.

HTTP traffic is allowed on port 80.

Administrative access was later moved toward AWS Systems Manager rather than relying on an EC2 SSH key pair.

## IAM Role

Terraform creates:

cloudnova-ec2-role

The trust policy allows the EC2 service to assume the role.

## Instance Profile

Terraform creates:

cloudnova-ec2-profile

The Instance Profile connects the IAM Role to the EC2 instance.

Architecture:

EC2
↓
Instance Profile
↓
IAM Role
↓
AWS permissions

## S3 Permissions

The EC2 IAM Role can:

- List the project S3 bucket
- Read objects
- Upload objects

Permissions are scoped to the project bucket.

## Systems Manager

AmazonSSMManagedInstanceCore is attached to the EC2 role.

This enables the EC2 instance to register with AWS Systems Manager and allows administrative sessions through Session Manager.

## Credential Strategy

No AWS Access Key ID or Secret Access Key is stored on the EC2 instance.

The instance receives temporary credentials through the IAM Role.