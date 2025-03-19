---
layout: post
title: 🚀 Tổng Quan về GitLab
date: 2025-03-19 23:52 +0700
categories: [Git, GitLab]
tags:
  [
    GitLab,
    GitLab CI/CD,
    GitLab với Docker Compose,
    GitLab Docker Container,
    GitLab Container Registry,
  ]
image:
  path: /assets/img/gitlab-introduction/gitlab.png
  width: 800
---

## 1. 🏗️ GitLab là gì?

GitLab là một nền tảng DevOps cung cấp giải pháp quản lý mã nguồn và CI/CD toàn diện. GitLab giúp các nhóm phát triển phần mềm quản lý source code, kiểm thử, triển khai và bảo mật dự án hiệu quả.

### ✨ Tính năng chính của GitLab:

- **📌 Version Control**: Quản lý mã nguồn dựa trên Git.
- **⚙️ CI/CD**: Tích hợp và triển khai liên tục.
- **🐞 Issue Tracking**: Theo dõi và quản lý lỗi, nhiệm vụ.
- **📦 Container Registry**: Lưu trữ hình ảnh Docker.
- **🔐 Security & Compliance**: Đảm bảo bảo mật và tuân thủ quy trình DevOps.

## 2. 🖥️ Cách tạo GitLab trên Server

GitLab có thể được self-hosted trên server để quản lý mã nguồn nội bộ.

### 🛠️ Cài đặt GitLab trên Server Ubuntu:

```bash
sudo apt update && sudo apt install -y curl openssh-server ca-certificates tzdata perl
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
sudo apt install -y gitlab-ce
```

### 🚀 Cấu hình GitLab:

```bash
sudo gitlab-ctl reconfigure
```

Sau đó, truy cập `http://<server-ip>` để thiết lập GitLab.

## 3. 🐳 Cách dùng Docker để tạo GitLab

Nếu không muốn cài đặt trực tiếp, bạn có thể sử dụng Docker để chạy GitLab.

### 🏗️ Cài đặt Docker và chạy GitLab:

```bash
sudo apt update && sudo apt install -y docker.io docker-compose
mkdir -p ~/gitlab/config ~/gitlab/logs ~/gitlab/data
```

### 📄 Tạo `docker-compose.yml`:

```yaml
version: "3"
services:
  gitlab:
    image: gitlab/gitlab-ce:latest
    container_name: gitlab
    restart: always
    hostname: "gitlab.local"
    environment:
      GITLAB_OMNIBUS_CONFIG: "external_url 'http://localhost'"
    ports:
      - "80:80"
      - "443:443"
      - "22:22"
    volumes:
      - ~/gitlab/config:/etc/gitlab
      - ~/gitlab/logs:/var/log/gitlab
      - ~/gitlab/data:/var/opt/gitlab
```

### 🚀 Chạy GitLab với Docker:

```bash
docker-compose up -d
```

Sau đó, truy cập `http://localhost` để thiết lập GitLab.

## 4. 🎯 Cách sử dụng GitLab

### 4.1. 🏁 Khởi tạo Repository trên GitLab:

```bash
git init
git remote add origin https://gitlab.com/your-username/repository-name.git
```

### 4.2. 📤 Đẩy mã nguồn lên GitLab:

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 4.3. 📥 Clone Repository từ GitLab:

```bash
git clone https://gitlab.com/your-username/repository-name.git
```

## 5. 📦 Sử dụng GitLab Container Registry

GitLab Container Registry là một giải pháp tích hợp giúp lưu trữ và quản lý hình ảnh Docker.

### 5.1. 🔑 Đăng nhập GitLab Container Registry:

```bash
docker login registry.gitlab.com -u YOUR_GITLAB_USERNAME --password-stdin
```

### 5.2. 🏷️ Gán thẻ cho hình ảnh Docker:

```bash
docker tag my-app registry.gitlab.com/YOUR_GITLAB_USERNAME/my-app:latest
```

### 5.3. 📤 Đẩy hình ảnh lên GitLab Container Registry:

```bash
docker push registry.gitlab.com/YOUR_GITLAB_USERNAME/my-app:latest
```

### 5.4. 📥 Kéo hình ảnh từ GitLab Container Registry:

```bash
docker pull registry.gitlab.com/YOUR_GITLAB_USERNAME/my-app:latest
```

## 🎉 Kết luận

GitLab là một nền tảng DevOps mạnh mẽ, cung cấp khả năng self-hosted, tích hợp CI/CD và Container Registry. Nếu bạn muốn quản lý mã nguồn nội bộ hoặc triển khai một hệ thống DevOps toàn diện, GitLab là một lựa chọn lý tưởng.
