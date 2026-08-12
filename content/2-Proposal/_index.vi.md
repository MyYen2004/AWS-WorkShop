---
title: "Bản đề xuất"
date: 2026-03-10
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Đề xuất triển khai CloudMenu trên AWS

## 1. Tổng quan dự án

CloudMenu là một hệ thống gọi món trực tuyến tại bàn, được xây dựng nhằm hỗ trợ khách hàng đặt món nhanh chóng và thuận tiện thông qua mã QR riêng của từng bàn.

Hệ thống cho phép khách hàng sử dụng điện thoại quét mã QR tại bàn để mở thực đơn, tự động xác định số bàn, xem và tìm kiếm món ăn, lọc món theo danh mục, thêm món vào giỏ hàng và gửi đơn gọi món. Sau khi đơn được gửi, khách hàng có thể theo dõi trạng thái đơn hàng từ PENDING đến PREPARING và COMPLETED, đồng thời xem thời gian đặt món, thời gian chờ và thời gian dự kiến chuẩn bị.

Đối với nhân viên bếp, hệ thống cung cấp giao diện riêng để xem danh sách đơn hàng, thông tin món ăn, số bàn và tổng tiền, đồng thời cập nhật trạng thái chế biến và ghi nhận thời gian hoàn thành đơn.

Bên cạnh đó, hệ thống cung cấp Dashboard thống kê dành cho Admin/Manager, hỗ trợ theo dõi tổng số đơn hàng, tổng doanh thu, số đơn theo từng trạng thái, doanh thu theo bàn, các món được gọi nhiều nhất và tổng số món đã được gọi.

CloudMenu được triển khai theo kiến trúc Serverless trên Amazon Web Services (AWS). Phần frontend sử dụng HTML, CSS và JavaScript, được lưu trữ trên Amazon S3 và phân phối thông qua Amazon CloudFront. Các yêu cầu từ frontend được xử lý thông qua Amazon API Gateway và AWS Lambda, trong khi dữ liệu đơn hàng được lưu trữ và quản lý bằng Amazon DynamoDB. AWS IAM được sử dụng để quản lý quyền truy cập và bảo mật các tài nguyên AWS.

Kiến trúc này giúp hệ thống giảm sự phụ thuộc vào máy chủ truyền thống, đồng thời tận dụng các dịch vụ managed và serverless của AWS để triển khai một hệ thống gọi món trực tuyến linh hoạt và dễ mở rộng.

## 2. Vấn đề và giải pháp

### Vấn đề hiện tại

Đối với hệ thống gọi món trực tuyến tại bàn, việc xử lý đơn hàng nhanh chóng, đảm bảo dữ liệu chính xác và cho phép khách hàng theo dõi trạng thái đơn hàng là những yếu tố quan trọng. Nếu hệ thống được triển khai theo mô hình máy chủ truyền thống hoặc quản lý riêng lẻ, có thể phát sinh một số vấn đề:
- Khó đáp ứng lượng truy cập thay đổi khi có nhiều khách hàng cùng quét mã QR và gửi đơn trong cùng một thời điểm.
- Việc quản lý và lưu trữ dữ liệu đơn hàng có thể trở nên phức tạp khi số lượng đơn tăng lên.
- Quá trình cập nhật trạng thái đơn hàng giữa khách hàng và nhân viên bếp cần được xử lý chính xác để tránh sai lệch thông tin.
- Việc triển khai và phân phối frontend đến khách hàng có thể gặp hạn chế nếu không có cơ chế lưu trữ và phân phối nội dung phù hợp.
- Khó kiểm soát quyền truy cập đến các tài nguyên và dịch vụ AWS nếu không có cơ chế phân quyền rõ ràng.
- Khi hệ thống có nhiều thành phần xử lý khác nhau, việc duy trì một máy chủ riêng để vận hành toàn bộ hệ thống có thể làm tăng công việc quản lý và bảo trì.

### Giải pháp

