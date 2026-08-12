---
title : "IAM & Security"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.2.4 </b> "
---

## 5.2.4 IAM & Security

CloudMenu sử dụng AWS Identity and Access Management (IAM) để quản lý quyền truy cập giữa các AWS services và kiểm soát những hành động mà từng thành phần trong hệ thống được phép thực hiện.

- AWS IAM

IAM được sử dụng để quản lý quyền truy cập vào các tài nguyên AWS của CloudMenu. Trong hệ thống, IAM Role được cấp cho AWS Lambda để Lambda có thể thực hiện các thao tác cần thiết với Amazon DynamoDB.

- IAM Role

AWS Lambda sử dụng IAM Role để xác định các quyền mà function được phép thực hiện.

IAM Role của Lambda được cấu hình để cho phép:

    - Đọc dữ liệu từ Amazon DynamoDB.
    - Tạo dữ liệu đơn hàng trong Amazon DynamoDB.
    - Cập nhật dữ liệu đơn hàng trong Amazon DynamoDB.
    - Ghi log hoạt động của Lambda vào Amazon CloudWatch.

- Least Privilege

CloudMenu áp dụng nguyên tắc Least Privilege, theo đó mỗi Lambda function chỉ được cấp những quyền cần thiết cho nghiệp vụ của mình.

Việc giới hạn quyền giúp giảm nguy cơ một function có thể truy cập hoặc thay đổi các tài nguyên AWS không cần thiết.

- Security Flow

Quyền truy cập giữa các thành phần được kiểm soát thông qua IAM:

Amazon API Gateway → AWS Lambda → IAM Role → Amazon DynamoDB

Lambda sử dụng IAM Role để xác thực và thực hiện các thao tác được cấp quyền trên DynamoDB.

- Security Considerations

Một số nguyên tắc bảo mật được áp dụng cho CloudMenu:

    - Không lưu AWS credentials trực tiếp trong source code.
    - Sử dụng IAM Role thay vì lưu access key cho Lambda.
    - Chỉ cấp các quyền cần thiết cho Lambda.
    - Giới hạn quyền truy cập vào table CloudMenuOrders.
    - Kiểm tra và rà soát IAM Policies trong quá trình vận hành hệ thống.