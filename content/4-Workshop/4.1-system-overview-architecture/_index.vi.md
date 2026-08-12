---
title : "Tổng quan và kiến trúc hệ thống"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

## 4.1 Tổng quan và kiến trúc hệ thống

### Tổng quan

**CloudMenu** là hệ thống gọi món trực tuyến tại bàn, cho phép khách hàng quét mã QR riêng của từng bàn để xem thực đơn, lựa chọn món và gửi đơn gọi món.

Kiến trúc được thiết kế theo hướng Serverless trên AWS nhằm:

- Khả năng mở rộng linh hoạt khi số lượng khách hàng và đơn hàng thay đổi.
- Xử lý đơn hàng nhanh chóng thông qua Amazon API Gateway và AWS Lambda.
- Lưu trữ và quản lý dữ liệu đơn hàng bằng Amazon DynamoDB.
- Phân phối giao diện ổn định thông qua Amazon S3 và Amazon CloudFront.
- Quản lý quyền truy cập và bảo mật thông qua AWS IAM.

### Kiến trúc

![Sơ đồ kiến trúc CloudMenu](/images/AWS_CloudMenu.png)
