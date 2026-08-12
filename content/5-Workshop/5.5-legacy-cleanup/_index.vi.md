---
title : "Dọn dẹp tài nguyên"
date : 2024-01-01
weight : 99
chapter : false
pre : " <b> 5.5. </b> "
draft : false
---

## 5.5 Dọn dẹp tài nguyên

Khi không còn cần sử dụng hệ thống CloudMenu trên AWS, cần kiểm tra và dọn dẹp các tài nguyên đã được tạo trong quá trình triển khai để tránh phát sinh chi phí không cần thiết.

CloudMenu sử dụng các dịch vụ Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda, Amazon DynamoDB và AWS IAM, do đó việc dọn dẹp cần được thực hiện theo từng dịch vụ và kiểm tra cẩn thận trước khi xóa.

### Các tài nguyên cần kiểm tra

- Amazon S3: Xóa các file frontend và các tài nguyên tĩnh nếu không còn sử dụng. Cần kiểm tra và xóa các object trong bucket trước khi xóa bucket nếu cần.
- Amazon CloudFront: Disable và xóa CloudFront distribution nếu hệ thống không còn được sử dụng.
- Amazon API Gateway: Xóa các API và stage không còn cần thiết.
- AWS Lambda: Xóa các Lambda functions được sử dụng cho CloudMenu nếu không còn nhu cầu sử dụng.
- Amazon DynamoDB: Xóa table CloudMenuOrders nếu dữ liệu đơn hàng không còn cần thiết. Cần sao lưu dữ liệu trước khi thực hiện nếu dữ liệu vẫn có giá trị.
- AWS IAM: Kiểm tra và xóa các IAM Role hoặc Policy được tạo riêng cho CloudMenu khi chúng không còn được sử dụng.

### Trước khi dọn dẹp

- Kiểm tra đúng AWS Account và AWS Region đang sử dụng để tránh xóa nhầm tài nguyên của hệ thống khác.
- Kiểm tra các tài nguyên CloudMenu đang hoạt động trên AWS Management Console.
- Xác định dữ liệu trong Amazon DynamoDB có cần được giữ lại hay không trước khi xóa table CloudMenuOrders.
- Kiểm tra Amazon S3 và đảm bảo các file frontend cần thiết đã được sao lưu nếu cần.
- Kiểm tra các IAM Role/Policy để đảm bảo chúng không được sử dụng bởi các Lambda functions hoặc tài nguyên khác.

### Sau khi dọn dẹp 

Sau khi hoàn tất, kiểm tra lại AWS Management Console để đảm bảo các tài nguyên CloudMenu không còn cần thiết đã được xóa.

Đặc biệt cần kiểm tra:

- Không còn CloudFront Distribution không sử dụng.
- Không còn API Gateway không cần thiết.
- Không còn Lambda Functions của CloudMenu.
- Không còn DynamoDB Table CloudMenuOrders nếu đã xác định không cần dữ liệu.
- Không còn S3 Bucket/Object không sử dụng.
- Không còn IAM Role/Policy được tạo riêng cho CloudMenu nhưng không còn được sử dụng.

Lưu ý: Việc xóa DynamoDB table hoặc dữ liệu đơn hàng có thể làm mất dữ liệu. Cần xác nhận và sao lưu dữ liệu trước khi thực hiện nếu dữ liệu vẫn cần được lưu trữ. đến khi xong.

