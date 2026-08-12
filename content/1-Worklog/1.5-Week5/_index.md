---
title: "Week 5 Worklog"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Goals

- Learn about NoSQL databases with Amazon DynamoDB.
- Design the data model for the CloudMenu system.
- Create the CloudMenuOrders table and configure orderId as the Partition Key.
- Integrate AWS Lambda with DynamoDB to create, read, and update order data.
- Build and test the order status flow:
PENDING → PREPARING → COMPLETED.
- Verify the accuracy of order data stored in DynamoDB.

**Time Period:** 20/07/2026 - 24/07/2026

---

### Weekly Tasks Overview

| Day | Activity                                                                                                                                                                                                                          | Start Date | End Date   | Reference                                         |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ------------------------------------------------- |
| 1 | - Study NoSQL databases with Amazon DynamoDB. <br> - Learn the concepts of Table, Item, Attribute, and Partition Key. | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html?utm_source=chatgpt.com> |
| 2 | - Analyze and design the CloudMenu data model. <br> - Identify the main order attributes and configure orderId as the Partition Key. | 21/07/2026 | 21/07/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html?utm_source=chatgpt.com> |
| 3 | - Create the CloudMenuOrders table in Amazon DynamoDB. <br> - Test creating, reading, and managing order data in the table. | 22/07/2026 | 22/07/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html?utm_source=chatgpt.com> |
| 4 | - Integrate AWS Lambda with Amazon DynamoDB. <br> - Perform order creation, retrieval, and update operations through Lambda. <br> - Test the API Gateway → Lambda → DynamoDB flow. | 23/07/2026 | 23/07/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway-tutorial.html?utm_source=chatgpt.com> |
| 5 | - Implement and test the order status flow PENDING → PREPARING → COMPLETED. <br> - Verify the accuracy and consistency of order data in DynamoDB. <br> - Complete the integration between the Backend and Data Layer. | 24/07/2026 | 24/07/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transactions.html?utm_source=chatgpt.com> |

---

### Week 5 Achievements

- Gained an understanding of Amazon DynamoDB and the NoSQL database model.
- Designed and implemented the CloudMenuOrders table with orderId as the Partition Key.
- Defined and implemented the main attributes of the order data.
- Successfully integrated AWS Lambda with Amazon DynamoDB to create, retrieve, and update order data.
- Completed the order status workflow PENDING → PREPARING → COMPLETED.
- Verified that order data was correctly stored and updated in DynamoDB.