Để giải quyết các vấn đề trên, CloudMenu được xây dựng theo kiến trúc Serverless trên AWS, tận dụng các dịch vụ managed của AWS để giảm việc quản lý máy chủ và tăng khả năng mở rộng của hệ thống:
- Frontend: Sử dụng HTML, CSS và JavaScript, được lưu trữ trên Amazon S3 và phân phối đến khách hàng thông qua Amazon CloudFront.
- Backend: Sử dụng Amazon API Gateway làm API endpoint và AWS Lambda để xử lý logic nghiệp vụ, bao gồm tiếp nhận đơn hàng, truy vấn dữ liệu và cập nhật trạng thái đơn hàng.
- Database: Sử dụng Amazon DynamoDB để lưu trữ dữ liệu đơn hàng theo mô hình NoSQL, bao gồm mã đơn hàng, số bàn, trạng thái, danh sách món, tổng tiền và thời gian xử lý.
- Quản lý quyền truy cập và bảo mật: Sử dụng AWS IAM để quản lý quyền truy cập đến các tài nguyên AWS, đảm bảo các dịch vụ chỉ được cấp những quyền cần thiết.
- Luồng xử lý: Khi khách hàng, nhân viên bếp hoặc Admin/Manager thực hiện thao tác trên giao diện, frontend gửi request đến Amazon API Gateway. API Gateway chuyển request đến AWS Lambda, Lambda xử lý nghiệp vụ và đọc/ghi dữ liệu trên Amazon DynamoDB, sau đó trả kết quả về frontend.

Nhờ kiến trúc này, CloudMenu có thể tận dụng khả năng mở rộng và các dịch vụ được quản lý của AWS để xây dựng hệ thống gọi món trực tuyến linh hoạt, giảm công việc quản trị máy chủ và phù hợp với mô hình ứng dụng cloud-native.


## 3. Kiến trúc giải pháp

Kiến trúc đề xuất bám sát mô hình ứng dụng trên môi trường cloud:
![CloudMenu AWS architecture](/images/AWS_CloudMenu.png)

**Các dịch vụ AWS**

| Dịch vụ | Vai trò trong CloudMenu |
| :--- | :--- |
| **Amazon S3** | Lưu trữ các file frontend của CloudMenu như HTML, CSS, JavaScript và các tài nguyên tĩnh của hệ thống. Frontend được upload lên S3 để phục vụ việc triển khai ứng dụng. |
| **Amazon CloudFront** | Phân phối frontend từ Amazon S3 đến người dùng thông qua mạng CDN, giúp khách hàng, nhân viên bếp và Manager truy cập các giao diện CloudMenu thông qua đường dẫn CloudFront. |
| **Amazon API Gateway** | Cung cấp các API endpoint để frontend giao tiếp với backend. Tiếp nhận các request tạo đơn hàng, lấy danh sách đơn hàng và cập nhật trạng thái đơn hàng. Dữ liệu đơn hàng trả về có thể được sử dụng để hiển thị và tổng hợp thông tin trên Dashboard. |
| **AWS Lambda** | Xử lý logic nghiệp vụ của hệ thống theo mô hình serverless. Lambda tiếp nhận request từ API Gateway, xử lý dữ liệu và thực hiện các thao tác đọc/ghi với DynamoDB. |
| **Amazon DynamoDB** | Cơ sở dữ liệu NoSQL chính của CloudMenu. Table CloudMenuOrders lưu thông tin đơn hàng như orderId, tableNumber, status, items, totalAmount, createdAt, updatedAt và completedAt. |
| **AWS Identity and Access Management (IAM)** | Quản lý quyền truy cập giữa các tài nguyên AWS. IAM Role được sử dụng để cấp quyền cho các hàm AWS Lambda thực hiện các thao tác cần thiết với bảng Amazon DynamoDB. |

## 4. Timeline (8 tuần)

- **Tuần 1–2 — Phân tích yêu cầu & xây dựng Frontend**
  - **Tuần 1:** Phân tích yêu cầu và xác định các chức năng chính của hệ thống CloudMenu. Thiết kế luồng gọi món từ việc quét QR, xác định số bàn, xem menu, chọn món, thêm vào giỏ hàng và gửi đơn. Xác định các vai trò Customer, Kitchen và Manager cùng các chức năng tương ứng.
  - **Tuần 2:** Xây dựng và hoàn thiện các giao diện frontend bằng HTML, CSS và JavaScript, bao gồm trang khách hàng, trang trạng thái đơn hàng, trang bếp và Dashboard quản lý. Chuẩn bị các file frontend để triển khai lên Amazon S3.

