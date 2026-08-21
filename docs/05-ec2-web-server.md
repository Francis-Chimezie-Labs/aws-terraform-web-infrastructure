# EC2 Web Server

## AMI Selection

Terraform uses an AWS AMI data source to dynamically locate a recent Ubuntu 24.04 image.

This avoids relying on a manually hard-coded AMI identifier.

## Instance

Instance type:

t3.micro

The instance is deployed in the CloudNova public subnet.

## User Data

Terraform provides an EC2 startup script that:

- Updates Ubuntu packages
- Installs Nginx
- Enables Nginx
- Starts Nginx
- Creates the CloudNova web page

## Verification

The public IP address was obtained through Terraform outputs.

Opening the address in a browser displayed:

CloudNova Web Server

This confirmed that the networking, Security Group, EC2 instance, user data, and Nginx configuration were functioning together.