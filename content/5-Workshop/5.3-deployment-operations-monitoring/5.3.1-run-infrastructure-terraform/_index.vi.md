---
title: "Triển khai Frontend với Amazon S3 và Amazon CloudFront"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.3.1 </b> "
aliases:
  - /5-workshop/5.3-deployment-operations-monitoring/5.3.1-vpc-network/
---

## 5.3.1 Triển khai Frontend với Amazon S3 và Amazon CloudFront

### 1. Chuẩn bị Frontend

CloudMenu sử dụng frontend được xây dựng bằng HTML, CSS và JavaScript, bao gồm các giao diện:

- Customer
- Order Status
- Kitchen
- Manager Dashboard

Source code frontend được quản lý trên GitHub. Trước khi triển khai, kiểm tra cấu trúc file và các API endpoint mà frontend sử dụng.

### 2. Upload Frontend lên Amazon S3

Tạo một Amazon S3 bucket để lưu trữ các file frontend của CloudMenu.

Các file HTML, CSS, JavaScript và các tài nguyên tĩnh được upload thủ công lên S3.

Có thể mô tả luồng:

Developer → GitHub → Deploy/Upload → Amazon S3

![CloudMenu AWS architecture](/images/2.jpg)

Lưu ý: Hiện tại CloudMenu chưa sử dụng CI/CD tự động từ GitHub đến S3. Việc upload frontend lên S3 được thực hiện thủ công.

### 3. Cấu hình Amazon CloudFront

Sau khi frontend được lưu trữ trên S3, tạo CloudFront Distribution và cấu hình Amazon S3 làm origin.

CloudFront chịu trách nhiệm phân phối các file frontend đến người dùng thông qua mạng CDN.

Luồng phân phối: Amazon S3 → Amazon CloudFront → Browser/Phone

### 4. Truy cập CloudMenu

Sau khi CloudFront Distribution được triển khai, người dùng có thể truy cập CloudMenu thông qua CloudFront URL.

Các nhóm người dùng có thể truy cập các giao diện tương ứng:

Customer / Kitchen / Manager → Amazon CloudFront → Amazon S3

Customer có thể mở giao diện gọi món bằng điện thoại sau khi quét QR của bàn.

### 5. Kiểm tra sau khi triển khai

Sau khi triển khai, kiểm tra:

- CloudFront URL có truy cập được hay không.
- Các file HTML, CSS, JavaScript có tải đúng hay không.
- Các giao diện Customer, Kitchen và Manager có hoạt động hay không.
- Frontend có gọi được API Gateway hay không.
- Kiểm tra lỗi CORS nếu frontend không thể gửi request đến API.


