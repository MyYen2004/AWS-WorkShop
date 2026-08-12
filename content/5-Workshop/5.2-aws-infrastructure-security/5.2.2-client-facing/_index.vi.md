---
title : "API Gateway & Serverless Backend"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2.2 </b> "
---

## 5.2.2 API Gateway & Serverless Backend

CloudMenu sử dụng Amazon API Gateway và AWS Lambda để xây dựng Backend theo kiến trúc Serverless. API Gateway đóng vai trò là API endpoint tiếp nhận các request từ frontend, trong khi Lambda xử lý logic nghiệp vụ của hệ thống.

- Amazon API Gateway

Amazon API Gateway cung cấp các API endpoint để frontend giao tiếp với Backend. Các request chính của CloudMenu bao gồm:

    - Create Order — tạo đơn hàng mới.
    - Get Orders — lấy thông tin hoặc danh sách đơn hàng.
    - Update Order Status — cập nhật trạng thái đơn hàng.

API Gateway tiếp nhận request từ các giao diện Customer, Kitchen và Manager, sau đó chuyển request đến AWS Lambda tương ứng.

- AWS Lambda

AWS Lambda thực hiện các logic nghiệp vụ của CloudMenu mà không cần duy trì máy chủ riêng.

Lambda xử lý các yêu cầu như:

    - Tiếp nhận và xử lý đơn hàng từ Customer.
    - Truy vấn đơn hàng cho Kitchen.
    - Cập nhật trạng thái đơn hàng.
    - Cung cấp dữ liệu cho Dashboard Manager.

Lambda thực hiện việc đọc và ghi dữ liệu với Amazon DynamoDB. Phần mô hình dữ liệu và cách lưu trữ đơn hàng được trình bày chi tiết trong 4.2.3 DynamoDB & Data Model.

- Request Flow

Luồng xử lý request chính của CloudMenu:

Frontend / Browser → Amazon API Gateway → AWS Lambda → Amazon DynamoDB

Sau khi Lambda hoàn thành xử lý, kết quả được trả ngược về frontend thông qua API Gateway.

- CORS

API Gateway được cấu hình CORS để cho phép frontend được phân phối thông qua CloudFront gửi request đến các API của CloudMenu.

- Serverless Architecture

Việc sử dụng API Gateway và Lambda giúp CloudMenu không cần quản lý máy chủ Backend truyền thống. AWS tự quản lý việc cung cấp và thực thi Lambda theo request, phù hợp với hệ thống có lượng truy cập thay đổi theo thời điểm.