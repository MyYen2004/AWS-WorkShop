---
title : "API Gateway & Serverless Backend"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 4.2.2 </b> "
---

## 4.2.2 API Gateway & Serverless Backend

CloudMenu uses Amazon API Gateway and AWS Lambda to build its Backend using a Serverless architecture. API Gateway acts as the API endpoint that receives requests from the frontend, while Lambda handles the system's business logic.

- Amazon API Gateway

Amazon API Gateway provides API endpoints for the frontend to communicate with the Backend. The main requests of CloudMenu include:

    - Create Order — creates a new order.
    - Get Orders — retrieves order information or a list of orders.
    - Update Order Status — updates the status of an order.

API Gateway receives requests from the Customer, Kitchen, and Manager interfaces and forwards them to the corresponding AWS Lambda functions.

- AWS Lambda

AWS Lambda handles the business logic of CloudMenu without requiring a dedicated backend server.

Lambda processes requests such as:

    - Receiving and processing orders from Customers.
    - Retrieving order information for Kitchen staff.
    - Updating order statuses.
    - Providing data for the Manager Dashboard.

Lambda reads and writes data to Amazon DynamoDB. The data model and order storage structure are described in detail in 4.2.3 DynamoDB & Data Model.

- Request Flow

The main request flow of CloudMenu is:

Frontend / Browser → Amazon API Gateway → AWS Lambda → Amazon DynamoDB

After Lambda completes the processing, the result is returned to the frontend through API Gateway.

- CORS

API Gateway is configured with CORS to allow the frontend distributed through CloudFront to send requests to the CloudMenu APIs.

- Serverless Architecture

Using API Gateway and Lambda allows CloudMenu to operate without managing traditional backend servers. AWS manages the provisioning and execution of Lambda functions based on incoming requests, making this architecture suitable for a system with varying levels of traffic.