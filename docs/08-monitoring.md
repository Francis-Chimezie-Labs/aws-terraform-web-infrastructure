# CloudWatch Monitoring and SNS

## CloudWatch

Amazon CloudWatch monitors EC2 CPU utilization.

## Alarm

Alarm name:

cloudnova-high-cpu

Metric:

CPUUtilization

Threshold:

70%

Period:

5 minutes

Evaluation periods:

2

## SNS

Terraform provisions an SNS topic for infrastructure alerts.

An email subscription provides an operational notification channel.

## Verification

The CloudWatch alarm was queried through AWS CLI and reported:

State: OK
Threshold: 70%

CPUUtilization datapoints were successfully retrieved from CloudWatch.

This confirmed that CloudWatch was receiving metrics from the CloudNova EC2 instance.

End-to-end ALARM-state notification testing should be documented separately once performed.