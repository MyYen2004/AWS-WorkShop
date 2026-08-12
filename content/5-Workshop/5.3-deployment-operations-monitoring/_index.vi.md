---
title: "Triển khai và vận hành hệ thống Serverless"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## 5.3 Triển khai và vận hành hệ thống Serverless

Chương này trình bày quá trình triển khai và vận hành CloudMenu trên AWS, tập trung vào cách đưa frontend lên môi trường AWS, triển khai các thành phần backend Serverless và kết nối các dịch vụ AWS để hệ thống hoạt động hoàn chỉnh.

CloudMenu sử dụng kiến trúc Serverless với Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda, Amazon DynamoDB và AWS IAM. Frontend được quản lý trên GitHub và hiện tại được upload thủ công lên Amazon S3, sau đó Amazon CloudFront phân phối nội dung đến người dùng.

Backend được triển khai thông qua Amazon API Gateway và AWS Lambda. Lambda xử lý các nghiệp vụ chính của CloudMenu và đọc/ghi dữ liệu trong table CloudMenuOrders trên Amazon DynamoDB.

### Luồng triển khia và vận hành

Quá trình triển khai CloudMenu được chia thành các bước chính:

- Chuẩn bị source code
    - Clone hoặc tải source code CloudMenu từ GitHub.
    - Kiểm tra các file frontend HTML, CSS, JavaScript.
    - Kiểm tra cấu hình API endpoint được sử dụng bởi frontend.
- Triển khai Frontend
    - Tạo và cấu hình Amazon S3 bucket để lưu trữ frontend.
    - Upload các file HTML, CSS, JavaScript và tài nguyên tĩnh lên S3.
    - Cấu hình Amazon CloudFront sử dụng S3 làm origin.
    - Kiểm tra khả năng truy cập các giao diện Customer, Kitchen và Manager thông qua CloudFront.
- Triển khai Backend Serverless
    - Tạo và cấu hình các AWS Lambda functions.
    - Xây dựng các API nghiệp vụ chính của CloudMenu.
    - Kết nối Amazon API Gateway với các Lambda functions.
    - Kiểm tra request và response giữa frontend, API Gateway và Lambda.
- Cấu hình DynamoDB
    - Tạo table CloudMenuOrders trên Amazon DynamoDB.
    - Cấu hình orderId làm Partition Key.
    - Kiểm tra các thao tác tạo, đọc và cập nhật dữ liệu đơn hàng.
    - Kiểm tra luồng trạng thái PENDING → PREPARING → COMPLETED.
- Cấu hình IAM
    - Tạo và cấu hình IAM Role cho AWS Lambda.
    - Cấp các quyền cần thiết để Lambda truy cập DynamoDB.
    - Áp dụng nguyên tắc Least Privilege.
    - Kiểm tra quyền truy cập trước khi đưa hệ thống vào vận hành.
- Kiểm thử và vận hành
    - Kiểm tra frontend thông qua CloudFront.
    - Kiểm tra các API chính: Create Order, Get Orders và Update Order Status.
    - Kiểm tra luồng đặt món từ Customer đến Kitchen.
    - Kiểm tra Dashboard của Manager.
    - Kiểm tra log của Lambda và các lỗi phát sinh trong quá trình xử lý.

### Kiến trúc triển khai 

CloudMenu được triển khai theo hai luồng chính:

- Frontend Deployment Flow

Developer → GitHub → Deploy/Upload → Amazon S3 → Amazon CloudFront → Browser/Phone

Hiện tại, source code được quản lý trên GitHub và frontend được upload thủ công lên Amazon S3. Chưa triển khai CI/CD tự động từ GitHub đến S3.

- Backend Request Flow

Browser/Phone → Amazon API Gateway → AWS Lambda → Amazon DynamoDB

Frontend gửi request đến API Gateway. API Gateway chuyển request đến Lambda tương ứng. Lambda xử lý nghiệp vụ và thực hiện các thao tác đọc/ghi dữ liệu trên DynamoDB, sau đó trả kết quả về frontend thông qua API Gateway.

### Vì sao sử dụng kiến trúc Serverless

Kiến trúc Serverless giúp CloudMenu giảm nhu cầu quản lý máy chủ Backend truyền thống. Amazon API Gateway và AWS Lambda đảm nhiệm việc tiếp nhận và xử lý request, trong khi Amazon DynamoDB cung cấp lớp lưu trữ dữ liệu được quản lý bởi AWS.

Frontend được lưu trữ trên Amazon S3 và phân phối thông qua CloudFront, giúp tách biệt việc phục vụ giao diện khỏi quá trình xử lý Backend.

### Nội dung

1. [4.3.1 Triển khai Frontend với Amazon S3 và Amazon CloudFront](4.3.1-run-infrastructure-terraform/)
2. [4.3.2 Triển khai Backend Serverless với API Gateway và AWS Lambda](4.3.2-frontend-hosting/)
3. [4.3.3 Tích hợp DynamoDB và kiểm thử hệ thống](4.3.3-backend/)
