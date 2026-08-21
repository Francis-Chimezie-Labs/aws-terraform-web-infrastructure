# AWS Systems Manager

## Purpose

AWS Systems Manager Session Manager provides administrative access to EC2 without requiring an EC2 SSH private key.

## IAM Configuration

The EC2 role was granted:

AmazonSSMManagedInstanceCore

## EC2 Registration

Systems Manager reported the instance as:

PingStatus: Online
Platform: Ubuntu
PlatformVersion: 24.04

## Local Session Manager Plugin

The Session Manager Plugin was installed on the Windows workstation.

## Connection

The EC2 session was started using:

aws ssm start-session --target <instance-id>

The session connected successfully as:

ssm-user

The hostname confirmed the session was connected to the CloudNova EC2 instance.

## IAM Role Verification

AWS CLI was installed inside EC2.

Running:

aws sts get-caller-identity

returned an assumed-role identity for:

cloudnova-ec2-role

This proved the EC2 instance was using temporary IAM Role credentials instead of stored access keys.