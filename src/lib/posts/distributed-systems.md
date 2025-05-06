---
title: "Hệ thống phân tán"
date: "2025-04-28"
updated: "2025-055-06"
author: "Trần Huyền Trang"
categories:
  - "sveltekit"
  - "web"
  - "css"
  - "markdown"
coverImage: "/images/DCS.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Blog này cung cấp cái nhìn tổng quan về hệ thống phân tán, bao gồm định nghĩa, ứng dụng thực tế, các khái niệm và thuật ngữ quan trọng, ví dụ minh họa dễ hiểu, cùng các mô hình kiến trúc phổ biến như Client-Server, Microservices và Serverless.
---

# 1. Hệ thống phân tán là gì?

Hệ thống phân tán (**Distributed System**) là tập hợp nhiều máy tính độc lập phối hợp với nhau như một hệ thống duy nhất để người dùng có cảm giác đang làm việc trên một hệ thống thống nhất. Các máy tính này giao tiếp và phối hợp thông qua mạng.

# 2. Các ứng dụng của hệ thống phân tán

- Dịch vụ web (Google, Facebook, Amazon)
- Hệ thống lưu trữ dữ liệu lớn (Google Drive, Dropbox)
- Game trực tuyến
- Blockchain và tiền mã hóa
- Các hệ thống ngân hàng điện tử

# 3. Các khái niệm chính của hệ thống phân tán

## Scalability
Khả năng mở rộng hệ thống khi có nhu cầu tăng tài nguyên (CPU, RAM, lưu trữ, băng thông) hoặc số lượng người dùng.

## Fault Tolerance
Khả năng hệ thống tiếp tục hoạt động bình thường ngay cả khi một hoặc nhiều thành phần bị lỗi.

## Availability
Khả năng hệ thống luôn sẵn sàng phục vụ người dùng, với thời gian downtime tối thiểu.

## Transparency
Ẩn đi sự phức tạp của hệ thống phân tán để người dùng thấy như đang sử dụng một hệ thống duy nhất.

## Concurrency
Hệ thống có thể xử lý nhiều yêu cầu cùng lúc, tận dụng tối đa tài nguyên.

## Parallelism
Thực thi đồng thời nhiều tác vụ khác nhau nhằm tăng tốc độ xử lý.

## Openness
Hệ thống hỗ trợ tương tác qua các giao thức tiêu chuẩn và dễ dàng mở rộng hoặc tích hợp thêm thành phần mới.

## Vertical Scaling
Tăng tài nguyên (CPU, RAM) cho một máy chủ hiện tại để cải thiện hiệu suất.

## Horizontal Scaling
Thêm nhiều máy chủ mới vào hệ thống để chia tải và mở rộng khả năng xử lý.

## Load Balancer
Thành phần phân phối lưu lượng truy cập đồng đều đến các server để tối ưu hóa hiệu suất và đảm bảo độ tin cậy.

## Replication
Sao chép dữ liệu hoặc dịch vụ để tăng độ tin cậy, khả năng phục hồi và hiệu suất.

# Ví dụ minh họa

Giả sử chúng ta xây dựng một hệ thống bán hàng trực tuyến:

- **Load Balancer** phân phối lưu lượng đến nhiều server web.
- Các server **Replicate** dữ liệu đơn hàng để tránh mất mát.
- Khi nhu cầu tăng vào dịp lễ, ta dùng **Horizontal Scaling** thêm server mới.
- Nếu một server bị lỗi, hệ thống vẫn hoạt động nhờ **Fault Tolerance**.
- Người dùng không biết hệ thống phức tạp thế nào, nhờ **Transparency**.
- Các yêu cầu mua hàng được xử lý **Concurrent** và **Parallel** nhằm tăng tốc độ đáp ứng.
- Hệ thống mở, hỗ trợ thêm module thanh toán mới nhờ **Openness**.
- Nếu chỉ cần nâng cấp phần cứng server thay vì thêm mới, đó là **Vertical Scaling**.

# 4. Kiến trúc của hệ thống phân tán

## Các mô hình phổ biến

- **Client-Server Model**  
  Máy khách gửi yêu cầu, máy chủ xử lý.

- **Three-Tier Architecture**  
  Gồm tầng trình bày (Presentation), tầng xử lý nghiệp vụ (Application), và tầng dữ liệu (Data).

- **Microservices Architecture**  
  Chia hệ thống thành các dịch vụ nhỏ, độc lập, dễ triển khai và mở rộng.

- **Peer-to-Peer (P2P) Architecture**  
  Các node ngang hàng, chia sẻ tài nguyên trực tiếp cho nhau.

- **Serverless Architecture**  
  Triển khai ứng dụng không cần quản lý server, tận dụng dịch vụ cloud.

## Ví dụ minh họa

Một ứng dụng lưu trữ ảnh như Google Photos:

- Frontend web/app di động (Client)
- API Gateway (Load Balancer)
- Các service nhỏ quản lý upload, chỉnh sửa, chia sẻ ảnh (Microservices)
- Dữ liệu lưu trên cloud distributed storage (Replication)
- Serverless Functions xử lý resize ảnh khi upload.

# Hình ảnh minh họa
**Client-Server Model**
![Distributed System Architecture](/images/CSM.png)
**Three-Tier Architecture**  
![Distributed System Architecture](/images/TTA.png)
**Microservices Architecture** 
![Distributed System Architecture](/images/MA.png)
**Peer-to-Peer (P2P) Architecture** 
![Distributed System Architecture](/images/P2P.png)
**Serverless Architecture** 
![Distributed System Architecture](/images/SA.jpg)

