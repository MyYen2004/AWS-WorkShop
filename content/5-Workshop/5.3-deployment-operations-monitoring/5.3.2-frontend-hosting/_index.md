---
title: "Serverless Backend Deployment with API Gateway and AWS Lambda"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.3.2 </b> "
aliases:
  - /5-workshop/5.3-deployment-operations-monitoring/5.3.2-frontend-hosting-auth/
---

## 5.3.2 Serverless Backend Deployment with API Gateway and AWS Lambda

This section presents the deployment process of the CloudMenu Backend using a Serverless architecture, with Amazon API Gateway serving as the API endpoint and AWS Lambda handling the business logic.

### 1. Backend Preparation

Review the Backend source code and identify the main business operations of CloudMenu. The Backend handles requests from the Customer, Kitchen, and Manager interfaces.

The main operations include:

- Create Order — creates a new order.
- Get Orders — retrieves order information or a list of orders.
- Update Order Status — updates the status of an order.
### 2. Deploying AWS Lambda

Create AWS Lambda functions to handle the business logic of CloudMenu.

Lambda receives requests from API Gateway, processes the data, and performs read/write operations with Amazon DynamoDB.

Processing flow:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

### 3. Configuring Amazon API Gateway

Create API endpoints and connect each endpoint to the corresponding Lambda function.

API Gateway is responsible for:

- Receiving requests from the frontend.
- Forwarding requests to Lambda.
- Receiving responses from Lambda and returning them to the frontend.
- Configuring CORS so that the frontend distributed through CloudFront can access the APIs.
### 4. Backend Testing

After deployment, test the main APIs and the system processing flow:

Browser/Phone → API Gateway → Lambda → DynamoDB

Verify that Customer can submit orders, Kitchen can retrieve and update orders, and Manager can retrieve data for the Dashboard.

### 5. Monitoring and Operation

Check API responses, Lambda errors, and data written to DynamoDB. Amazon CloudWatch can be used to monitor Lambda logs during testing and system operation.

Result: The CloudMenu Backend is deployed using a Serverless architecture, where API Gateway receives requests and Lambda processes the business logic without requiring a dedicated Backend server.