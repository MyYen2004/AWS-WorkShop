---
title: "Worklog"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

**Week 1 (22/06 - 26/06):** [Introduction to AWS and Core Services](1.1-week1/)

- Learn about the AWS Cloud platform and major service categories such as Compute, Storage, Database, and Networking.
- Get familiar with the AWS Management Console and AWS CLI.
- Practice basic AWS operations and learn about application deployment models in the Cloud.
- Learn the fundamental concepts of Serverless Architecture and AWS services suitable for CloudMenu.

**Week 2 (29/06 - 03/07):** [AWS IAM, S3, and CloudMenu Architecture](1.2-week2/)

- Learn and practice AWS IAM for managing access to AWS resources.
- Study Amazon S3 and its use for storing frontend files.
- Learn about Amazon CloudFront and content delivery through a CDN.
- Analyze requirements and identify the main components of the CloudMenu system.
- Identify the Customer, Kitchen, and Manager user groups and their corresponding functions.

**Week 3 (06/07 - 10/07):** [Frontend Development and AWS Deployment](1.3-week3/)

- Build and complete the CloudMenu interfaces using HTML, CSS, and JavaScript.
- Develop the Customer, Order Status, Kitchen, and Manager Dashboard interfaces.
- Build the ordering flow from QR scanning → table identification → menu viewing → item selection → order submission.
- Upload the frontend to Amazon S3.
- Configure Amazon CloudFront to distribute the frontend to users.
- Verify that CloudMenu can be accessed through CloudFront.

**Week 4 (13/07 - 17/07):** [API Gateway and AWS Lambda](1.4-week4/)

- Learn about Serverless Backend architecture on AWS.
- Build AWS Lambda functions to handle CloudMenu business logic.
- Use Amazon API Gateway to create API endpoints.
- Implement the main APIs:
    - Create Order
    - Get Orders
    - Update Order Status
- Test the Frontend → API Gateway → Lambda request flow.
- Configure CORS to allow the frontend to communicate with the APIs.

**Week 5 (20/07 - 24/07):** [Amazon DynamoDB and Order Data Management](1.5-week5/)

- Learn about NoSQL databases with Amazon DynamoDB.
- Design the data model for the CloudMenu system.
- Create the CloudMenuOrders table and configure orderId as the Partition Key.
- Integrate AWS Lambda with DynamoDB to create, read, and update order data.
- Build and test the order status flow:
PENDING → PREPARING → COMPLETED.
- Verify the accuracy of order data stored in DynamoDB.

**Week 6 (27/07 - 31/07):** [Business Logic Completion and System Integration](1.6-week6/)

- Complete the main functions for Customer, Kitchen, and Manager.
- Integrate the Customer interface with the API to submit and track orders.
- Integrate the Kitchen interface to view and update order statuses.
- Complete the Manager Dashboard with statistical information.
- Verify total orders, revenue, order status, revenue by table, and most frequently ordered items.
- Test the end-to-end processing flow from Customer → Kitchen → Manager.

**Week 7 (03/08 - 07/08):** [Security, IAM, and Monitoring](1.7-week7/)

- Complete access control using AWS IAM.
- Configure an IAM Role for Lambda to access Amazon DynamoDB.
- Apply the Least Privilege principle to Lambda permissions.
- Identify and resolve errors occurring during API and Lambda execution.
- Test CORS, API responses, and system error scenarios.
- Review the security configuration of the AWS services used by CloudMenu.

**Week 8 (10/08 - 14/08):** [Testing, Optimization, and CloudMenu Completion](1.8-week8/)

- Test the complete CloudMenu system in the AWS environment.
- Verify the main system flow:
Customer → Order → Kitchen → Completed → Manager Dashboard.
- Verify the operation of S3, CloudFront, API Gateway, Lambda, DynamoDB, IAM.
- Monitor and optimize AWS costs for a low-traffic system.
- Review the Serverless architecture and CloudMenu's scalability.
- Complete the Architecture Diagram, Order Workflow Diagram, Use Case Diagram, Data Model Diagram, and Deployment/Request Flow Diagram.
- Complete the Proposal including Architecture, Implementation Plan, Cost, Risk, and Expansion Roadmap.
- Finalize the technical documentation and summarize the internship results.

