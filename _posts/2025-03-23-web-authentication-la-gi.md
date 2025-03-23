---
layout: post
title: 🔐 Web Authentication là gì? Các phương pháp xác thực phổ biến trên website
date: 2025-03-23 22:03 +0700
categories: [Security]
tags:
  [
    web authentication là gì,
    xác thực người dùng web,
    session vs token,
    jwt là gì,
    đăng nhập bảo mật,
  ]
image:
  path: /assets/img/web-authentication-la-gi/Web-Authentication.jpg
---

## 📌 Web Authentication là gì?

**Web Authentication** (xác thực trên web) là quá trình **kiểm tra danh tính người dùng** truy cập vào một ứng dụng hoặc hệ thống. Mục tiêu là đảm bảo chỉ những người **được phép** mới có thể truy cập tài nguyên bảo mật như trang quản trị, tài khoản cá nhân, giỏ hàng...

---

## 🧾 Xác thực khác gì phân quyền?

- ✅ **Authentication**: Ai đang đăng nhập? (kiểm tra danh tính)
- ✅ **Authorization**: Người đó **được phép làm gì** trong hệ thống?

---

## 🔐 Các phương pháp xác thực phổ biến

### 1. 📧 Xác thực bằng username/password (Basic Auth)

- Người dùng nhập email + mật khẩu → gửi đến server để kiểm tra.
- Nếu đúng → cấp quyền truy cập.
- Nếu sai → trả về lỗi 401 Unauthorized.

📉 Nhược điểm:
- Dễ bị tấn công nếu không mã hóa.
- Cần bảo vệ mật khẩu trong quá trình truyền tải (sử dụng HTTPS).

---

### 2. 🍪 Session-based Authentication

- Sau khi đăng nhập, server tạo một **session** lưu trên server và gửi lại cho client một **session ID** dưới dạng cookie.
- Mỗi lần client gửi request → kèm cookie → server kiểm tra session và xác nhận.

✅ Ưu điểm:
- Phù hợp cho các hệ thống truyền thống (monolithic).
- Dễ quản lý từ phía server.

---

### 3. 🔐 Token-based Authentication (thường dùng JWT)

- Sau khi đăng nhập, server tạo **token** chứa thông tin người dùng (thường dùng JWT).
- Token được gửi kèm trong header của các request tiếp theo.

📌 Ví dụ header:
```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI...
```
### ✅ Ưu điểm của Token-based Authentication (JWT)

- ❌ Không cần lưu session trên server.
- ✅ Dễ dàng tích hợp với **SPA**, **mobile app**, **microservices**.
- 🔄 Có thể triển khai xác thực phân tán giữa nhiều service.

---

### 4. 🪪 OAuth2 – Xác thực qua bên thứ ba

Cho phép người dùng **đăng nhập bằng tài khoản bên thứ ba** như Google, Facebook, GitHub...

- Sau khi đăng nhập thành công, hệ thống nhận **access token** từ nhà cung cấp (provider) để xác minh danh tính.
- Không cần lưu mật khẩu người dùng trong hệ thống.

📍 **Phù hợp với:**
- Ứng dụng cộng đồng
- Tích hợp mạng xã hội
- Hệ thống không cần quản lý thông tin đăng nhập riêng

---

## 🧱 So sánh Session vs Token vs OAuth2

| Tiêu chí               | 🧁 Session-Based    | 🪙 Token-Based (JWT) | 🪪 OAuth2 (Social Login)   |
|------------------------|--------------------|-----------------------|-----------------------------|
| 🔁 Lưu trạng thái      | ✅ Có              | ❌ Không              | ✅ Có (tuỳ cách triển khai) |
| ⚙️ Dễ tích hợp SPA     | ❌ Khó             | ✅ Dễ                 | ✅ Dễ                        |
| 🗃 Server lưu thông tin | ✅ Có              | ❌ Không              | ❌ Không                     |
| 🚀 Dễ mở rộng hệ thống | ❌ Hạn chế         | ✅ Cao                | ✅ Cao                       |

---

## 🔐 Cách bảo mật quá trình xác thực

- ✅ Sử dụng **HTTPS** để mã hóa dữ liệu truyền đi.
- ✅ Không lưu mật khẩu dưới dạng plain text → dùng **hash** (bcrypt, scrypt...).
- ✅ Thiết lập **giới hạn số lần đăng nhập sai** để tránh brute-force.
- ✅ Áp dụng **xác thực 2 yếu tố (2FA)** cho tài khoản nhạy cảm.
- ✅ Cấu hình **thời gian hết hạn** hợp lý cho session hoặc token.

---

## 🧠 Tổng kết

> **Authentication** là **lớp bảo vệ đầu tiên** của mọi hệ thống web.

Việc chọn **phương pháp xác thực phù hợp** sẽ giúp bạn xây dựng hệ thống:

- 🔐 **An toàn hơn**
- ✨ **Trải nghiệm người dùng tốt hơn**
- 🧱 **Dễ mở rộng và tích hợp về sau**