- **Tuần 3–4 — Triển khai Frontend & xây dựng Backend Serverless**
  - **Tuần 3:** Triển khai frontend lên Amazon S3 và cấu hình Amazon CloudFront để phân phối nội dung. Kiểm tra khả năng truy cập các giao diện CloudMenu thông qua CloudFront và hoàn thiện cấu hình cần thiết cho frontend.
  - **Tuần 4:** Xây dựng Backend theo kiến trúc Serverless với Amazon API Gateway và AWS Lambda. Triển khai các API chính như Create Order, Get Orders và Update Order Status, đồng thời kiểm tra luồng request giữa frontend, API Gateway và Lambda.

- **Tuần 5–6 — Tích hợp DynamoDB & hoàn thiện nghiệp vụ**
  - **Tuần 5:** Thiết kế mô hình dữ liệu NoSQL và xây dựng table CloudMenuOrders trên Amazon DynamoDB. Tích hợp Lambda với DynamoDB để thực hiện các thao tác tạo, đọc và cập nhật đơn hàng. Hoàn thiện các trạng thái PENDING → PREPARING → COMPLETED.
  - **Tuần 6:** Hoàn thiện các chức năng của hệ thống cho Customer, Kitchen và Manager. Tích hợp giao diện bếp với API để tiếp nhận và cập nhật trạng thái đơn hàng, đồng thời xây dựng Dashboard thống kê tổng số đơn, doanh thu, trạng thái đơn, doanh thu theo bàn và các món được gọi nhiều nhất.

- **Tuần 7–8 — Bảo mật, kiểm thử & hoàn thiện hệ thống**
  - **Tuần 7:** Cấu hình AWS IAM để quản lý quyền truy cập giữa các dịch vụ AWS, đặc biệt là quyền của Lambda khi truy cập DynamoDB. Kiểm thử toàn bộ luồng hệ thống từ khách hàng gửi đơn, bếp xử lý đơn đến khách hàng theo dõi trạng thái. Kiểm tra API, dữ liệu và các trường hợp lỗi.
  - **Tuần 8:** Hoàn thiện và kiểm tra hệ thống CloudMenu trên môi trường AWS. Rà soát kiến trúc, luồng xử lý và cấu hình các dịch vụ S3, CloudFront, API Gateway, Lambda, DynamoDB và IAM. Hoàn thiện tài liệu kỹ thuật, sơ đồ kiến trúc, Workflow Diagram, Use Case Diagram, Data Model Diagram và Deployment/Request Flow Diagram, đồng thời tổng kết kết quả thực tập.
  
## 5. Ngân sách

Chi phí dưới đây là mức ước tính tham khảo cho 1 tháng (USD) đối với kiến trúc CloudMenu sử dụng các dịch vụ Serverless của AWS. Chi phí thực tế phụ thuộc vào số lượng request, dung lượng dữ liệu lưu trữ, lượng dữ liệu truyền tải và thời gian thực thi Lambda.

| Dịch vụ AWS | Thành phần / Sử dụng | Chi phí (USD/tháng) |
|---|---|---:|
| Amazon S3 | Lưu trữ frontend và các tài nguyên tĩnh | $0 - $2 |
| Amazon CloudFront | Phân phối frontend và dữ liệu đến người dùng | $0 - $10 |
| Amazon API Gateway | API endpoint và xử lý các request từ frontend | $0 - $5 |
| AWS Lambda | Xử lý logic nghiệp vụ và các API của CloudMenu | $0 - $5 |
| Amazon DynamoDB | Lưu trữ dữ liệu đơn hàng và truy vấn dữ liệu | 0 - $5 |
| AWS IAM | Quản lý quyền truy cập đến các tài nguyên AWS | Không tính phí trực tiếp |
| **TỔNG CHI PHÍ AWS** |  | **$0 - $27** |

Lưu ý: Đây chỉ là mức ước tính tham khảo cho môi trường phát triển hoặc hệ thống có lưu lượng nhỏ. Các dịch vụ Serverless của AWS chủ yếu tính phí dựa trên mức sử dụng, vì vậy chi phí thực tế có thể thấp hơn hoặc cao hơn tùy vào lượng người dùng và số lượng request của hệ thống.

Đề xuất kiểm soát chi phí:
- Sử dụng Amazon S3 để lưu trữ frontend thay vì duy trì máy chủ riêng cho việc phục vụ các file tĩnh.
- Tận dụng Amazon CloudFront để phân phối nội dung và giảm số lượng request trực tiếp đến S3.
- Theo dõi số lượng request và mức sử dụng của Amazon API Gateway và AWS Lambda để phát hiện các request bất thường.
- Tối ưu code Lambda, hạn chế thời gian thực thi không cần thiết và tránh gọi Lambda nhiều lần cho cùng một thao tác.
- Thiết kế dữ liệu và access pattern phù hợp với Amazon DynamoDB để hạn chế các thao tác đọc/ghi không cần thiết.
- Thường xuyên kiểm tra chi phí AWS và mức sử dụng tài nguyên trong quá trình phát triển và vận hành hệ thống.

