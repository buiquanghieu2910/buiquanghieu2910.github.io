---
layout: post
title: 🌐 API là gì? Tất tần tật về Giao diện lập trình ứng dụng
date: 2025-03-23 21:35 +0700
categories: [Technology]
tags:
  [
    API là gì, 
    giao diện lập trình ứng dụng, 
    REST API, 
    cách gọi API, ví dụ API,
  ]
image:
  path: /assets/img/api-va-cach-hoat-dong/api.jpg
---

## 📌 API là gì?

**API** (Application Programming Interface) là **giao diện lập trình ứng dụng**, cho phép các phần mềm **giao tiếp và trao đổi dữ liệu với nhau**.

Hiểu đơn giản, API giống như **một chiếc cầu nối** giữa hai hệ thống, cho phép bên này “hỏi” và bên kia “trả lời”.

---

## 📦 Ví dụ thực tế

📱 Một ứng dụng đặt đồ ăn sử dụng API để:
- Lấy danh sách món ăn từ máy chủ (server).
- Gửi đơn hàng đến hệ thống nhà hàng.
- Nhận trạng thái giao hàng theo thời gian thực.

---

## 🔄 Cách hoạt động của API
👨 Người dùng → 📱 Ứng dụng → 🌐 API → 🖥️ Server → 📦 Dữ liệu → Trả lại API → Hiển thị cho người dùng

## 🧱 Các loại API phổ biến

### 1. 🧭 REST API
- Giao tiếp qua HTTP (GET, POST, PUT, DELETE).
- Dữ liệu thường ở định dạng JSON hoặc XML.
- Phổ biến nhất hiện nay (đặc biệt trong web, mobile).

### 2. 🛰️ GraphQL API
- Gửi một truy vấn duy nhất và chỉ nhận đúng dữ liệu cần.
- Hiệu quả hơn REST khi dữ liệu phức tạp.

### 3. 🔐 WebSocket API
- Giao tiếp hai chiều theo thời gian thực (real-time).
- Thường dùng cho chat app, game, livestream...

---

## 🧪 Ví dụ 1 lời gọi API đơn giản (REST)

```http
GET https://api.example.com/users/123

Response:
{
  "id": 123,
  "name": "Nguyễn Văn A",
  "email": "nva@example.com"
}
```

## 🚦 HTTP Methods thường dùng trong API

| Method | Mục đích              | Ví dụ                        |
|--------|-----------------------|------------------------------|
| GET    | Lấy dữ liệu           | Lấy danh sách người dùng     |
| POST   | Tạo mới dữ liệu       | Tạo tài khoản mới            |
| PUT    | Cập nhật toàn bộ      | Cập nhật thông tin user      |
| PATCH  | Cập nhật một phần     | Sửa email user               |
| DELETE | Xoá dữ liệu           | Xoá người dùng               |

---

## 🔐 API cần bảo mật như thế nào?

- Sử dụng **token** (ví dụ: JWT) để xác thực.
- Giới hạn quyền truy cập (**role-based access**).
- Giới hạn tần suất truy cập (**rate limiting**).
- Mã hóa dữ liệu truyền qua **HTTPS**.

---

## ✅ Lợi ích của API

- 🌍 **Kết nối linh hoạt** giữa các hệ thống.
- ♻️ **Tái sử dụng** được nhiều nơi (web, mobile, bên thứ ba).
- 🚀 **Tăng tốc phát triển phần mềm**.
- 🔌 **Dễ tích hợp** với dịch vụ ngoài (Zalo, Google, Facebook...).

---

## 🧠 Tổng kết

> **API** chính là "ngôn ngữ chung" để các hệ thống hiểu nhau.  
Từ **web app**, **mobile app** đến các hệ thống **IoT** – tất cả đều cần API để **trao đổi, kết nối và mở rộng**.

Nếu bạn đang học **backend**, **frontend** hay muốn tích hợp với bên thứ ba –  
👉 *Hãy bắt đầu với API ngay hôm nay!* 💪
