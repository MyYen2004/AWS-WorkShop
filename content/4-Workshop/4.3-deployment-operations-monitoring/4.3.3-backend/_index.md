---
title: "DynamoDB Integration and System Testing"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3.3 </b> "
---

## 4.3.3 DynamoDB Integration and System Testing

This section presents the integration of Amazon DynamoDB with the CloudMenu Serverless Backend and the testing of the complete system processing flow.

### 1. Amazon DynamoDB Configuration

CloudMenu uses Amazon DynamoDB to store order data. Create the CloudMenuOrders table and use orderId as the Partition Key.

The main order attributes include:

- orderId — order ID.
- tableNumber — table number.
- status — order status.
- items — list of ordered items.
- totalAmount — total order amount.
- createdAt — order creation time.
- updatedAt — update time.
- completedAt — completion time.

### 2. Integrating Lambda with DynamoDB

AWS Lambda is connected to Amazon DynamoDB to perform data read and write operations.

The main operations include:

- Creating new orders.
- Retrieving order information and order lists.
- Updating order status.
- Retrieving data for the Dashboard.

Processing flow:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

### 3. Order Flow Testing

Test the complete process from the Customer submitting an order to the order being completed:

Scan QR → Identify Table → View Menu → Select Items → Cart → Submit Order → PENDING → PREPARING → COMPLETED

Verify that the table number, ordered items, total amount, and order status are correctly stored in DynamoDB.

### 4. Interface Testing

Test the main functions of each user group:

- Customer: Submit orders and track order status.
- Kitchen: View orders and update the preparation status.
- Manager: Retrieve order data and display statistical information on the Dashboard.

The synchronization of order status between the Customer and Kitchen interfaces is also verified.

### 5. System Monitoring and Verification

After completing the tests, verify the data stored in CloudMenuOrders, API responses, and any errors occurring during Lambda execution.

Amazon CloudWatch is used to monitor Lambda logs and help identify errors during system operation.

Overall Testing Flow

Customer / Kitchen / Manager → CloudFront → Frontend → API Gateway → Lambda → DynamoDB

Result: The integration between Amazon DynamoDB and the Serverless Backend is completed, and the main CloudMenu functions are verified to work correctly from the frontend through to the data layer.