---
title: "Tiến trình & Luồng"
date: "2025-05-06"
updated: "2025-05-06"
author: "Trần Huyền Trang"
categories:
  - "Distributed Systems"
  - "Processes and Threads"
  - "Concurrency"
coverImage: "/images/PVT.png"
coverWidth: 16
coverHeight: 9
excerpt: Blog này giúp bạn hiểu rõ về tiến trình và luồng trong hệ thống phân tán, sự khác biệt giữa chúng, và cách chúng ảnh hưởng đến hiệu năng của máy tính khi xử lý các tác vụ đồng thời.
---

# 1. Dựa vào bài học, check CPU, GPU, RAM, giải thích về hiệu năng của máy tính mà em đang dùng?

Phân tích hiệu năng máy tính ASUS VivoBook 15

| Thành phần | Thông số chi tiết | Đánh giá hiệu năng |
|------------|------------------|---------------------|
| **CPU** | Intel Core i5-1135G7 (4 nhân, 8 luồng, base 2.4GHz, turbo ~4.2GHz) <br> Cache: L1: 320KB, L2: 5MB, L3: 8MB | Bộ xử lý dòng U (tiết kiệm điện), hỗ trợ đa luồng, hiệu quả cho tác vụ lập trình, xử lý song song nhẹ và học tập. Có hỗ trợ **ảo hóa**. |
| **GPU** | Intel Iris Xe Graphics <br> Driver: 30.0.101.3111 <br> DirectX 12 (FL 12.1) <br> Shared GPU memory: 3.9 GB | GPU tích hợp đủ dùng cho hiển thị đồ họa 2D, lập trình giao diện, xem video 4K. Không phù hợp cho AI training nặng hoặc game 3D phức tạp. |
| **RAM** | 8GB DDR4, bus 3200MT/s <br> Đang dùng: ~6.8GB, Còn trống: ~875MB <br> Dạng: SODIMM, Slot RAM còn trống: 1 | Đủ dùng cho lập trình web/mobile, VSCode, trình duyệt, nhẹ nhàng chạy máy ảo. Tuy nhiên, bị giới hạn khi dùng nhiều tiến trình nặng cùng lúc hoặc thử nghiệm đa luồng quy mô lớn. |

**Sử dụng hiện tại:**  
- **CPU:** 12% sử dụng  
- **GPU:** 2% sử dụng  
- **RAM:** 6.8GB/8GB đang dùng  
- **Số tiến trình:** 272  
- **Số luồng:** 3101  

### 🔎 Kết luận:

Máy đủ mạnh để:
- Viết code với VSCode, chạy các server backend nhẹ.
- Học tập về **đa tiến trình**, **đa luồng** qua thực hành.
- Dùng ảo hóa (VirtualBox, WSL2) nhờ hỗ trợ VT-x.
- Không nên dùng cho AI deep learning nặng hoặc xử lý media lớn.

# 2. Nghiên cứu tìm hiểu, liệt kê ít nhất 12 bài toán phổ biến trong ngành CNTT của em đang học, những bài toán này sử dụng đa luồng, đa tiến trình ở đâu?

Trong ngành công nghệ thông tin, có nhiều bài toán đụng phải việc xử lý đồng thời với đa tiến trình và đa luồng. Dưới đây là một số ví dụ:

**1. Xử lý ảnh (Image Processing)**  
   - **Đa Luồng**: Chia ảnh thành các phần nhỏ và xử lý song song trên từng phần ảnh bằng các luồng. Điều này giúp tiết kiệm thời gian xử lý tổng thể.
   - **Đa Tiến Trình**: Nếu dữ liệu ảnh quá lớn hoặc cần xử lý trên nhiều máy tính, có thể sử dụng đa tiến trình để xử lý các phần ảnh độc lập.

**2. Tính toán khoa học và mô phỏng (Scientific Computing)**  
   - **Đa Luồng**: Sử dụng trong các bài toán tính toán phức tạp, chia nhỏ các phần tính toán để xử lý song song trong một tiến trình.
   - **Đa Tiến Trình**: Các mô phỏng quy mô lớn, như mô phỏng vật lý, có thể yêu cầu sử dụng nhiều tiến trình trên các máy chủ khác nhau để xử lý song song các tác vụ.

**3. Máy chủ Web (Web Servers)**  
   - **Đa Luồng**: Các máy chủ như Apache, Nginx sử dụng đa luồng để xử lý các yêu cầu HTTP song song từ nhiều người dùng mà không cần tạo ra quá nhiều tiến trình.
   - **Đa Tiến Trình**: Một số máy chủ web sử dụng đa tiến trình để quản lý yêu cầu từ người dùng, nơi mỗi tiến trình chịu trách nhiệm xử lý một kết nối riêng biệt.

