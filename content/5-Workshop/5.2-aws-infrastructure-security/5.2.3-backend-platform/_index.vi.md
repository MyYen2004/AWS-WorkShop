---
title : "DynamoDB & Data Model"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.2.3 </b> "
---

## 5.2.3 DynamoDB & Data Model

CloudMenu sử dụng Amazon DynamoDB làm cơ sở dữ liệu chính để lưu trữ và quản lý thông tin đơn hàng. DynamoDB là cơ sở dữ liệu NoSQL managed service của AWS, phù hợp với kiến trúc Serverless của hệ thống.

- Amazon DynamoDB

Amazon DynamoDB lưu trữ các thông tin chính của đơn hàng, bao gồm:

    - Mã đơn hàng.
    - Số bàn.
    - Trạng thái đơn hàng.
    - Danh sách món ăn.
    - Tổng tiền.
    - Thời gian tạo đơn hàng.
    - Thời gian cập nhật.
    - Thời gian hoàn thành.

Table chính của hệ thống là CloudMenuOrders.

- CloudMenuOrders Data Model

Table CloudMenuOrders sử dụng orderId làm Partition Key.

Các thuộc tính chính:

    - orderId — Partition Key, định danh đơn hàng.
    - tableNumber — số bàn.
    - status — trạng thái đơn hàng.
    - items — danh sách món ăn.
    - totalAmount — tổng giá trị đơn hàng.
    - createdAt — thời gian tạo đơn.
    - updatedAt — thời gian cập nhật.
    - completedAt — thời gian hoàn thành.

![CloudMenu AWS architecture](/images/3.jpg)

Mỗi phần tử trong items bao gồm:

    - itemId
    - name
    - price
    - quantity

- Order Status

Đơn hàng được quản lý theo ba trạng thái:

PENDING → PREPARING → COMPLETED

PENDING — Đơn hàng đã được gửi và đang chờ xử lý.
PREPARING — Đơn hàng đang được nhân viên bếp chế biến.
COMPLETED — Đơn hàng đã hoàn thành.

- Data Flow

Dữ liệu đơn hàng được xử lý thông qua kiến trúc Serverless:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

AWS Lambda thực hiện các thao tác đọc, tạo và cập nhật dữ liệu trong table CloudMenuOrders.

- NoSQL Data Model

CloudMenu sử dụng mô hình dữ liệu NoSQL của DynamoDB thay vì mô hình cơ sở dữ liệu quan hệ. Dữ liệu đơn hàng và danh sách món được tổ chức trong cùng một item, phù hợp với các access pattern của hệ thống.