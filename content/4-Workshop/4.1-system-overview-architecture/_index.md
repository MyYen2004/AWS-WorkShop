---
title : "System overview and architecture"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

## 4.1 System overview and architecture

### Overview

**CloudMenu** is a table-side online ordering system that allows customers to scan a unique QR code at each table to view the menu, select dishes, and submit orders.

The architecture is designed using a Serverless approach on AWS to provide:

- Flexible scalability as the number of customers and orders changes.
- Fast order processing through Amazon API Gateway and AWS Lambda.
- Order data storage and management using Amazon DynamoDB.
- Reliable frontend distribution through Amazon S3 and Amazon CloudFront.
- Access control and security management through AWS IAM..

### Architecture

![CloudMenu AWS architecture](/images/AWS_CloudMenu.png)