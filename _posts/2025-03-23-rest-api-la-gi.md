---
layout: post
title: 🌐 REST API là gì? Tìm hiểu chuẩn thiết kế phổ biến nhất hiện nay
date: 2025-03-23 21:42 +0700
categories: [API]
tags:
  [
    rest api là gì, 
    kiến trúc rest api, 
    chuẩn restful, 
    restful api là gì, 
    restful design
  ]
image:
  path: /assets/img/rest-api-la-gi/rest-api.jpg
---

## 🧠 REST API là gì?

**REST API** (Representational State Transfer) là một **kiến trúc thiết kế API** dựa trên giao thức HTTP, được dùng rộng rãi trong phát triển web và mobile. REST không phải là một công nghệ, mà là **tập hợp nguyên tắc và ràng buộc** để xây dựng API dễ hiểu, dễ sử dụng và dễ mở rộng.

---

## ⚙️ Cách hoạt động của REST API

REST sử dụng các phương thức HTTP như:

- **GET** – Lấy dữ liệu
- **POST** – Tạo mới
- **PUT / PATCH** – Cập nhật
- **DELETE** – Xoá dữ liệu

📌 Dữ liệu thường được trả về ở định dạng **JSON** hoặc **XML** (phổ biến nhất hiện nay là JSON).

---

## 📐 6 đặc tính của một RESTful API

Để được xem là "RESTful", API cần tuân thủ các nguyên tắc sau:

### 1. **Client – Server** (Phân tách giao diện và xử lý)
- Giao diện người dùng và xử lý dữ liệu tách biệt.
- Giúp frontend và backend phát triển độc lập.

### 2. **Stateless** (Không lưu trạng thái)
- Mỗi request là độc lập, không phụ thuộc vào request trước đó.
- Mọi thông tin cần thiết phải có trong mỗi request.

### 3. **Cacheable** (Có thể lưu vào bộ nhớ đệm)
- Response từ server nên cho phép cache để tăng hiệu suất.

### 4. **Uniform Interface** (Giao diện thống nhất)
- Tài nguyên được định danh qua URL.
- Sử dụng HTTP method đúng mục đích (GET, POST...).
- Phản hồi rõ ràng, thống nhất (status code, header, body).

### 5. **Layered System** (Kiến trúc phân tầng)
- Hệ thống có thể có nhiều lớp: API Gateway, Auth service, Backend...
- Client không cần biết có bao nhiêu lớp, chỉ cần gọi đúng endpoint.

### 6. **Code on Demand** (tuỳ chọn)
- Cho phép server trả về code (JavaScript) để client thực thi – thường ít dùng trong thực tế.

---

## 📦 Ví dụ REST API đơn giản

Giả sử bạn có một API quản lý người dùng:

| Hành động        | HTTP Method | Endpoint               |
|------------------|-------------|------------------------|
| Lấy danh sách    | GET         | `/api/users`           |
| Lấy chi tiết     | GET         | `/api/users/:id`       |
| Tạo mới          | POST        | `/api/users`           |
| Cập nhật         | PUT         | `/api/users/:id`       |
| Xoá người dùng   | DELETE      | `/api/users/:id`       |

### 🧪 Ví dụ gọi API:

```json
GET: /api/users/123

response:
{
  "id": 123,
  "name": "Nguyễn Văn A",
  "email": "nva@example.com"
}
```

## 🎯 REST API khác gì với GraphQL?

| 🧩 Tiêu chí         | 🔁 REST API                  | 🧠 GraphQL                        |
|---------------------|------------------------------|-----------------------------------|
| 🔍 Truy vấn dữ liệu | Theo nhiều endpoint          | Một endpoint duy nhất             |
| 📦 Dữ liệu trả về   | Trả toàn bộ theo thiết kế    | Trả đúng dữ liệu client yêu cầu   |
| ⚡ Hiệu suất         | Có thể bị thừa/thiếu dữ liệu | Linh hoạt hơn với truy vấn        |

---

## ✅ Khi nào nên dùng REST API?

- 🧭 Khi bạn cần giao tiếp giữa **frontend và backend đơn giản**, dễ triển khai.
- 🪄 Khi hệ thống **không quá phức tạp** về mối quan hệ dữ liệu.
- 🌐 Khi bạn cần **dễ tích hợp với các hệ thống bên ngoài** (REST là chuẩn phổ biến nhất hiện nay).

---

## 🧠 Tổng kết

> REST API là **chuẩn thiết kế phổ biến nhất** hiện nay khi xây dựng hệ thống **web**, **mobile**, **backend** – nhờ tính **đơn giản**, **rõ ràng** và **dễ tích hợp**.

Dù hiện nay có nhiều lựa chọn mới như **GraphQL**, **gRPC**… nhưng **REST vẫn là điểm khởi đầu tốt nhất** nếu bạn đang học hoặc làm quen với API 💪.