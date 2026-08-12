---
title: "Nhật ký Tuần 5"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5

- Tìm hiểu cơ sở dữ liệu NoSQL với Amazon DynamoDB.
- Thiết kế mô hình dữ liệu cho hệ thống CloudMenu.
- Tạo table CloudMenuOrders và cấu hình orderId làm Partition Key.
- Tích hợp AWS Lambda với DynamoDB để thực hiện các thao tác tạo, đọc và cập nhật đơn hàng.
- Xây dựng và kiểm thử luồng trạng thái:
PENDING → PREPARING → COMPLETED.
- Kiểm tra tính chính xác của dữ liệu đơn hàng trong DynamoDB.


**Thời gian:** 20/07/2026 - 24/07/2026

---

### Tổng quan Nhiệm vụ Tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                               | Ngày bắt đầu | Ngày kết thúc | Tài liệu tham khảo                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------- | ------------------------------------ |
| 1    | - Tìm hiểu cơ sở dữ liệu NoSQL với Amazon DynamoDB. <br> - Nghiên cứu các khái niệm Table, Item, Attribute và Partition Key.                                                          | 20/07/2026   | 20/07/2026    | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html?utm_source=chatgpt.com> |
| 2    | - Phân tích và thiết kế mô hình dữ liệu CloudMenu. <br> - Xác định các thuộc tính chính của đơn hàng và cấu hình orderId làm Partition Key.                  | 21/07/2026   | 21/07/2026    | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html?utm_source=chatgpt.com>        |
| 3    | - Tạo table CloudMenuOrders trên Amazon DynamoDB. <br> - Kiểm tra việc tạo, đọc và quản lý dữ liệu đơn hàng trong table.                                                | 22/07/2026   | 22/07/2026    | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html?utm_source=chatgpt.com>     |
| 4    | - Tích hợp AWS Lambda với Amazon DynamoDB. <br> - Thực hiện các thao tác tạo, đọc và cập nhật đơn hàng thông qua Lambda. <br> - Kiểm tra luồng API Gateway → Lambda → DynamoDB.                          | 23/07/2026   | 23/07/2026    | <https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway-tutorial.html?utm_source=chatgpt.com>  |
| 5    | - Xây dựng và kiểm thử luồng trạng thái PENDING → PREPARING → COMPLETED. <br> - Kiểm tra tính chính xác và nhất quán của dữ liệu đơn hàng trong DynamoDB. <br> -	Hoàn thiện tích hợp Backend với lớp dữ liệu. | 24/07/2026   | 24/07/2026    | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transactions.html?utm_source=chatgpt.com>  |


---

### Thành tựu Tuần 5

- Nắm được cách sử dụng Amazon DynamoDB và mô hình cơ sở dữ liệu NoSQL.
- Thiết kế và triển khai table CloudMenuOrders với orderId làm Partition Key.
- Xác định và triển khai các thuộc tính chính của dữ liệu đơn hàng.
- Tích hợp thành công AWS Lambda với Amazon DynamoDB để tạo, đọc và cập nhật dữ liệu đơn hàng.
- Hoàn thiện luồng xử lý trạng thái đơn hàng PENDING → PREPARING → COMPLETED.
- Kiểm tra và xác nhận dữ liệu đơn hàng được lưu trữ và cập nhật chính xác trong DynamoDB.

