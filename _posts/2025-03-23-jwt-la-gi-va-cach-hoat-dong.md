---
layout: post
title: 🔐 JWT là gì? Cách hoạt động và ứng dụng trong xác thực người dùng
date: 2025-03-23 22:09 +0700
categories: [Security]
tags:
  [
    jwt là gì, 
    cấu trúc jwt, 
    cách hoạt động jwt,
    xác thực bằng jwt, 
    bearer token là gì  
  ]
image:
  path: /assets/img/jwt-la-gi-va-cach-hoat-dong/jwt-la-gi.jpg
---

## 📌 JWT là gì?

**JWT** (JSON Web Token) là một tiêu chuẩn mở (RFC 7519) dùng để **truyền thông tin dưới dạng token** giữa client và server một cách an toàn, nhỏ gọn và có thể xác minh được.

Token JWT thường được sử dụng trong hệ thống **xác thực (authentication)** và **phân quyền (authorization)** của web app, mobile app hoặc API.

---

## 🧱 Cấu trúc của một JWT

JWT gồm **3 phần**, được nối với nhau bằng dấu `.`
xxxxx.yyyyy.zzzzz


| Thành phần   | Mô tả                                                                 |
|--------------|----------------------------------------------------------------------|
| 📘 Header     | Thông tin loại token và thuật toán ký (ví dụ: HS256)                 |
| 📦 Payload    | Dữ liệu cần truyền: userId, email, role... (KHÔNG nên chứa mật khẩu) |
| 🔐 Signature  | Chữ ký số – dùng để kiểm tra tính toàn vẹn của token                 |

---

### 🔍 Ví dụ JWT (rút gọn)

```text
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJ1c2VySWQiOjEyMywibmFtZSI6Ik5ndXnhbiBW4bqhbiBBIn0.
sflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

## 🔄 JWT hoạt động như thế nào?

1. 🧑 Người dùng đăng nhập bằng email/mật khẩu.
2. ✅ Server xác thực thông tin → tạo JWT → gửi về cho client.
3. 🌐 Client lưu JWT trong **localStorage**, **sessionStorage** hoặc **cookie**.
4. 🔄 Ở mỗi request tiếp theo, client gửi JWT kèm theo trong **Authorization header**:

```http
Authorization: Bearer <token>
```
## 🛡 Server kiểm tra token như thế nào?

Sau khi nhận được JWT từ client, server sẽ thực hiện các bước:

- 🔍 **Giải mã chữ ký** (`verify signature`) để đảm bảo token không bị sửa đổi.
- ⌛ **Kiểm tra thời hạn (`exp`)** – nếu token hết hạn → từ chối.
- 📦 **Giải mã payload** để lấy thông tin người dùng (`userId`, `role`, ...).

✅ Nếu hợp lệ → Cho phép xử lý request  
❌ Nếu không hợp lệ → Trả về mã lỗi `401 Unauthorized` hoặc `403 Forbidden`.

---

## ⚙️ Ưu điểm của JWT

- ✅ Không cần lưu session trên server → **Stateless**.
- 🔐 Dễ xác minh bằng chữ ký → tăng độ an toàn và hiệu suất.
- 🌐 Dễ tích hợp với **SPA**, **mobile app**, **microservices**.
- 🔁 Tùy chỉnh payload dễ dàng theo nhu cầu (ví dụ: `userId`, `role`, `permissions`...).

---

## ⚠️ Nhược điểm và lưu ý khi dùng JWT

- ❌ **Không thể thu hồi** token nếu không có hệ thống **blacklist**.
- ⌛ Cần cài đặt **thời gian hết hạn (`expiresIn`)** hợp lý để giảm rủi ro lộ token.
- ❌ **Không lưu thông tin nhạy cảm** (mật khẩu, OTP, thông tin tài chính...) trong payload vì token có thể bị giải mã.
- 🛡️ Token phải được ký bằng **secret key mạnh** (với HS256) hoặc **private key** (với RS256) để tránh bị giả mạo.

---

## 🧪 Khi nào nên dùng JWT?

✅ JWT phù hợp khi bạn cần:

- 🧱 Xây dựng **API backend stateless**
- ⚙️ Tích hợp với **SPA** (React, Vue, Angular)
- 🔗 Giao tiếp giữa các **microservices**
- 📱 Xác thực đồng thời cho **web và mobile app**

---

## 🧠 Tổng kết

> **JWT** là giải pháp xác thực người dùng **hiện đại**, **nhẹ**, và **dễ triển khai**.

Tuy nhiên, bạn cần:

- 🔄 Hiểu rõ cách hoạt động bên trong
- ⚠️ Nhận thức các **lỗ hổng bảo mật**
- 🔐 Kết hợp thêm các kỹ thuật như **HTTPS**, **2FA**, **token expiration**, **blacklist**

👉 Sử dụng đúng cách sẽ giúp hệ thống của bạn **an toàn hơn**, **linh hoạt hơn**, và **dễ mở rộng trong môi trường thực tế** 💪
