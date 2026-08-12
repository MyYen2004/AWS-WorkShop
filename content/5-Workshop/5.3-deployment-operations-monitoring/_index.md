---
title: "Serverless System Deployment and Operations"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## 5.3 Serverless System Deployment and Operations

This chapter presents the process of deploying and operating CloudMenu on AWS, focusing on deploying the frontend to the AWS environment, deploying the Serverless backend components, and integrating AWS services to make the system fully operational.

CloudMenu uses a Serverless architecture with Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, and AWS IAM. The frontend is managed on GitHub and is currently uploaded manually to Amazon S3, after which Amazon CloudFront distributes the content to users.

The backend is deployed using Amazon API Gateway and AWS Lambda. Lambda handles the main CloudMenu business operations and reads/writes order data in the CloudMenuOrders table on Amazon DynamoDB.

### Deployment and Operations Flow

The CloudMenu deployment process consists of the following main steps:

- Source Code Preparation
    - Clone or download the CloudMenu source code from GitHub.
    - Check the HTML, CSS, and JavaScript frontend files.
    - Check the API endpoint configuration used by the frontend.
- Frontend Deployment
    - Create and configure an Amazon S3 bucket to store the frontend.
    - Upload the HTML, CSS, JavaScript, and static resources to S3.
    - Configure Amazon CloudFront with S3 as the origin.
    - Verify that the Customer, Kitchen, and Manager interfaces can be accessed through CloudFront.
- Serverless Backend Deployment
    - Create and configure the AWS Lambda functions.
    - Implement the main CloudMenu business APIs.
    - Connect Amazon API Gateway with the corresponding Lambda functions.
    - Test requests and responses between the frontend, API Gateway, and Lambda.
- DynamoDB Configuration
    - Create the CloudMenuOrders table in Amazon DynamoDB.
    - Configure orderId as the Partition Key.
    - Test order creation, retrieval, and update operations.
    - Verify the order status flow: PENDING → PREPARING → COMPLETED.
- IAM Configuration
    - Create and configure an IAM Role for AWS Lambda.
    - Grant the required permissions for Lambda to access DynamoDB.
    - Apply the Least Privilege principle.
    - Verify access permissions before operating the system.
- Testing and Operations
    - Test the frontend through CloudFront.
    - Test the main APIs: Create Order, Get Orders, and Update Order Status.
    - Test the ordering flow from Customer to Kitchen.
    - Test the Manager Dashboard.
    - Check Lambda logs and errors that may occur during processing.

### Deployment Architecture

CloudMenu is deployed through two main flows:

- Frontend Deployment Flow

Developer → GitHub → Deploy/Upload → Amazon S3 → Amazon CloudFront → Browser/Phone

Currently, the source code is managed on GitHub and the frontend is manually uploaded to Amazon S3. An automated CI/CD process from GitHub to S3 has not yet been implemented.

- Backend Request Flow

Browser/Phone → Amazon API Gateway → AWS Lambda → Amazon DynamoDB

The frontend sends requests to API Gateway. API Gateway forwards the requests to the corresponding Lambda function. Lambda processes the business logic and performs read/write operations on DynamoDB, then returns the result to the frontend through API Gateway.

### Why Use a Serverless Architecture

The Serverless architecture allows CloudMenu to reduce the need to manage traditional backend servers. Amazon API Gateway and AWS Lambda handle incoming requests and business logic, while Amazon DynamoDB provides a managed data storage layer.

The frontend is stored on Amazon S3 and distributed through Amazon CloudFront, separating frontend content delivery from backend request processing.

### Content

1. [4.3.1 Frontend Deployment with Amazon S3 and Amazon CloudFront ](4.3.1-run-infrastructure-terraform/)
2. [4.3.2 Serverless Backend Deployment with API Gateway and AWS Lambda](4.3.2-frontend-hosting/)
3. [4.3.3 DynamoDB Integration and System Testing](4.3.3-backend/)
