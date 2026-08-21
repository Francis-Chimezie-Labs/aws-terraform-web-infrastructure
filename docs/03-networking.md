# AWS Networking

## VPC

Terraform provisions a dedicated VPC using:

10.0.0.0/16

DNS support and DNS hostnames are enabled.

## Public Subnet

CIDR:

10.0.1.0/24

The public subnet assigns public IP addresses to appropriate resources.

The EC2 web server is deployed in this subnet.

## Private Subnet

CIDR:

10.0.2.0/24

The private subnet provides network separation for resources that should not require direct public exposure.

## Internet Gateway

An Internet Gateway is attached to the CloudNova VPC.

## Route Tables

The public route table contains a default route:

0.0.0.0/0 → Internet Gateway

The public subnet is associated with the public route table.

A separate private route table is associated with the private subnet.

## Design Decision

Separating public and private subnets provides a foundation for multi-tier infrastructure where internet-facing resources and internal resources can be isolated.