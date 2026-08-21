# Amazon S3 Storage

## Bucket

Terraform creates a CloudNova S3 bucket using a unique naming strategy based on the AWS account identifier.

## Public Access

S3 Block Public Access is enabled.

## Versioning

Bucket versioning is enabled to preserve multiple versions of objects.

## EC2 Access

The CloudNova EC2 IAM Role is allowed to:

- List the bucket
- Upload objects
- Download objects

## Testing

An initial test object was uploaded through the local AWS CLI.

A second test was performed directly from the EC2 instance.

The EC2 instance created:

ec2-test.txt

The object was uploaded using:

aws s3 cp ec2-test.txt s3://<cloudnova-bucket>/

The bucket listing confirmed both test objects existed.

This verified:

EC2 → IAM Role → S3