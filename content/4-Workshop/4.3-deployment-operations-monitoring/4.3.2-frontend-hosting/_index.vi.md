---
title: "Triển khai Backend Serverless với API Gateway và AWS Lambda"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.3.2 </b> "
aliases:
  - /4-workshop/4.3-deployment-operations-monitoring/4.3.2-frontend-hosting-auth/
---

## 4.3.2 Triển khai Backend Serverless với API Gateway và AWS Lambda

Phần này trình bày quá trình triển khai Backend của CloudMenu theo kiến trúc Serverless, sử dụng Amazon API Gateway làm API endpoint và AWS Lambda để xử lý logic nghiệp vụ.

### 1. Chuẩn bị Backend

Kiểm tra source code Backend và xác định các nghiệp vụ chính của CloudMenu. Backend cần xử lý các request từ giao diện Customer, Kitchen và Manager.

Các nghiệp vụ chính gồm:

- Create Order — tạo đơn hàng mới.
- Get Orders — lấy thông tin hoặc danh sách đơn hàng.
- Update Order Status — cập nhật trạng thái đơn hàng.
### 2. Triển khai AWS Lambda

Tạo các AWS Lambda functions để xử lý logic nghiệp vụ của CloudMenu.

Lambda tiếp nhận request từ API Gateway, xử lý dữ liệu và thực hiện các thao tác đọc/ghi với Amazon DynamoDB.

Luồng xử lý:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

### 3. Cấu hình Amazon API Gateway

Tạo các API endpoint và kết nối từng endpoint với Lambda function tương ứng.

API Gateway chịu trách nhiệm:

- Tiếp nhận request từ frontend.
- Chuyển request đến Lambda.
- Nhận response từ Lambda và trả về frontend.
- Cấu hình CORS để frontend được phân phối qua CloudFront có thể gọi API.
### 4. Kiểm thử Backend

Sau khi triển khai, kiểm tra các API chính và luồng xử lý của hệ thống:

Browser/Phone → API Gateway → Lambda → DynamoDB

Kiểm tra Customer có thể gửi đơn, Kitchen có thể lấy và cập nhật đơn hàng, đồng thời Manager có thể lấy dữ liệu để hiển thị Dashboard.

### 5. Kiểm tra và vận hành

Kiểm tra response của API, lỗi Lambda và dữ liệu được ghi vào DynamoDB. Có thể sử dụng Amazon CloudWatch để theo dõi log của Lambda trong quá trình kiểm thử và vận hành.

Kết quả: Backend CloudMenu được triển khai theo mô hình Serverless, trong đó API Gateway tiếp nhận request và Lambda xử lý nghiệp vụ mà không cần duy trì máy chủ Backend riêng.