## 6. Rủi ro

Trong quá trình triển khai và vận hành CloudMenu trên AWS, hệ thống có thể gặp một số rủi ro liên quan đến hiệu năng, dữ liệu, quyền truy cập và cấu hình dịch vụ.

- **Rủi ro chi phí tăng khi số lượng request tăng:** Khi số lượng khách hàng truy cập, gửi đơn và theo dõi trạng thái tăng lên, số lượng request đến API Gateway, Lambda và DynamoDB cũng tăng theo  
  *Giảm thiểu*: Theo dõi mức sử dụng và chi phí AWS định kỳ, tối ưu API và các thao tác đọc/ghi dữ liệu không cần thiết.

- **Rủi ro lỗi khi khách hàng gửi nhiều đơn cùng thời điểm:** Trong thời gian cao điểm, nhiều khách hàng có thể cùng quét QR và gửi đơn, dẫn đến số lượng request tăng đột biến.  
  *Giảm thiểu*: Sử dụng kiến trúc Serverless với API Gateway, Lambda và DynamoDB để có khả năng xử lý lượng request thay đổi, đồng thời kiểm thử hệ thống với nhiều request đồng thời.

- **Rủi ro sai lệch trạng thái đơn hàng:** Đơn hàng phải được cập nhật đúng theo luồng PENDING → PREPARING → COMPLETED. Nếu xử lý không chính xác, trạng thái hiển thị cho khách hàng và nhân viên bếp có thể không đồng nhất.  
  *Giảm thiểu*: Kiểm tra trạng thái hợp lệ trước khi cập nhật DynamoDB và kiểm thử các trường hợp cập nhật đơn hàng từ giao diện bếp.

- **Rủi ro mất hoặc sai dữ liệu đơn hàng:**Dữ liệu đơn hàng như số bàn, danh sách món, tổng tiền và trạng thái là dữ liệu quan trọng của hệ thống. Các lỗi trong quá trình ghi hoặc cập nhật DynamoDB có thể làm ảnh hưởng đến thông tin đơn hàng.  
  *Giảm thiểu*: Kiểm tra dữ liệu đầu vào, thiết kế cấu trúc DynamoDB phù hợp và xử lý lỗi trong Lambda trước khi trả response cho frontend.

- **Rủi ro phân quyền AWS không phù hợp:** Nếu Lambda hoặc các tài nguyên AWS được cấp quyền quá rộng, có thể làm tăng nguy cơ truy cập trái phép hoặc ảnh hưởng đến các tài nguyên khác.  
  *Giảm thiểu*: Sử dụng AWS IAM theo nguyên tắc Least Privilege, chỉ cấp cho Lambda các quyền cần thiết để truy cập DynamoDB và các tài nguyên liên quan.

- **Rủi ro lỗi API hoặc Lambda:** Lỗi trong API Gateway hoặc Lambda có thể khiến khách hàng không thể gửi đơn, nhân viên bếp không thể cập nhật trạng thái hoặc Manager không thể xem Dashboard. 
  *Giảm thiểu*: Kiểm thử các API chính như Create Order, Get Orders và Update Order Status, đồng thời kiểm tra log của Lambda để xác định và xử lý lỗi.

- **Rủi ro frontend không truy cập được:** Lỗi cấu hình hoặc triển khai Amazon S3/CloudFront có thể khiến khách hàng, nhân viên bếp hoặc Manager không thể truy cập giao diện CloudMenu.
  *Giảm thiểu*: Kiểm tra quá trình upload frontend lên S3, cấu hình CloudFront và kiểm thử truy cập từ trình duyệt trước khi sử dụng hệ thống.

- **Rủi ro CORS khi frontend gọi API:** Nếu API Gateway chưa cho phép origin của frontend, các request từ giao diện CloudMenu có thể bị trình duyệt chặn.
  *Giảm thiểu*:Cấu hình CORS trên API Gateway phù hợp với domain sử dụng CloudFront và kiểm tra request từ môi trường triển khai thực tế.

