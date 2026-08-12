---
title: "Nhật ký Tuần 6"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6


- Hoàn thiện các chức năng dành cho Customer, Kitchen và Manager.
- Tích hợp giao diện Customer với API để gửi và theo dõi đơn hàng.
- Tích hợp giao diện Kitchen để xem và cập nhật trạng thái đơn hàng.
- Hoàn thiện Manager Dashboard với các thông tin thống kê.
- Kiểm tra dữ liệu tổng số đơn, doanh thu, trạng thái đơn, doanh thu theo bàn và món được gọi nhiều nhất.
- Kiểm thử luồng xử lý end-to-end từ Customer → Kitchen → Manager.


**Thời gian:** 27/07/2026 - 31/07/2026

---

### Tổng quan Nhiệm vụ Tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                        | Ngày bắt đầu | Ngày kết thúc | Tài liệu tham khảo                     |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | ------------- | -------------------------------------- |
| 1    | - Hoàn thiện các chức năng dành cho Customer. <br> - Tích hợp giao diện Customer với API để gửi đơn và theo dõi trạng thái đơn hàng. <br> - Kiểm tra luồng đặt món từ Customer.                      | 27/07/2026   | 27/07/2026    | <https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway.html?utm_source=chatgpt.com>    |
| 2    | - Hoàn thiện các chức năng dành cho Kitchen. <br> - Tích hợp API để lấy danh sách đơn hàng. <br> - Xây dựng chức năng cập nhật trạng thái đơn hàng từ PENDING → PREPARING → COMPLETED.                                                     | 28/07/2026   | 28/07/2026    | -   |
| 3    | - Hoàn thiện Manager Dashboard. <br> - Hiển thị các thông tin thống kê: tổng số đơn hàng, doanh thu, trạng thái đơn, doanh thu theo bàn và món được gọi nhiều nhất. <br> - Kiểm tra tính chính xác của dữ liệu thống kê. | 29/07/2026   | 29/09/2026    | -                                      |
| 4    | - Kiểm thử toàn bộ hệ thống theo luồng Customer → Kitchen → Manager. <br> - Kiểm tra sự đồng bộ trạng thái và dữ liệu đơn hàng giữa các giao diện. <br> -	Xử lý lỗi và hoàn thiện các chức năng chính của CloudMenu.                                | 30/07/2026   | 30/07/2026    | - |


---

### Thành tựu Tuần 6

- Hoàn thiện các chức năng chính dành cho Customer, Kitchen và Manager.
- Tích hợp giao diện Customer với API để gửi đơn và theo dõi trạng thái đơn hàng.
- Tích hợp giao diện Kitchen để xem và cập nhật trạng thái đơn hàng.
- Hoàn thiện Manager Dashboard và các chức năng thống kê.
- Hiển thị được các thông tin như tổng số đơn hàng, doanh thu, trạng thái đơn hàng, doanh thu theo bàn và các món được gọi nhiều nhất.
- Kiểm thử thành công luồng xử lý Customer → Order → Kitchen → Completed → Manager Dashboard.


