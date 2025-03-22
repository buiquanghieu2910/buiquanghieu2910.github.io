---
layout: post
title: 🛡️ CSRF (Cross-Site Request Forgery) – Tấn công và cách phòng tránh
date: 2025-03-23 05:42 +0700
categories: [Security]
tags:
  [
    CSRF là gì,
    Cross-Site Request Forgery,
    Cách phòng chống CSRF,
    CSRF token,
    Phòng tránh CSRF trong ứng dụng web,
  ]
image:
  path: /assets/img/csrf-va-cach-phong-tranh/csrf.jpg
---

## 🎯 **Giới thiệu về CSRF**
**CSRF (Cross-Site Request Forgery)** là một loại tấn công trong đó kẻ tấn công giả mạo một yêu cầu từ phía người dùng đã đăng nhập hợp lệ vào một trang web, với mục đích thực hiện các hành động trái phép thay mặt người dùng đó. CSRF thường xảy ra khi người dùng truy cập một trang web chứa mã độc, và khi họ thực hiện hành động nào đó (ví dụ: chuyển tiền, thay đổi mật khẩu) mà không hay biết.

CSRF có thể gây ra những hậu quả nghiêm trọng như **thực hiện giao dịch tài chính** trái phép, **thay đổi mật khẩu**, hoặc **gửi thông tin nhạy cảm** mà không có sự đồng ý của người dùng.

## 🔧 **Cách thức hoạt động của CSRF**
1. Người dùng đã đăng nhập vào một trang web hợp pháp và có session hợp lệ (ví dụ: tài khoản ngân hàng).
2. Kẻ tấn công tạo ra một trang web độc hại chứa mã HTML hoặc JavaScript, có thể gửi yêu cầu tới trang web hợp pháp của người dùng (ví dụ: chuyển tiền).
3. Khi người dùng truy cập trang web độc hại, mã độc sẽ tự động gửi yêu cầu này mà không cần người dùng thực hiện hành động, vì người dùng đã đăng nhập từ trước.
4. Trang web hợp pháp xử lý yêu cầu đó mà không nhận biết đây là yêu cầu giả mạo.

## 📊 **Ví dụ về CSRF**
Giả sử một ứng dụng ngân hàng có chức năng chuyển tiền:
```html
<form action="https://bank.com/transfer" method="POST">
    <input type="text" name="amount" value="1000">
    <input type="text" name="recipient" value="hacker_account">
    <button type="submit">Transfer</button>
</form>
```

## 🛡️ **Cách phòng tránh CSRF**

### ✅ **1. Sử dụng CSRF Token**
- **CSRF token** là một chuỗi ngẫu nhiên được tạo ra và gắn vào mỗi form hoặc yêu cầu. Server sẽ kiểm tra token này khi nhận được yêu cầu, và nếu token không hợp lệ, yêu cầu sẽ bị từ chối.
- Đảm bảo mỗi form có một trường `csrf_token` chứa giá trị duy nhất cho mỗi phiên làm việc của người dùng.

### ✅ **2. Kiểm tra phương thức HTTP**
- CSRF chỉ hoạt động khi kẻ tấn công có thể gửi **Yêu cầu GET/POST** giả mạo. Cần đảm bảo rằng các yêu cầu thay đổi trạng thái (ví dụ: chuyển tiền, thay đổi mật khẩu) chỉ sử dụng **phương thức POST** và được xác thực kỹ.

### ✅ **3. Sử dụng SameSite Cookie Attribute**
- **SameSite cookies** giúp ngăn cản việc gửi cookie trong các yêu cầu cross-site (từ một trang web khác). Có thể thiết lập cookie **SameSite** với giá trị `Strict` hoặc `Lax` để bảo vệ ứng dụng khỏi các yêu cầu từ trang web khác.

**Ví dụ**:
```
Set-Cookie: sessionid=your_session_id; SameSite=Strict;
```

### ✅ **4. Kiểm tra Referer và Origin header**
- Kiểm tra header **Referer** hoặc **Origin** trong các yêu cầu để đảm bảo rằng yêu cầu đến từ một trang hợp lệ, không phải từ một trang web độc hại.

### ✅ **5. Yêu cầu người dùng xác nhận hành động quan trọng**
- Đối với các hành động quan trọng như chuyển tiền hoặc thay đổi thông tin tài khoản, hãy yêu cầu người dùng xác nhận lại trước khi thực hiện hành động (ví dụ: qua một mã OTP).

## 🚀 **Tổng kết**
**CSRF** là một trong những mối đe dọa phổ biến đối với các ứng dụng web, nhưng có thể phòng tránh được thông qua các biện pháp bảo mật như **CSRF tokens**, **SameSite cookies**, và kiểm tra **Referer/Origin**. Việc bảo vệ ứng dụng khỏi CSRF giúp bảo vệ người dùng khỏi các hành động không mong muốn và đảm bảo tính toàn vẹn của hệ thống.