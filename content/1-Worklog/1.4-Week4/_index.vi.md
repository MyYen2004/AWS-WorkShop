---
title: "Nhật ký Tuần 4"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4

- Tìm hiểu kiến trúc Serverless Backend trên AWS.
- Xây dựng các AWS Lambda functions xử lý logic nghiệp vụ của CloudMenu.
- Sử dụng Amazon API Gateway để tạo các API endpoint.
- Triển khai các API chính:
    - Create Order
    - Get Orders
    - Update Order Status
- Kiểm thử luồng request Frontend → API Gateway → Lambda.
- Cấu hình CORS để frontend có thể giao tiếp với API.


**Thời gian:** 30/03/2026 - 03/04/2026

---

### Tổng quan Nhiệm vụ Tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                | Ngày bắt đầu | Ngày kết thúc | Tài liệu tham khảo                            |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------- | --------------------------------------------- |
| 1    | - Tìm hiểu kiến trúc Serverless Backend trên AWS. <br> - Nghiên cứu cách AWS Lambda và Amazon API Gateway phối hợp trong xử lý request.            | 30/03/2026   | 30/03/2026    | <https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway.html?utm_source=chatgpt.com>           |
| 2    | - Xây dựng và cấu hình các AWS Lambda functions cho CloudMenu. <br> - Xử lý logic nghiệp vụ cho việc tạo và quản lý đơn hàng. | 31/03/2026   | 31/03/2026    | <https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html?utm_source=chatgpt.com>           |
| 3    | - Cấu hình Amazon API Gateway. <br> - Tạo các API endpoint chính: Create Order, Get Orders và Update Order Status.p <br> - Kết nối API Gateway với các Lambda functions.     | 01/04/2026   | 01/04/2026    | <https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html?utm_source=chatgpt.com>           |
| 4    | - Kiểm thử các API chính của CloudMenu. <br> - Kiểm tra luồng request Frontend → API Gateway → Lambda. <br> - Kiểm tra request và response của từng API. | 02/04/2026   | 02/04/2026    | <https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-test-method.html?utm_source=chatgpt.com>           |
| 5    | - Cấu hình CORS để frontend có thể giao tiếp với API Gateway. <br> - Kiểm tra kết nối giữa frontend và backend. <br> - Xử lý các lỗi phát sinh trong quá trình gọi API và hoàn thiện Backend Serverless. | 03/04/2026   | 03/04/2026    | <https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html?utm_source=chatgpt.com> |

---

### Thành tựu Tuần 4

- Hiểu và triển khai được Backend theo kiến trúc Serverless.
-Xây dựng các AWS Lambda functions để xử lý logic nghiệp vụ của CloudMenu.
- Cấu hình Amazon API Gateway và tạo các API endpoint chính cho hệ thống.
- Hoàn thiện các API Create Order, Get Orders và Update Order Status.
- Kiểm thử thành công luồng request Frontend → API Gateway → Lambda.
- Cấu hình CORS để frontend có thể giao tiếp với các API của CloudMenu.

