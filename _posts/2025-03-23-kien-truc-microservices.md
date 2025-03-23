---
layout: post
title: 🧱 Microservices là gì? Hiểu đúng về kiến trúc Microservices
date: 2025-03-23 17:20 +0700
categories: [Design Pattern]
tags:
  [
    microservices là gì,
    kiến trúc microservices,
    ví dụ microservices,
    ưu nhược điểm microservices,
    khi nào nên dùng microservices,
    microservices vs monolith,
  ]
image:
  path: /assets/img/kien-truc-microservices/microservice.jpg
---

## 🔍 Giới thiệu

**Microservices** (hay kiến trúc vi dịch vụ) là một kiểu kiến trúc phần mềm, trong đó ứng dụng được chia thành nhiều **dịch vụ nhỏ, độc lập**, mỗi dịch vụ đảm nhận một chức năng riêng biệt và giao tiếp với nhau thông qua **API** (thường là HTTP REST, gRPC...).

> 💡 Tư tưởng chính: "Tách ra để dễ quản lý, dễ mở rộng".

---

## 🧩 Đặc điểm chính của Microservices

- 🧱 **Tách biệt chức năng**: Mỗi service đảm nhiệm một nhiệm vụ cụ thể như Auth, User, Order...
- 🚀 **Triển khai độc lập**: Có thể deploy, scale từng service mà không ảnh hưởng đến toàn hệ thống.
- ⚙️ **Công nghệ độc lập**: Các service có thể viết bằng ngôn ngữ, framework khác nhau.
- 🔁 **Giao tiếp qua API**: Chủ yếu sử dụng HTTP, RESTful API, gRPC, message queue (Kafka, RabbitMQ).

---

## 📦 So sánh Monolith vs Microservices

| Tiêu chí         | Monolithic App            | Microservices                            |
| ---------------- | ------------------------- | ---------------------------------------- |
| Cấu trúc         | Một khối lớn duy nhất     | Nhiều dịch vụ nhỏ tách biệt              |
| Triển khai       | Deploy toàn bộ ứng dụng   | Deploy từng service riêng lẻ             |
| Công nghệ        | Một stack công nghệ       | Mỗi service dùng công nghệ riêng nếu cần |
| Độ phụ thuộc     | Cao                       | Thấp (service độc lập)                   |
| Khả năng mở rộng | Hạn chế                   | Dễ scale theo chiều ngang                |
| Bảo trì          | Khó khăn khi hệ thống lớn | Dễ bảo trì, dễ quản lý                   |

---

## 🔄 Sơ đồ kiến trúc Microservices

                       🌐 Client
                          │
                          ▼
                   🛡️ API Gateway
                   /       |       \
                  ▼        ▼        ▼
            📦 Service A  📦 Service B  📦 Service C
               │             │             │
               ▼             ▼             ▼
         🗄️ Database A   🗄️ Database B   🗄️ Database C

📌 **Lưu ý:** Mỗi service thường có database riêng để đảm bảo độc lập.

---

## 🧠 Ưu điểm của Microservices

✅ Tăng khả năng mở rộng hệ thống  
✅ Dễ bảo trì, phát triển, triển khai độc lập  
✅ Đội ngũ có thể làm việc song song (mỗi team 1 service)  
✅ Tăng khả năng tái sử dụng và linh hoạt công nghệ

---

## ⚠️ Nhược điểm

❌ Quản lý phức tạp hơn so với monolith  
❌ Giao tiếp giữa các service dễ phát sinh lỗi (timeout, failover...)  
❌ Khó khăn trong việc debug, test toàn hệ thống  
❌ Yêu cầu cao về DevOps, CI/CD, giám sát, logging

---

## 🛠️ Công nghệ thường dùng với Microservices

| Thành phần            | Công nghệ gợi ý                |
| --------------------- | ------------------------------ |
| API Gateway           | NGINX, Kong, API Gateway AWS   |
| Service Communication | REST, gRPC, RabbitMQ, Kafka    |
| Service Discovery     | Consul, Eureka, Kubernetes     |
| Containerization      | Docker, Kubernetes             |
| Monitoring & Logging  | Prometheus, Grafana, ELK stack |
| Authentication        | JWT, OAuth2, Keycloak          |

---

## 📌 Khi nào nên dùng Microservices?

- Dự án **lớn**, nhiều chức năng độc lập.
- Có nhiều team phát triển song song.
- Cần **scale linh hoạt** từng phần hệ thống.
- Tổ chức có nền tảng DevOps, CI/CD tốt.

---

## ❓ Khi nào KHÔNG nên dùng

- Ứng dụng nhỏ, chưa rõ yêu cầu mở rộng.
- Thiếu kinh nghiệm DevOps/CI/CD.
- Dự án cần ra MVP nhanh, đơn giản.

---

## 🏁 Kết luận

**Microservices** là một hướng đi hiện đại cho các hệ thống quy mô lớn, giúp tối ưu hóa hiệu suất, bảo trì và khả năng mở rộng. Tuy nhiên, nó đòi hỏi kiến thức về DevOps, giám sát, và một tư duy kiến trúc rõ ràng.  
➡️ _Không phải mọi dự án đều cần microservices, nhưng nếu áp dụng đúng, bạn sẽ gặt hái được rất nhiều lợi ích!_
