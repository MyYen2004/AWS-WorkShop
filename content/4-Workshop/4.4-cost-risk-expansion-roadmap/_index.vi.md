---
title : "Chi phí, rủi ro và định hướng mở rộng"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 4.4. </b> "
---

## 4.4 Chi phí, rủi ro và định hướng mở rộng

### Tối ưu chi phí
- Theo dõi chi phí theo các dịch vụ chính: Amazon S3, Amazon CloudFront, Amazon API Gateway, AWS Lambda và Amazon DynamoDB.
- Ưu tiên sử dụng các cấu hình phù hợp với môi trường phát triển và hệ thống có lưu lượng nhỏ:
  - Tận dụng Amazon S3 để lưu trữ frontend thay vì duy trì máy chủ riêng.
  - Sử dụng Amazon CloudFront để phân phối nội dung và giảm số lượng request trực tiếp đến S3.
  - Theo dõi số lượng request và thời gian thực thi của AWS Lambda.
  - Tối ưu các thao tác đọc/ghi dữ liệu trên Amazon DynamoDB.
  - Thường xuyên kiểm tra AWS Cost và mức sử dụng tài nguyên để phát hiện các khoản chi phí bất thường.

### Rủi ro và giảm thiểu
- Rủi ro tăng chi phí khi số lượng khách hàng, đơn hàng và API request tăng.
- Rủi ro sai lệch trạng thái đơn hàng giữa Customer và Kitchen trong quá trình cập nhật PENDING → PREPARING → COMPLETED.
- Rủi ro lỗi API hoặc Lambda khiến khách hàng không thể gửi đơn hoặc nhân viên bếp không thể cập nhật trạng thái.
- Rủi ro mất hoặc sai dữ liệu đơn hàng trong quá trình đọc/ghi Amazon DynamoDB.
- Rủi ro phân quyền AWS không phù hợp nếu Lambda hoặc các tài nguyên khác được cấp quyền quá rộng.
- Rủi ro frontend không truy cập được do lỗi cấu hình Amazon S3 hoặc Amazon CloudFront.
- Hướng giảm thiểu: kiểm thử API và Lambda, kiểm tra dữ liệu đầu vào, sử dụng AWS IAM theo nguyên tắc Least Privilege, theo dõi log, kiểm tra cấu hình S3/CloudFront và thường xuyên giám sát chi phí AWS.

### Lộ trình mở rộng
- Xây dựng CI/CD pipeline để tự động hóa quá trình triển khai frontend lên Amazon S3.
- Bổ sung automated testing và smoke testing cho các API chính như Create Order, Get Orders và Update Order Status.
- Tăng cường monitoring và logging thông qua Amazon CloudWatch để theo dõi Lambda và phát hiện lỗi.
- Hoàn thiện cơ chế bảo mật và phân quyền IAM, áp dụng nguyên tắc Least Privilege cho từng dịch vụ.
- Cải thiện khả năng xử lý khi số lượng khách hàng và đơn hàng tăng.
- Xem xét mở rộng kiến trúc với các dịch vụ AWS bổ sung khi CloudMenu được triển khai ở quy mô production.
