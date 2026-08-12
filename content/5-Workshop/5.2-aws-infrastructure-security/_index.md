---
title : "AWS Services and Security"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

## 5.2 AWS Services and Security

![CloudMenu AWS architecture](/images/4.jpg)

AWS Platform and Security. CloudMenu is deployed on AWS using a Serverless architecture, leveraging AWS managed services for frontend hosting, content delivery, API processing, data storage, and access control.

The system architecture is divided into the following main components:

- Frontend Hosting & Content Delivery — Amazon S3 stores the frontend files, while Amazon CloudFront distributes the content to Customers, Kitchen staff, and Managers.
- API & Application Layer — Amazon API Gateway provides API endpoints, while AWS Lambda handles business logic such as creating orders, retrieving orders, and updating order statuses.
- Data Layer — Amazon DynamoDB stores CloudMenu order data using a NoSQL data model.
- Security & Access Control — AWS IAM manages access permissions between AWS services, particularly the permissions required by Lambda to perform operations on DynamoDB.

The detailed architecture is divided into modules corresponding to the main components of CloudMenu:

- 4.2.1 Frontend Hosting & Content Delivery
    - Amazon S3
    - Amazon CloudFront
    - Access flow: Customer / Kitchen / Manager → CloudFront → S3
- 4.2.2 API Gateway & Serverless Backend
    - Amazon API Gateway
    - AWS Lambda
    - Main APIs:
        - Create Order
        - Get Orders
        - Update Order Status
    - Processing flow: Frontend → API Gateway → Lambda
- 4.2.3 DynamoDB & Data Model
    - Amazon DynamoDB
    - Table: CloudMenuOrders
    - Main attributes:
        - orderId
        - tableNumber
        - status
        - items
        - totalAmount
        - createdAt
        - updatedAt
        - completedAt
    - Order status flow: PENDING → PREPARING → COMPLETED
- 4.2.4 IAM & Security
    - AWS Identity and Access Management (IAM)
    - IAM Roles and Policies
    - Lambda is granted permission to access DynamoDB according to the Least Privilege principle, ensuring that each service receives only the permissions required to perform its intended operations.

![CloudMenu AWS architecture](/images/1.jpg)

1. [4.2.1 Frontend Hosting & Content Delivery](4.2.1-vpc-network/).
2. [4.2.2 API Gateway & Serverless Backend](4.2.2-client-facing/) 
3. [4.2.3 DynamoDB & Data Model](4.2.3-backend-platform/)
4. [4.2.4 IAM & Security](4.2.4-database/).