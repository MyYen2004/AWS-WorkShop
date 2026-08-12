---
title : "Frontend Hosting & Content Delivery"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.2.1 </b> "
---

## 4.2.1 Frontend Hosting & Content Delivery

CloudMenu sử dụng Amazon S3 để lưu trữ các file frontend được xây dựng bằng HTML, CSS và JavaScript. Frontend bao gồm giao diện dành cho Customer, Kitchen và Manager.

Amazon CloudFront được sử dụng để phân phối các file frontend từ Amazon S3 đến người dùng thông qua mạng CDN, giúp các giao diện CloudMenu có thể được truy cập từ Internet thông qua CloudFront.

- Amazon S3

Amazon S3 đóng vai trò là nơi lưu trữ frontend và các tài nguyên tĩnh của CloudMenu. Các file frontend được upload lên S3 để triển khai hệ thống.

- Amazon CloudFront

Amazon CloudFront đóng vai trò là lớp phân phối nội dung phía trước Amazon S3. Người dùng truy cập CloudMenu thông qua CloudFront thay vì truy cập trực tiếp vào S3.

- Frontend Deployment Flow

Frontend được quản lý trên GitHub và hiện tại được upload thủ công lên Amazon S3. Sau đó, Amazon CloudFront sử dụng S3 làm nguồn nội dung để phân phối frontend.

- Luồng triển khai:

Developer → GitHub → Deploy/Upload → Amazon S3 → Amazon CloudFront → Browser/Phone

- User Access Flow

Customer / Kitchen / Manager → Amazon CloudFront → Amazon S3

