---
title : "Các dịch vụ AWS và bảo mật"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

## 5.2 Các dịch vụ AWS và bảo mật

![CloudMenu AWS architecture](/images/4.jpg)

Nền tảng AWS và bảo mật. CloudMenu được triển khai trên AWS theo kiến trúc Serverless, sử dụng các dịch vụ AWS managed để lưu trữ, phân phối frontend, xử lý API, lưu trữ dữ liệu và quản lý quyền truy cập.

Kiến trúc hệ thống được chia thành các thành phần chính:

- Frontend Hosting & Content Delivery — Amazon S3 lưu trữ các file frontend và Amazon CloudFront phân phối nội dung đến Customer, Kitchen và Manager.
- API & Application Layer — Amazon API Gateway cung cấp các API endpoint và AWS Lambda xử lý logic nghiệp vụ như tạo đơn hàng, lấy danh sách đơn và cập nhật trạng thái đơn hàng.
- Data Layer — Amazon DynamoDB lưu trữ dữ liệu đơn hàng của CloudMenu theo mô hình NoSQL.
- Security & Access Control — AWS IAM quản lý quyền truy cập giữa các dịch vụ AWS, đặc biệt là quyền của Lambda khi thực hiện các thao tác với DynamoDB.

Chi tiết kiến trúc được chia thành các module phù hợp với từng thành phần của CloudMenu:

- 4.2.1 Frontend Hosting và Content Delivery
    - Amazon S3
    - Amazon CloudFront
    - Luồng truy cập: Customer / Kitchen / Manager → CloudFront → S3
- 4.2.2 API Gateway và Serverless Backend
    - Amazon API Gateway
    - AWS Lambda
    - Các API chính: Create Order, Get Orders, Update Order Status
    - Luồng xử lý: Frontend → API Gateway → Lambda
- 4.2.3 DynamoDB và mô hình dữ liệu
    - Amazon DynamoDB
    - Table: CloudMenuOrders
    - Dữ liệu: orderId, tableNumber, status, items, totalAmount, createdAt, updatedAt, completedAt
    - Trạng thái đơn: PENDING → PREPARING → COMPLETED
- 4.2.4 IAM và bảo mật hệ thống
    - AWS IAM
    - IAM Roles và Policies
    - Phân quyền Lambda truy cập DynamoDB theo nguyên tắc Least Privilege.

![CloudMenu AWS architecture](/images/1.jpg)

1. [4.2.1 Frontend Hosting & Content Delivery](4.2.1-vpc-network/).
2. [4.2.2 API Gateway & Serverless Backend](4.2.2-client-facing/).
3. [4.2.3 DynamoDB & Data Model](4.2.3-backend-platform/).
4. [4.2.4 IAM & Security](4.2.4-database/).
