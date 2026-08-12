---
title: "Nhật ký công việc"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

**Tuần 1 (22/06 - 26/06):** [Làm quen với AWS và các dịch vụ cơ bản](1.1-week1/)

- Tìm hiểu nền tảng AWS Cloud và các nhóm dịch vụ chính như Compute, Storage, Database và Networking.
- Làm quen với AWS Management Console và AWS CLI.
- Thực hành các thao tác cơ bản trên AWS và tìm hiểu mô hình triển khai ứng dụng trên Cloud.
- Tìm hiểu các khái niệm cơ bản về Serverless Architecture và các dịch vụ AWS phù hợp với CloudMenu.

**Tuần 2 (29/06 - 03/07):** [AWS IAM, S3 và kiến trúc CloudMenu](1.2-week2/)

- Tìm hiểu và thực hành AWS IAM để quản lý quyền truy cập tài nguyên AWS.
- Nghiên cứu Amazon S3 và cách sử dụng S3 để lưu trữ các file frontend.
- Tìm hiểu Amazon CloudFront và mô hình phân phối nội dung thông qua CDN.
- Phân tích yêu cầu và xác định các thành phần chính của hệ thống CloudMenu.
- Xác định các nhóm người dùng Customer, Kitchen và Manager cùng các chức năng tương ứng.

**Tuần 3 (06/07 - 10/07):** [Xây dựng Frontend và triển khai trên AWS](1.3-week3/)

- Xây dựng và hoàn thiện các giao diện CloudMenu bằng HTML, CSS và JavaScript.
- Phát triển giao diện Customer, Order Status, Kitchen và Manager Dashboard.
- Xây dựng luồng gọi món từ quét QR → xác định bàn → xem menu → chọn món → gửi đơn.
- Upload frontend lên Amazon S3.
- Cấu hình Amazon CloudFront để phân phối frontend đến người dùng.
- Kiểm tra khả năng truy cập CloudMenu thông qua CloudFront.

**Tuần 4 (13/07 - 17/07):** [API Gateway và AWS Lambda](1.4-week4/)

- Tìm hiểu kiến trúc Serverless Backend trên AWS.
- Xây dựng các AWS Lambda functions xử lý logic nghiệp vụ của CloudMenu.
- Sử dụng Amazon API Gateway để tạo các API endpoint.
- Triển khai các API chính:
    - Create Order
    - Get Orders
    - Update Order Status
- Kiểm thử luồng request Frontend → API Gateway → Lambda.
- Cấu hình CORS để frontend có thể giao tiếp với API.

**Tuần 5 (20/07 - 24/07):** [Amazon DynamoDB và quản lý dữ liệu đơn hànge](1.5-week5/)

- Tìm hiểu cơ sở dữ liệu NoSQL với Amazon DynamoDB.
- Thiết kế mô hình dữ liệu cho hệ thống CloudMenu.
- Tạo table CloudMenuOrders và cấu hình orderId làm Partition Key.
- Tích hợp AWS Lambda với DynamoDB để thực hiện các thao tác tạo, đọc và cập nhật đơn hàng.
- Xây dựng và kiểm thử luồng trạng thái:
PENDING → PREPARING → COMPLETED.
- Kiểm tra tính chính xác của dữ liệu đơn hàng trong DynamoDB.

**Tuần 6 (27/07 - 31/07):** [Hoàn thiện nghiệp vụ và tích hợp hệ thống](1.6-week6/)

- Hoàn thiện các chức năng dành cho Customer, Kitchen và Manager.
- Tích hợp giao diện Customer với API để gửi và theo dõi đơn hàng.
- Tích hợp giao diện Kitchen để xem và cập nhật trạng thái đơn hàng.
- Hoàn thiện Manager Dashboard với các thông tin thống kê.
- Kiểm tra dữ liệu tổng số đơn, doanh thu, trạng thái đơn, doanh thu theo bàn và món được gọi nhiều nhất.
- Kiểm thử luồng xử lý end-to-end từ Customer → Kitchen → Manager.

**Tuần 7 (03/08 - 07/08):** [Bảo mật, IAM và Monitoring](1.7-week7/)

- Hoàn thiện cơ chế phân quyền bằng AWS IAM.
- Cấu hình IAM Role cho Lambda để truy cập Amazon DynamoDB.
- Áp dụng nguyên tắc Least Privilege cho các quyền của Lambda.
- Kiểm tra và xử lý các lỗi phát sinh trong quá trình API và Lambda thực thi.
- Kiểm thử CORS, API response và các trường hợp lỗi của hệ thống.
- Rà soát cấu hình bảo mật của các dịch vụ AWS đang sử dụng.

**Tuần 8 (10/08 - 14/08):** [Kiểm thử, tối ưu và hoàn thiện CloudMenu](1.8-week8/)

- Kiểm thử toàn bộ hệ thống CloudMenu trên môi trường AWS.
- Kiểm tra các luồng chính:
Customer → Order → Kitchen → Completed → Manager Dashboard.
- Kiểm tra hoạt động của S3, CloudFront, API Gateway, Lambda, DynamoDB, IAM.
- Theo dõi và tối ưu chi phí AWS đối với hệ thống có lưu lượng nhỏ.
- Rà soát kiến trúc Serverless và khả năng mở rộng của CloudMenu.
- Hoàn thiện Architecture Diagram, Order Workflow Diagram, Use Case Diagram, Data Model Diagram và Deployment/Request Flow Diagram.
- Hoàn thiện Proposal gồm Architecture, Implementation Plan, Cost, Risk và Expansion Roadmap.
- Hoàn thiện tài liệu kỹ thuật và tổng kết kết quả thực tập.