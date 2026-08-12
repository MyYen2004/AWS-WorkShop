---
title: "Nhật ký Tuần 7"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7

- Hoàn thiện cơ chế phân quyền bằng AWS IAM.
- Cấu hình IAM Role cho Lambda để truy cập Amazon DynamoDB.
- Áp dụng nguyên tắc Least Privilege cho các quyền của Lambda.
- Kiểm tra và xử lý các lỗi phát sinh trong quá trình API và Lambda thực thi.
- Kiểm thử CORS, API response và các trường hợp lỗi của hệ thống.
- Rà soát cấu hình bảo mật của các dịch vụ AWS đang sử dụng.


**Thời gian:** 03/08/2026 - 07/08/2026

---

### Tổng quan Nhiệm vụ Tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                     | Ngày bắt đầu | Ngày kết thúc | Tài liệu tham khảo                 |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------- | ---------------------------------- |
| 1    | - Rà soát và hoàn thiện cơ chế phân quyền bằng AWS IAM. <br> - Kiểm tra các IAM Role và Policy đang được sử dụng trong CloudMenu.                                        | 03/08/2026   | 03/08/2026    | -                   |
| 2    | - Cấu hình IAM Role cho AWS Lambda. <br> - Cấp quyền cần thiết để Lambda truy cập Amazon DynamoDB.  <br> - Áp dụng nguyên tắc Least Privilege.                      | 04/08/2026   | 04/08/2026    | -                   |
| 3    | - Theo dõi Lambda logs và kiểm tra các hoạt động trong quá trình thực thi. <br> - Xác định và xử lý các lỗi phát sinh.                         | 05/08/2026   | 05/08/2026    | -                   |
| 4    | - Kiểm thử CORS và API response. <br> - Kiểm tra các trường hợp request lỗi và khả năng xử lý lỗi của Lambda.<br> - Kiểm tra hoạt động giữa Frontend → API Gateway → Lambda → DynamoDB. | 06/08/2026   | 06/08/2026    | -                   |
| 5    | - Rà soát cấu hình bảo mật của các dịch vụ AWS đang sử dụng. <br> - Kiểm tra quyền truy cập, IAM Policy và Lambda Role.  <br> - Hoàn thiện các cấu hình bảo mật và xử lý các vấn đề phát hiện trong quá trình kiểm thử.                                    | 07/08/2026   | 07/08/2026    | -  |

---

### Thành tựu Tuần 7

- Hoàn thiện cơ chế phân quyền cho CloudMenu bằng AWS IAM.
- Cấu hình IAM Role cho AWS Lambda để truy cập Amazon DynamoDB.
- Áp dụng nguyên tắc Least Privilege nhằm giới hạn các quyền không cần thiết.
- Kiểm tra và xử lý các lỗi phát sinh trong quá trình thực thi API và Lambda.
- Kiểm thử CORS, API response và các trường hợp lỗi của hệ thống.
- Rà soát và cải thiện cấu hình bảo mật của các dịch vụ AWS được sử dụng trong CloudMenu.