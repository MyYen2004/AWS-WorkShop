---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Workshop: Kiến trúc CloudMenu trên AWS

Phần workshop này đi sâu vào kiến trúc hệ thống AWS của CloudMenu: các dịch vụ AWS được sử dụng, luồng xử lý giữa frontend và backend, mô hình Serverless và cơ chế quản lý quyền truy cập.

Kiến trúc và triển khai CloudMenu được trình bày theo từng thành phần, bao gồm Amazon S3 và Amazon CloudFront cho việc lưu trữ và phân phối frontend, Amazon API Gateway và AWS Lambda cho xử lý backend theo kiến trúc Serverless, Amazon DynamoDB cho lưu trữ dữ liệu đơn hàng, và AWS IAM cho quản lý quyền truy cập và bảo mật.

Các nội dung về luồng gọi món, triển khai frontend, xử lý API, mô hình dữ liệu DynamoDB, phân quyền IAM và monitoring Lambda được trình bày trong các phần tương ứng của workshop, giúp làm rõ cách các dịch vụ AWS phối hợp để vận hành hệ thống CloudMenu.

Nội dung được gom thành các nhóm chính để thuận tiện theo dõi:
- Tổng quan và kiến trúc hệ thống CloudMenu.
- Các dịch vụ AWS và cơ chế bảo mật.
- Triển khai và vận hành hệ thống Serverless.
- Chi phí, rủi ro và định hướng mở rộng.
- Dọn dẹp và quản lý tài nguyên AWS.

#### Nội dung

1. [4.1 Tổng quan và kiến trúc hệ thống](4.1-system-overview-architecture/)
2. [4.2 Các dịch vụ AWS và bảo mật](4.2-aws-infrastructure-security/)
3. [4.3 Triển khai và vận hành hệ thống Serverless](4.3-deployment-operations-monitoring/)
4. [4.4 Chi phí, rủi ro và định hướng mở rộng](4.4-cost-risk-expansion-roadmap/)
5. [4.5 Dọn dẹp tài nguyên](4.5-legacy-cleanup/)