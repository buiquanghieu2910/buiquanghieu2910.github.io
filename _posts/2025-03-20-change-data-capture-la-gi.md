---
layout: post
title: 🔥 Giới thiệu về CDC (Change Data Capture) – Công nghệ Theo Dõi Thay Đổi Dữ Liệu
date: 2025-03-20 23:03 +0700
categories: [Database & Data Engineering]
tags:
  [
    Change Data Capture là gì,
    Hướng dẫn CDC,
    CDC với Debezium,
    Các phương pháp CDC trong database
  ]
image:
  path: /assets/img/change-data-capture-la-gi/CDC.png
---

## 🎯 **CDC là gì?**
**CDC (Change Data Capture)** là một kỹ thuật giúp **theo dõi và ghi nhận các thay đổi trong dữ liệu** của cơ sở dữ liệu. Thay vì quét toàn bộ bảng để tìm dữ liệu thay đổi, CDC giúp **phát hiện và ghi nhận chỉ các thay đổi (INSERT, UPDATE, DELETE)** theo thời gian thực hoặc gần thời gian thực.

📌 **Các đặc điểm nổi bật của CDC:**
- **Ghi nhận thay đổi dữ liệu hiệu quả**, không cần quét toàn bộ bảng.
- **Cải thiện hiệu suất và giảm tải cho hệ thống**.
- **Hỗ trợ đồng bộ dữ liệu theo thời gian thực** giữa các hệ thống.
- **Tích hợp tốt với Big Data, ETL, Data Warehousing và Streaming Systems**.

---

## ✅ **Lợi ích của CDC**
✔ **Giúp đồng bộ dữ liệu nhanh chóng giữa các hệ thống** (Database Replication, Data Warehouse, Kafka, v.v.).
✔ **Hỗ trợ hệ thống event-driven**, phù hợp với Microservices.
✔ **Cải thiện hiệu suất của ETL**, chỉ xử lý dữ liệu thay đổi thay vì quét toàn bộ dữ liệu.
✔ **Dễ dàng phát hiện thay đổi trong dữ liệu**, giúp hệ thống analytics & monitoring chính xác hơn.
✔ **Giảm thiểu rủi ro mất dữ liệu** trong quá trình đồng bộ.

🚀 **Ví dụ ứng dụng thực tế:**
- **Cập nhật dữ liệu real-time từ database sang hệ thống Big Data (Kafka, Snowflake, ElasticSearch)**.
- **Đồng bộ dữ liệu giữa hệ thống On-Premise và Cloud**.
- **Theo dõi & xử lý giao dịch ngân hàng theo thời gian thực**.
- **Tự động cập nhật dữ liệu khách hàng khi có thay đổi trong hệ thống CRM.**

---

## 🔥 **Các phương pháp triển khai CDC**
### **1️⃣ CDC dựa trên Log (Log-based CDC)**
- Theo dõi trực tiếp **binlog, WAL logs, Redo logs** của database.
- Hiệu suất cao, phù hợp với dữ liệu thay đổi liên tục.
- Hỗ trợ tốt trên MySQL (binlog), PostgreSQL (WAL), Oracle (Redo logs).

### **2️⃣ CDC dựa trên Trigger (Trigger-based CDC)**
- Dùng **trigger trong database** để ghi nhận thay đổi vào bảng log.
- Dễ triển khai nhưng có thể ảnh hưởng đến hiệu suất database.

### **3️⃣ CDC dựa trên Timestamp (Timestamp-based CDC)**
- Sử dụng **cột timestamp** để xác định dữ liệu thay đổi.
- Không yêu cầu quyền đặc biệt, nhưng có thể bỏ sót dữ liệu nếu ứng dụng không cập nhật timestamp đúng cách.

### **4️⃣ CDC dựa trên Batch Query (Polling-based CDC)**
- Định kỳ quét database để tìm dữ liệu thay đổi.
- Phù hợp với dữ liệu ít thay đổi, nhưng có độ trễ cao.

---

## 📊 **So sánh các phương pháp CDC**

| **Phương pháp**         | **Hiệu suất** | **Độ chính xác** | **Ứng dụng phổ biến** |
|-----------------------|--------------|----------------|------------------|
| Log-based CDC       | ✅ Cao       | ✅ Chính xác cao  | MySQL, PostgreSQL, Oracle |
| Trigger-based CDC   | ❌ Ảnh hưởng hiệu suất | ✅ Chính xác cao  | SQL Server, Oracle |
| Timestamp-based CDC | ✅ Trung bình | ❌ Có thể bỏ sót dữ liệu | MongoDB, NoSQL DB |
| Polling-based CDC   | ❌ Thấp      | ❌ Có độ trễ cao | ETL truyền thống |

📌 **Log-based CDC là phương pháp tối ưu nhất về hiệu suất và độ chính xác.**

---

## 🚀 **Các công cụ hỗ trợ CDC phổ biến**
### **1️⃣ Debezium** (Mở rộng Kafka Connect)
- Hỗ trợ CDC cho **MySQL, PostgreSQL, MongoDB, Oracle, SQL Server**.
- Tích hợp với **Apache Kafka, Elasticsearch, BigQuery, Snowflake**.
- **Mạnh mẽ, real-time, open-source**.

### **2️⃣ AWS DMS (Database Migration Service)**
- Hỗ trợ CDC trên AWS Cloud.
- Đồng bộ dữ liệu từ **RDS, Aurora, DynamoDB, Redshift**.
- **Phù hợp với hệ thống Cloud-Native**.

### **3️⃣ Oracle GoldenGate**
- Giải pháp CDC **do Oracle phát triển**.
- Hỗ trợ **multi-database** và replication trên hệ thống lớn.
- **Tốn phí, phù hợp với doanh nghiệp lớn**.

### **4️⃣ StreamSets**
- Công cụ ETL mạnh mẽ hỗ trợ CDC.
- Hỗ trợ **Kafka, Snowflake, BigQuery**.
- Phù hợp với **hệ thống dữ liệu lớn**.

---

## 🏆 **Kết luận**
- **CDC giúp theo dõi thay đổi dữ liệu một cách hiệu quả**, giảm tải hệ thống, cải thiện hiệu suất ETL.
- **Log-based CDC là phương pháp tối ưu**, phù hợp cho hệ thống real-time.
- **Debezium + Kafka là lựa chọn phổ biến nhất** để triển khai CDC hiện nay.
- **Nếu bạn làm việc với AWS, hãy dùng AWS DMS để tận dụng Cloud CDC.**