**4. Ứng dụng game đa người chơi (Multiplayer Games)**  
   - **Đa Luồng**: Sử dụng đa luồng để xử lý các hành động người chơi, đồng bộ hóa trạng thái game, và quản lý kết nối mạng trong cùng một tiến trình.
   - **Đa Tiến Trình**: Có thể sử dụng nhiều tiến trình cho mỗi phần của trò chơi, như một tiến trình cho giao diện người dùng và một tiến trình khác cho máy chủ game.

**5. Hệ thống tài chính (Financial Systems)**  
   - **Đa Luồng**: Xử lý các giao dịch tài chính trong cùng một tiến trình bằng cách sử dụng các luồng riêng biệt để xử lý các giao dịch song song, giúp giảm thời gian trễ.
   - **Đa Tiến Trình**: Dùng đa tiến trình khi cần xử lý một lượng lớn giao dịch từ nhiều khách hàng, mỗi tiến trình xử lý giao dịch độc lập.

**6. Học máy (Machine Learning)**  
   - **Đa Luồng**: Trong quá trình huấn luyện mô hình học máy, các luồng có thể được sử dụng để chia nhỏ công việc, ví dụ như xử lý các phần của dữ liệu huấn luyện song song.
   - **Đa Tiến Trình**: Các mô hình học máy phức tạp có thể được huấn luyện trên nhiều tiến trình để tận dụng sức mạnh của các CPU đa nhân hoặc thậm chí phân phối trên các máy chủ khác nhau.

**7. Xử lý video (Video Processing)**  
   - **Đa Luồng**: Sử dụng các luồng để xử lý đồng thời các phần của video, ví dụ: một luồng mã hóa video, một luồng giải mã khác, và một luồng xử lý hình ảnh động.
   - **Đa Tiến Trình**: Xử lý video với độ phân giải cao có thể được phân chia thành nhiều tiến trình để xử lý từng phần video độc lập.

**8. Thu thập dữ liệu web (Web Crawling)**  
   - **Đa Luồng**: Thu thập dữ liệu từ nhiều trang web đồng thời bằng các luồng, mỗi luồng xử lý một trang web.
   - **Đa Tiến Trình**: Sử dụng đa tiến trình khi cần thu thập dữ liệu từ hàng nghìn hoặc hàng triệu trang web, mỗi tiến trình thu thập một nhóm trang web riêng biệt.

**9. Hệ thống phân tán (Distributed Systems)**  
   - **Đa Luồng**: Trong các hệ thống phân tán, các tiến trình có thể sử dụng nhiều luồng để xử lý đồng thời các tác vụ như truy vấn cơ sở dữ liệu, gửi yêu cầu, v.v.
   - **Đa Tiến Trình**: Các hệ thống phân tán thường sử dụng đa tiến trình để phân phối công việc xử lý giữa các máy chủ khác nhau, giúp tăng khả năng mở rộng và hiệu suất.

**10. Cơ sở dữ liệu phân tán (Distributed Databases)**  
   - **Đa Luồng**: Để cải thiện tốc độ truy vấn trong cơ sở dữ liệu phân tán, các luồng có thể xử lý các truy vấn song song trong một tiến trình.
   - **Đa Tiến Trình**: Các cơ sở dữ liệu phân tán như MongoDB hoặc Cassandra sử dụng đa tiến trình để đồng bộ hóa dữ liệu giữa các nút phân tán.

**11. Giám sát hệ thống (System Monitoring)**  
   - **Đa Luồng**: Giám sát và thu thập dữ liệu từ các hệ thống hoặc thiết bị có thể được thực hiện bằng cách sử dụng các luồng để giám sát từng hệ thống hoặc phần mềm độc lập.
   - **Đa Tiến Trình**: Đối với các hệ thống phức tạp hoặc cần xử lý dữ liệu lớn từ nhiều nguồn, có thể sử dụng đa tiến trình để thu thập và phân tích dữ liệu từ nhiều nguồn cùng lúc.

**12. Ứng dụng di động (Mobile Applications)**  
   - **Đa Luồng**: Các ứng dụng di động sử dụng đa luồng để xử lý các tác vụ như tải dữ liệu từ mạng, xử lý thông báo push, hoặc xử lý hình ảnh mà không làm gián đoạn giao diện người dùng.
   - **Đa Tiến Trình**: Trong một số trường hợp, ứng dụng di động có thể sử dụng đa tiến trình để xử lý các tác vụ phức tạp hoặc nặng, như xử lý video hoặc tính toán dữ liệu phức tạp.

