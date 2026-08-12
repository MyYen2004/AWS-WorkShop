---
title : "IAM & Security"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 4.2.4 </b> "
---

## 4.2.4 IAM & Security

CloudMenu uses AWS Identity and Access Management (IAM) to manage access permissions between AWS services and control the actions that each component of the system is allowed to perform.

- AWS IAM

IAM is used to manage access to CloudMenu's AWS resources. In the system, an IAM Role is assigned to AWS Lambda so that Lambda can perform the required operations on Amazon DynamoDB.

- IAM Role

AWS Lambda uses an IAM Role to define the permissions that the function is allowed to perform.

The IAM Role assigned to Lambda is configured to allow:

    - Read data from Amazon DynamoDB.
    - Create order data in Amazon DynamoDB.
    - Update order data in Amazon DynamoDB.
    - Write Lambda activity logs to Amazon CloudWatch.

- Least Privilege

CloudMenu follows the Least Privilege principle, meaning that each Lambda function is granted only the permissions required for its specific business operations.

Limiting permissions helps reduce the risk of a function accessing or modifying AWS resources that it does not need.

- Security Flow

Access permissions between the components are controlled through IAM:

Amazon API Gateway → AWS Lambda → IAM Role → Amazon DynamoDB

Lambda uses its IAM Role to authenticate and perform the permitted operations on DynamoDB.

- Security Considerations

The following security principles are applied to CloudMenu:

    - Do not store AWS credentials directly in the source code.
    - Use IAM Roles instead of storing access keys for Lambda.
    - Grant only the permissions required by each Lambda function.
    - Restrict access to the CloudMenuOrders table.
    - Regularly review IAM Policies during system operation.