---
title : "Cost, risk, and expansion roadmap"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.4. </b> "
---

## 5.4 Cost, risk, and expansion roadmap

### Cost optimization
- Monitor costs across the main services: Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda, and Amazon DynamoDB.
- Prioritize configurations suitable for development environments and low-traffic systems:
  - Leverage Amazon S3 to host the frontend instead of maintaining a dedicated server.
  - Use Amazon CloudFront to distribute content and reduce the number of direct requests to S3.
  - Monitor the number of requests and execution time of AWS Lambda.
  - Optimize read and write operations in Amazon DynamoDB.
  - Regularly review AWS costs and resource usage to identify any unusual charges.

### Risks and mitigation
- Risk of increased costs as the number of customers, orders, and API requests grows.
- Risk of inconsistent order statuses between Customers and Kitchen staff during the PENDING → PREPARING → COMPLETED workflow.
- Risk of API or Lambda failures, which may prevent customers from submitting orders or kitchen staff from updating order statuses.
- Risk of lost or incorrect order data during read/write operations in Amazon DynamoDB.
- Risk of inappropriate AWS permissions if Lambda functions or other resources are granted excessive permissions.
- Risk of frontend inaccessibility due to incorrect Amazon S3 or Amazon CloudFront configuration.
- Mitigation: Test APIs and Lambda functions, validate input data, apply the Least Privilege principle with AWS IAM, monitor logs, verify S3/CloudFront configurations, and regularly monitor AWS costs.

### Expansion roadmap
- Build a CI/CD pipeline to automate the frontend deployment process to Amazon S3.
- Add automated testing and smoke testing for key APIs such as Create Order, Get Orders, and Update Order Status.
- Enhance monitoring and logging through Amazon CloudWatch to monitor Lambda functions and detect errors.
- Strengthen IAM security and access control by applying the Least Privilege principle to each service.
- Improve the system's ability to handle increasing numbers of customers and orders.
- Consider expanding the architecture with additional AWS services when CloudMenu is deployed at a production scale.