# 3. Viết ra giấy rồi chụp ảnh, liệt kê các trường hợp nào thì nên dùng thread, trường hợp nào nên dùng process, khi nào thì nên dùng cả hai. Viết dưới dạng table và đưa ví dụ các bài toán

![Distributed System Architecture](/images/bl2.jpg)

# 4. Report, tìm hiểu 1. chatGPT training tập dữ liệu lớn bằng distributed system như thế nào. Đưa link nguồn tài liệu tham khảo từ google

Để huấn luyện các mô hình ngôn ngữ lớn như ChatGPT, các tổ chức thường sử dụng các hệ thống phân tán để xử lý khối lượng tính toán khổng lồ và yêu cầu về bộ nhớ. Dưới đây là các phương pháp và công cụ phổ biến được áp dụng.

## 🧠 Các phương pháp huấn luyện phân tán cho mô hình ngôn ngữ lớn

### 1. **Data Parallelism (Phân tán dữ liệu)**:
   - **Mô tả**: Dữ liệu được chia thành nhiều phần và mỗi phần được xử lý song song trên các nút khác nhau. Các cập nhật trọng số được đồng bộ hóa sau mỗi bước huấn luyện.
   - **Ví dụ**: Sử dụng **Horovod**, một thư viện hỗ trợ phân tán dữ liệu trên nhiều GPU và máy chủ.

### 2. **Model Parallelism (Phân tán mô hình)**:
   - **Mô tả**: Mô hình được chia thành nhiều phần và mỗi phần được đặt trên các thiết bị khác nhau. Phương pháp này hữu ích khi mô hình quá lớn để vừa vặn với bộ nhớ của một thiết bị duy nhất.
   - **Ví dụ**: **DeepSpeed**, một thư viện của Microsoft, hỗ trợ phân tán mô hình và tối ưu hóa bộ nhớ để huấn luyện các mô hình với hàng trăm tỷ tham số.

### 3. **Pipeline Parallelism (Phân tán theo đường ống)**:
   - **Mô tả**: Mô hình được chia thành các giai đoạn, và mỗi giai đoạn được xử lý trên các thiết bị khác nhau. Dữ liệu được chuyền qua các giai đoạn theo dạng "đường ống".
   - **Ví dụ**: **DeepSpeed** hỗ trợ phân tán theo đường ống, giúp tối ưu hóa hiệu suất huấn luyện.

### 4. **Tensor Parallelism (Phân tán theo tensor)**:
   - **Mô tả**: Các tensor (ma trận trọng số) được chia nhỏ và phân phối trên nhiều thiết bị, giúp giảm bớt yêu cầu về bộ nhớ và tăng tốc độ huấn luyện.
   - **Ví dụ**: **DeepSpeed** hỗ trợ phân tán theo tensor, cho phép huấn luyện các mô hình lớn hơn.

### 5. **Reinforcement Learning with Human Feedback (RLHF)**:
   - **Mô tả**: Sau khi huấn luyện sơ bộ, mô hình được tinh chỉnh bằng cách sử dụng phản hồi từ con người để cải thiện khả năng hiểu và phản hồi.
   - **Ví dụ**: **OpenAI** sử dụng phương pháp RLHF để huấn luyện các mô hình như **InstructGPT** và **ChatGPT**.

## 🛠️ Công cụ hỗ trợ huấn luyện phân tán

- **DeepSpeed**: Thư viện mã nguồn mở của Microsoft giúp tối ưu hóa huấn luyện mô hình lớn, hỗ trợ phân tán dữ liệu, mô hình và đường ống, đồng thời giảm thiểu yêu cầu về bộ nhớ.
- **Ray**: Một hệ thống phân tán hỗ trợ các tác vụ AI, bao gồm huấn luyện mô hình và triển khai ứng dụng.
- **Horovod**: Thư viện hỗ trợ huấn luyện phân tán trên nhiều GPU và máy chủ, tương thích với TensorFlow và PyTorch.

## 📚 Tài liệu tham khảo

- [DeepSpeed: Easy, Fast and Affordable RLHF Training of ChatGPT-like Models at All Scales](https://arxiv.org/abs/2308.01320)
- [Efficient Training of Large Language Models on Distributed Systems](https://arxiv.org/abs/2407.20018)
- [How Ray, a Distributed AI Framework, Helps Power ChatGPT](https://thenewstack.io/how-ray-a-distributed-ai-framework-helps-power-chatgpt/)
