---
title : "DynamoDB & Data Model"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 4.2.3 </b> "
---

## 4.2.3 DynamoDB & Data Model

CloudMenu uses Amazon DynamoDB as the primary database to store and manage order information. DynamoDB is an AWS managed NoSQL database service, making it suitable for the Serverless architecture of the system.

- Amazon DynamoDB

Amazon DynamoDB stores the main order information, including:

    - Order ID
    - Table number
    - Order status
    - List of food items
    - Total amount
    - Order creation time
    - Update time
    - Completion time

The main table of the system is CloudMenuOrders.

- CloudMenuOrders Data Model

The CloudMenuOrders table uses orderId as the Partition Key.

Main attributes include:

    - orderId — Partition Key, identifies the order.
    - tableNumber — table number.
    - status — order status.
    - items — list of food items.
    - totalAmount — total order amount.
    - createdAt — order creation time.
    - updatedAt — update time.
    - completedAt — order completion time.

![CloudMenu AWS architecture](/images/3.jpg)

Each item in items contains:

    - itemId
    - name
    - price
    - quantity

- Order Status

Orders are managed through three statuses:

PENDING → PREPARING → COMPLETED

PENDING — The order has been submitted and is waiting to be processed.
PREPARING — The order is being prepared by the kitchen staff.
COMPLETED — The order has been completed.

- Data Flow

Order data is processed through the Serverless architecture:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

AWS Lambda performs operations to create, read, and update data in the CloudMenuOrders table.

- NoSQL Data Model

CloudMenu uses the NoSQL data model provided by DynamoDB instead of a relational database model. Order information and the list of food items are organized within the same item, matching the access patterns of the system.