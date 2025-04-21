---
layout: post
title: 📡 Hướng Dẫn Sử Dụng Ngrok - Tạo Tunnels An Toàn
date: 2025-04-22 02:24 +0700
categories: [Technology]
tags: [
    Ngrok,
    Tạo tunnel,
    Hướng dẫn Ngrok,
    Ngrok for developers,
    Cài đặt Ngrok,
    Bảo mật với Ngrok
  ]
image:
  path: /assets/img/huong-dan-sd-ngrok-cai-dat-va-tinh-nang/ngrok.jpg
---

Ngrok là một công cụ mạnh mẽ giúp bạn tạo ra một tunnel (đường hầm) bảo mật từ máy tính cục bộ của bạn đến một địa chỉ URL công khai, giúp bạn dễ dàng chia sẻ ứng dụng web chạy trên máy tính của mình mà không cần phải cấu hình router hoặc mua hosting.

## 🛠 Cài Đặt Ngrok

1. **Tải Ngrok:**
   Truy cập [Trang chủ của Ngrok](https://ngrok.com/download) và tải về phiên bản tương ứng với hệ điều hành của bạn (Windows, MacOS, Linux).
2. **Cài đặt Ngrok:**

   - Đối với **Windows**, giải nén tệp tải về và di chuyển tệp `ngrok.exe` vào thư mục bạn muốn sử dụng.
   - Đối với **MacOS/Linux**, sử dụng dòng lệnh:
     ```bash
     unzip ngrok-stable-darwin-amd64.zip
     sudo mv ngrok /usr/local/bin
     ```

3. **Đăng ký tài khoản (tuỳ chọn):**
   Để nhận được các tính năng bổ sung, bạn có thể đăng ký tài khoản miễn phí tại [ngrok.com](https://ngrok.com/).

## 🚀 Tạo Tunnel với Ngrok

### Bước 1: Khởi động một ứng dụng cục bộ

Trước khi sử dụng Ngrok, bạn cần phải có một ứng dụng đang chạy trên máy tính của bạn. Ví dụ, bạn có thể chạy một ứng dụng Flask trên cổng `5000`:

```bash
python app.py
```

### Bước 2: Tạo Tunnel

Sử dụng lệnh Ngrok để tạo một tunnel đến cổng mà ứng dụng của bạn đang chạy:

```bash
ngrok http 5000
```

Sau khi thực hiện lệnh trên, Ngrok sẽ cung cấp cho bạn một URL công khai, ví dụ: http://abc123.ngrok.io, bạn có thể chia sẻ URL này với người khác để họ có thể truy cập vào ứng dụng của bạn.

## 🛡 Bảo mật và Tính năng nâng cao

Ngrok không chỉ giúp tạo tunnel mà còn cung cấp các tính năng bảo mật hữu ích như xác thực HTTP, bảo vệ bằng mật khẩu và giới hạn truy cập.

- Xác thực HTTP: Bạn có thể thêm xác thực cơ bản cho đường hầm của mình:

```bash
ngrok http -auth="username:password" 5000
```

- Bảo mật SSL: Ngrok cung cấp miễn phí HTTPS cho các tunnel, giúp bảo vệ dữ liệu của bạn khi truyền qua mạng.

## 💡 Các Tính Năng Nâng Cao Khác

- **Ngrok Dashboard**:  
  Giám sát và phân tích các kết nối thông qua bảng điều khiển trực tuyến tại [ngrok.com](https://ngrok.com/).

- **Tùy chỉnh Subdomains**:  
  Đối với tài khoản cao cấp, bạn có thể tùy chỉnh subdomain của URL. Ví dụ:
  ```bash
  ngrok http -subdomain=mylocalapp 5000
  ```

## 🎨 Kết Luận

Ngrok là một công cụ tuyệt vời để chia sẻ ứng dụng web cục bộ, thử nghiệm với webhooks, hoặc phục vụ cho các nhu cầu phát triển phần mềm nhanh chóng. Các tính năng như bảo mật SSL và xác thực HTTP cũng giúp nâng cao bảo mật cho các ứng dụng của bạn.

Đừng quên ghé thăm **Trang chính thức của Ngrok** để tìm hiểu thêm chi tiết và tải về phiên bản mới nhất!

🌐 **Tìm hiểu thêm**:

- [Ngrok Documentation](https://ngrok.com/docs)
- [Ngrok Blog](https://ngrok.com/blog)
