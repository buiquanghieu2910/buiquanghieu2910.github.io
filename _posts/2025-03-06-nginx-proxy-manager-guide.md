---
layout: post
title: Hướng Dẫn Cài Đặt & Sử Dụng Nginx Proxy Manager
date: 2025-03-06 02:04 +0700
categories: [Nginx]
tags:
  [
    Nginx Proxy Manager,
    Hướng dẫn cài đặt Nginx Proxy Manager,
    Cấu hình Nginx Proxy Manager,
    Nginx Proxy Manager Docker,
  ]
image:
  path: /assets/img/nginx-proxy-manager-guide/nginxproxymanager.jpg
  width: 800
---
# Hướng Dẫn Cài Đặt & Sử Dụng Nginx Proxy Manager

## 1. Giới Thiệu

**Nginx Proxy Manager (NPM)** là một công cụ quản lý Nginx với giao diện web trực quan, giúp cấu hình **Reverse Proxy**, **SSL**, **chuyển hướng (Redirect)** và nhiều tính năng khác mà không cần chỉnh sửa file cấu hình Nginx thủ công.

---

## 2. Cài Đặt Nginx Proxy Manager với Docker

### 2.1. Yêu Cầu Trước Khi Cài Đặt

- Máy chủ hoặc VPS cài đặt sẵn **Docker** và **Docker Compose**.
- Hệ điều hành hỗ trợ: Ubuntu, Debian, CentOS, hoặc bất kỳ hệ thống nào có Docker.

### 2.2. Cài Đặt Docker và Docker Compose (Nếu chưa có)

**Cài đặt Docker:**

```sh
curl -fsSL https://get.docker.com | bash
```

**Cài đặt Docker Compose:**

```sh
sudo apt install docker-compose -y
```

---

## 3. Triển Khai Nginx Proxy Manager với Docker Compose

### 3.1. Tạo File `docker-compose.yml`

```yaml
version: '3.8'

services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    container_name: nginx_proxy_manager
    restart: unless-stopped
    ports:
      - "80:80"       # HTTP
      - "81:81"       # UI Dashboard
      - "443:443"     # HTTPS
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
    environment:
      DB_SQLITE_FILE: "/data/database.sqlite"
```

### 3.2. Khởi Chạy Nginx Proxy Manager

```sh
docker-compose up -d
```

- `-d`: Chạy dịch vụ dưới nền (detached mode).
- Kiểm tra trạng thái:
  ```sh
  docker ps
  ```

---

## 4. Truy Cập Giao Diện Quản Lý

Mở trình duyệt và truy cập:

```
http://<server-ip>:81
```

- **Tài khoản mặc định:**
  - **Email:** `admin@example.com`
  - **Password:** `changeme`
- Đăng nhập và đổi mật khẩu ngay sau lần đăng nhập đầu tiên.

---

## 5. Cấu Hình Reverse Proxy

### 5.1. Thêm Proxy Host Mới

1. Chọn **"Proxy Hosts"** → **"Add Proxy Host"**.
2. Nhập **Domain Name** (tên miền hoặc địa chỉ IP của server backend).
3. Nhập **Forward Hostname/IP** (ví dụ: `192.168.1.100` hoặc `localhost`).
4. Nhập **Forward Port** (ví dụ: `3000` nếu ứng dụng chạy trên cổng 3000).
5. Tick chọn **Block Common Exploits** để tăng bảo mật.
6. Nhấn **Save** để lưu.

### 5.2. Thiết Lập HTTPS với Let's Encrypt

1. Chuyển sang tab **SSL**.
2. Chọn **Request a new SSL Certificate**.
3. Tick chọn **Force SSL** để buộc sử dụng HTTPS.
4. Nhấn **Save** để lưu và cấp chứng chỉ.

---

## 6. Cấu Hình Redirect (Chuyển Hướng)

1. Chọn **"Redirect Hosts"** → **"Add Redirect Host"**.
2. Nhập **Source Domain** (địa chỉ nguồn).
3. Nhập **Destination URL** (địa chỉ đích).
4. Chọn **301 Permanent** hoặc **302 Temporary**.
5. Nhấn **Save**.

---

## 7. Giám Sát Logs và Quản Lý Container

### 7.1. Kiểm Tra Logs

```sh
docker logs -f nginx_proxy_manager
```

### 7.2. Dừng & Khởi Động Lại Container

```sh
docker-compose down    # Dừng và xóa container
docker-compose up -d   # Chạy lại container
```

### 7.3. Cập Nhật Nginx Proxy Manager

```sh
docker-compose pull
docker-compose up -d
```

---

## 8. So Sánh với Các Công Cụ Khác

| Công Cụ                 | Chức Năng Chính         | Hỗ Trợ SSL         | UI Quản Lý      |
| ----------------------- | ----------------------- | ------------------ | --------------- |
| **Nginx Proxy Manager** | Reverse Proxy, SSL      | ✅ Có Let's Encrypt | ✅ Giao diện web |
| **Nginx UI**            | Chỉnh sửa file cấu hình | ❌ Không có         | ⚠️ UI đơn giản  |

---

## 9. Kết Luận

Nginx Proxy Manager giúp quản lý Reverse Proxy và SSL dễ dàng qua giao diện web. Đây là lựa chọn lý tưởng cho những ai muốn:

- Thiết lập **Nginx Reverse Proxy** nhanh chóng.
- Quản lý SSL với **Let's Encrypt** dễ dàng.
- Tránh chỉnh sửa file cấu hình thủ công.

---

## 10. Tham Khảo

- [Trang chủ Nginx Proxy Manager](https://nginxproxymanager.com/)
- [Kho Docker Hub của Nginx Proxy Manager](https://hub.docker.com/r/jc21/nginx-proxy-manager)
- [Tài liệu chính thức về Docker Compose](https://docs.docker.com/compose/)
- [Let's Encrypt - Cấp chứng chỉ SSL miễn phí](https://letsencrypt.org/)

**Nếu bạn gặp lỗi trong quá trình cài đặt hoặc sử dụng, hãy kiểm tra logs hoặc đặt câu hỏi trong cộng đồng Docker & Nginx!**

