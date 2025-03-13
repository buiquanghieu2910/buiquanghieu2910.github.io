---
layout: post
title: Hướng Dẫn Cơ Bản Về Docker
date: 2025-03-13 20:33 +0700
categories: [Docker]
tags:
  [
    Docker,
    Container,
    DevOps,
    Docker Compose,
    Virtualization,
    Microservices,
    Image,
    Deployment,
  ]
image:
  path: /assets/img/docker-guide/docker.png
  width: 800
---
# 🐳 Hướng Dẫn Chi Tiết Về Docker

## 🔹 1. Docker là gì?
Docker là một nền tảng **mã nguồn mở** giúp đóng gói, phân phối và chạy ứng dụng trong các **container**. Nó đảm bảo ứng dụng chạy nhất quán trên nhiều môi trường khác nhau, từ máy tính cá nhân đến máy chủ sản xuất.

## 🎯 2. Lợi ích của Docker
✅ **Di động**: Chạy ứng dụng trên bất kỳ môi trường nào mà không lo lắng về cấu hình.
✅ **Nhẹ**: Tiêu thụ ít tài nguyên hơn so với máy ảo (VM).
✅ **Cô lập**: Các container hoạt động độc lập, tránh xung đột giữa ứng dụng.
✅ **Dễ mở rộng**: Dễ dàng mở rộng ứng dụng với nhiều container.
✅ **Tự động hóa**: Quản lý nhiều container bằng Docker Compose hoặc Kubernetes.

## ⚙️ 3. Cài đặt Docker
### 🖥️ Windows / MacOS
📥 Tải và cài đặt [Docker Desktop](https://www.docker.com/products/docker-desktop/).

### 🐧 Linux (Ubuntu)
Chạy các lệnh sau:
```sh
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable --now docker
```
📌 Kiểm tra Docker đã cài đặt thành công chưa:
```sh
docker --version
```

## 🚀 4. Các Lệnh Cơ Bản Trong Docker
### 📌 Kiểm tra phiên bản Docker
```sh
docker version
```

### 🏗️ Chạy container từ một image
```sh
docker run hello-world
```

### 📜 Liệt kê các container đang chạy
```sh
docker ps
```

### 📜 Liệt kê tất cả container (bao gồm cả container đã dừng)
```sh
docker ps -a
```

### ⏹️ Dừng một container
```sh
docker stop <container_id>
```

### ❌ Xóa một container
```sh
docker rm <container_id>
```

### 🧹 Xóa tất cả container đã dừng
```sh
docker container prune
```

### ⬇️ Tải một image từ Docker Hub
```sh
docker pull nginx
```

### 🗑️ Xóa một image
```sh
docker rmi <image_id>
```

### 🏗️ Xây dựng image từ Dockerfile
```sh
docker build -t my-app .
```

### 🔄 Chạy container với cổng tùy chỉnh
```sh
docker run -d -p 8080:80 nginx
```

## 🛠️ 5. Docker Compose - Quản Lý Nhiều Container
Docker Compose giúp bạn quản lý nhiều container thông qua file `docker-compose.yml`.

### 🔧 Cài đặt Docker Compose
```sh
sudo apt install docker-compose -y
```

### 📄 Ví dụ file `docker-compose.yml`
```yaml
version: '3.8'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

### ▶️ Chạy ứng dụng với Docker Compose
```sh
docker-compose up -d
```

### ⏹️ Dừng ứng dụng
```sh
docker-compose down
```

## 🔍 6. Kiểm tra logs container
Trong quá trình chạy container, nếu có lỗi xảy ra, bạn có thể kiểm tra logs bằng lệnh:
```sh
docker logs <container_id>
```

## 🎯 7. Kết Luận
Docker giúp đơn giản hóa việc triển khai và quản lý ứng dụng. Bằng cách sử dụng container, bạn có thể dễ dàng chạy ứng dụng trên mọi nền tảng mà không cần lo lắng về sự khác biệt giữa các môi trường.

🔹 **Mẹo hữu ích**: Sử dụng `docker inspect <container_id>` để xem chi tiết container. 🚀
