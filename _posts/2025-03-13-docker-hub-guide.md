---
layout: post
title: 🐳 Hướng Dẫn Sử Dụng Docker Hub
date: 2025-03-13 20:44 +0700
categories: [Docker]
tags:
  [
    Docker Hub,
    Push image Docker,
    Pull image Docker,
    Docker registry,
    Docker image repository,
  ]
image:
  path: /assets/img/docker-hub-guide/docker-hub.jpg
  width: 800
---
## 🌍 1. Docker Hub là gì?
Docker Hub là một kho lưu trữ trực tuyến dành cho các image Docker. Nó giúp bạn lưu trữ, chia sẻ và quản lý các image container dễ dàng. 

🔹 **Tính năng chính của Docker Hub:**
###### ✅ Lưu trữ image công khai và riêng tư.
###### ✅ Hỗ trợ CI/CD để tự động build và push image.
###### ✅ Cho phép cộng đồng đóng góp và sử dụng image có sẵn.

## 🛠️ 2. Đăng ký và Đăng nhập Docker Hub

### 📌 Đăng ký tài khoản Docker Hub
Truy cập [Docker Hub](https://hub.docker.com/) và tạo tài khoản miễn phí.

### 🔑 Đăng nhập vào Docker Hub từ Terminal
Sau khi có tài khoản, đăng nhập vào Docker Hub bằng lệnh:
```sh
docker login
```
Nhập **username** và **password** khi được yêu cầu.

## 📤 3. Đẩy Image Lên Docker Hub

### 🏗️ Bước 1: Tạo một Image Docker
Giả sử bạn có một Dockerfile trong thư mục dự án, bạn có thể build image bằng lệnh:
```sh
docker build -t my-app .
```

### 🏷️ Bước 2: Gán tag cho image
Docker Hub yêu cầu image có định danh bao gồm tên người dùng của bạn. Gán tag bằng lệnh:
```sh
docker tag my-app <your-dockerhub-username>/my-app:latest
```

### 📤 Bước 3: Push image lên Docker Hub
```sh
docker push <your-dockerhub-username>/my-app:latest
```
Sau khi push xong, image sẽ xuất hiện trong kho Docker Hub của bạn.

## ⬇️ 4. Tải Image Từ Docker Hub
Để tải image từ Docker Hub về máy, sử dụng lệnh:
```sh
docker pull <your-dockerhub-username>/my-app:latest
```
Sau khi tải xong, bạn có thể chạy container từ image này:
```sh
docker run -d -p 8080:80 <your-dockerhub-username>/my-app:latest
```

## 🗑️ 5. Xóa Image Trên Docker Hub
Nếu bạn muốn xóa một image khỏi Docker Hub, bạn cần:
###### 1️⃣ Truy cập [Docker Hub](https://hub.docker.com/).
###### 2️⃣ Tìm image cần xóa.
###### 3️⃣ Chọn **Settings > Delete Repository**.

## 🎯 6. Kết Luận
Docker Hub là một công cụ mạnh mẽ giúp lưu trữ và chia sẻ image Docker dễ dàng. Việc push và pull image từ Docker Hub giúp bạn triển khai ứng dụng nhanh chóng và tiện lợi.

🚀 **Mẹo hữu ích:** Nếu bạn làm việc trong nhóm, hãy cân nhắc sử dụng **private repository** hoặc **Docker Organization** để quản lý image tốt hơn!
