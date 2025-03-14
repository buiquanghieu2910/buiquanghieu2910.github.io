---
layout: post
title: Hướng Dẫn Chạy WordPress Bằng Docker
date: 2025-03-14 23:18 +0700
categories: [WordPress]
tags:
  [
    Docker WordPress,
    WordPress trên Docker,
    Cài đặt WordPress với Docker,
    docker-compose WordPress,
    MySQL WordPress,
  ]
image:
  path: /assets/img/huong-dan-chay-wordpress-bang-docker/docker_wordpress.jpg
  width: 800
---

# 🚀 Hướng Dẫn Chạy WordPress Bằng Docker

## 📝 Giới thiệu

Docker giúp triển khai WordPress nhanh chóng mà không cần cài đặt thủ công các thành phần như Apache, MySQL. Trong hướng dẫn này, chúng ta sẽ chạy WordPress trên Docker với cấu hình tối ưu.

---

## 📦 Cấu Hình `docker-compose.yml`

Dưới đây là tệp `docker-compose.yml` để chạy WordPress với MySQL:

```yaml
version: "3.7"
services:
  wordpress:
    image: wordpress:latest
    volumes:
      - ./uploads.ini:/usr/local/etc/php/conf.d/uploads.ini
      - ./server:/var/www/html
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: admin
      WORDPRESS_DB_PASSWORD: admin123
      WORDPRESS_DB_NAME: wordpress_db
      WORDPRESS_ADMIN_USER: admin
      WORDPRESS_ADMIN_PASSWORD: admin123
      WORDPRESS_ADMIN_EMAIL: admin@example.com
    depends_on:
      - db

  db:
    image: mysql:latest
    restart: always
    command: --default-authentication-plugin=mysql_native_password
    ports:
      - 3307:3306
    environment:
      MYSQL_DATABASE: wordpress_db
      MYSQL_USER: admin
      MYSQL_PASSWORD: admin123
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_ROOT_HOST: "%"
```

---

## 🔍 Phân Tích `docker-compose.yml`

### 1. `wordpress` Service:

- **image: wordpress:latest** → Sử dụng bản mới nhất của WordPress.
- **volumes:**
  - `./uploads.ini:/usr/local/etc/php/conf.d/uploads.ini` → Cấu hình PHP để tăng dung lượng upload.
  - `./server:/var/www/html` → Lưu trữ mã nguồn WordPress bên ngoài container.
- **ports:** `8080:80` → Truy cập WordPress qua `http://localhost:8080`.
- **environment:**
  - `WORDPRESS_DB_HOST: db` → Kết nối với database service có tên `db`.
  - `WORDPRESS_DB_USER: admin`, `WORDPRESS_DB_PASSWORD: admin123`, `WORDPRESS_DB_NAME: wordpress_db` → Thông tin kết nối database.
  - `WORDPRESS_ADMIN_USER: admin`, `WORDPRESS_ADMIN_PASSWORD: admin123` → Tài khoản admin WordPress.
- **depends_on: db** → Chờ database khởi động trước khi chạy WordPress.

### 2. `db` Service:

- **image: mysql:latest** → Sử dụng bản MySQL mới nhất.
- **restart: always** → Tự động khởi động lại nếu container gặp sự cố.
- **command:** `--default-authentication-plugin=mysql_native_password` → Dùng cơ chế xác thực tương thích với WordPress.
- **ports:** `3307:3306` → Mở cổng 3307 trên máy để truy cập database.
- **environment:**
  - `MYSQL_DATABASE: wordpress_db` → Tạo database `wordpress_db`.
  - `MYSQL_USER: admin`, `MYSQL_PASSWORD: admin123` → Tạo user quản lý database.
  - `MYSQL_ROOT_PASSWORD: root123` → Mật khẩu root của MySQL.
  - `MYSQL_ROOT_HOST: '%'` → Cho phép truy cập từ bất kỳ địa chỉ nào.

---

## 🔧 Cấu Hình PHP (`uploads.ini`)

Để tăng dung lượng tải lên, tạo tệp `uploads.ini`:

```ini
file_uploads = On
memory_limit = 512M
upload_max_filesize = 512M
post_max_size = 512M
max_execution_time = 600
```

---

## 🚀 Cách Chạy WordPress với Docker

1. **Tạo thư mục dự án:**
   ```bash
   mkdir wordpress-docker && cd wordpress-docker
   ```
2. **Tạo tệp `docker-compose.yml`** và `uploads.ini` theo cấu hình trên.
3. **Chạy Docker Compose:**
   ```bash
   docker-compose up -d
   ```
4. **Truy cập WordPress:**
   Mở trình duyệt và vào địa chỉ `http://localhost:8080` để bắt đầu cài đặt WordPress.

---

## 🎯 Ưu Điểm Khi Chạy WordPress Bằng Docker

✅ Dễ dàng thiết lập và chạy WordPress nhanh chóng.
✅ Môi trường cách ly, không ảnh hưởng đến hệ thống chính.
✅ Linh hoạt trong việc cấu hình và mở rộng.

Nếu bạn gặp lỗi, hãy kiểm tra logs bằng:

```bash
docker-compose logs -f
```

Chúc bạn triển khai WordPress thành công! 🚀
