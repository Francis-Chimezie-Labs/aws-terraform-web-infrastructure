# Troubleshooting

Real infrastructure deployment rarely succeeds without investigation and refinement.

This project documents several issues encountered during implementation.

---

## 1. EC2 DescribeRegions Authorization Error

### Problem

AWS CLI returned:

UnauthorizedOperation

for:

ec2:DescribeRegions

### Root Cause

The IAM user authenticated successfully but did not have permission to perform the EC2 API operation.

### Resolution

IAM permissions were updated.

### Verification

The following command successfully returned:

us-east-2

This demonstrated the difference between authentication and authorization.

---

## 2. Incorrect S3 Bucket Name

### Problem

An upload was attempted using:

s3://cloudnova/

AWS returned:

NoSuchBucket

### Root Cause

The actual Terraform-generated bucket name contained a unique suffix.

### Resolution

The correct bucket name was retrieved and used.

### Verification

The object uploaded successfully and appeared in the bucket listing.

---

## 3. EC2 Had No SSH Key Pair

### Problem

The EC2 KeyName returned:

None

### Decision

Rather than rebuilding the instance around SSH key management, AWS Systems Manager Session Manager was implemented.

### Result

Administrative access became available without an EC2 private key.

---

## 4. Missing Session Manager Plugin

### Problem

Running:

aws ssm start-session

returned:

SessionManagerPlugin is not found

### Root Cause

The local Windows workstation did not have the Session Manager Plugin installed.

### Resolution

The AWS Session Manager Plugin was installed.

### Verification

A successful SSM session was established.

---

## 5. AWS CLI Missing on EC2

### Problem

Inside the EC2 instance:

aws: not found

### Root Cause

AWS CLI was not installed on the Ubuntu instance.

### Resolution

AWS CLI v2 was downloaded using the official AWS installer.

---

## 6. Ubuntu awscli Package Unavailable

### Problem

apt returned:

Package 'awscli' has no installation candidate

### Resolution

The official AWS CLI v2 ZIP installer was used instead of the Ubuntu package.

### Verification

aws --version returned a valid AWS CLI v2 installation.

---

## 7. Permission Denied Downloading AWS CLI

### Problem

curl returned:

Permission denied

when writing awscliv2.zip.

### Root Cause

ssm-user did not have write permission in the current directory.

### Resolution

The installer was downloaded to:

/tmp

---

## 8. Permission Denied Creating S3 Test File

### Problem

The EC2 session returned:

cannot create ec2-test.txt: Permission denied

### Root Cause

ssm-user could not write to the current directory.

### Resolution

The session moved to:

/tmp

The test file was created successfully.

### Verification

ec2-test.txt was uploaded successfully to S3.

---

## Engineering Takeaway

The project reinforced a troubleshooting workflow based on:

Problem → Evidence → Investigation → Root Cause → Resolution → Verification

Rather than rebuilding infrastructure immediately when an error occurred, AWS CLI, Terraform state, IAM configuration, Linux permissions, and service status were used to identify the underlying cause.