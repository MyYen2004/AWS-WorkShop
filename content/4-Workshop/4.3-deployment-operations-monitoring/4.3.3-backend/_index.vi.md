---
title: "Tích hợp DynamoDB và kiểm thử hệ thống"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3.3 </b> "
---

## 4.3.3 Tích hợp DynamoDB và kiểm thử hệ thống

Phần này trình bày quá trình tích hợp Amazon DynamoDB với Backend Serverless của CloudMenu và kiểm thử toàn bộ luồng xử lý của hệ thống.

### 1. Cấu hình Amazon DynamoDB

CloudMenu sử dụng Amazon DynamoDB để lưu trữ dữ liệu đơn hàng. Tạo table CloudMenuOrders và sử dụng orderId làm Partition Key.

Các thuộc tính chính của đơn hàng bao gồm:

- orderId — mã đơn hàng.
- tableNumber — số bàn.
- status — trạng thái đơn hàng.
- items — danh sách món ăn.
- totalAmount — tổng tiền.
- createdAt — thời gian tạo đơn.
- updatedAt — thời gian cập nhật.
- completedAt — thời gian hoàn thành.

### 2. Tích hợp Lambda với DynamoDB

AWS Lambda được kết nối với Amazon DynamoDB để thực hiện các thao tác đọc và ghi dữ liệu.

Các nghiệp vụ chính gồm:

- Tạo đơn hàng mới.
- Lấy thông tin và danh sách đơn hàng.
- Cập nhật trạng thái đơn hàng.
- Truy xuất dữ liệu phục vụ Dashboard.

Luồng xử lý:

Amazon API Gateway → AWS Lambda → Amazon DynamoDB

### 3. Kiểm thử luồng đặt món

Kiểm thử toàn bộ quá trình từ khi Customer gửi đơn đến khi đơn hàng hoàn thành:

Quét QR → Xác định bàn → Xem menu → Chọn món → Giỏ hàng → Gửi đơn → PENDING → PREPARING → COMPLETED

Kiểm tra đảm bảo thông tin số bàn, danh sách món, tổng tiền và trạng thái đơn hàng được lưu chính xác trong DynamoDB.

### 4. Kiểm thử các giao diện

Thực hiện kiểm thử các chức năng chính của từng nhóm người dùng:

- Customer: Gửi đơn và theo dõi trạng thái đơn hàng.
- Kitchen: Xem danh sách đơn hàng và cập nhật trạng thái chế biến.
- Manager: Truy xuất dữ liệu đơn hàng và hiển thị các thông tin thống kê trên Dashboard.

Đồng thời kiểm tra sự đồng bộ trạng thái đơn hàng giữa giao diện Customer và Kitchen.

### 5. Kiểm tra và giám sát hệ thống

Sau khi hoàn thành kiểm thử, kiểm tra dữ liệu được lưu trong CloudMenuOrders, response của các API và các lỗi phát sinh trong quá trình xử lý Lambda.

Amazon CloudWatch được sử dụng để theo dõi log của Lambda và hỗ trợ xác định lỗi trong quá trình vận hành.

Luồng kiểm thử tổng thể

Customer / Kitchen / Manager → CloudFront → Frontend → API Gateway → Lambda → DynamoDB

Kết quả: Hoàn thành tích hợp Amazon DynamoDB với Backend Serverless và xác nhận các chức năng chính của CloudMenu hoạt động đúng từ frontend đến lớp dữ liệu.