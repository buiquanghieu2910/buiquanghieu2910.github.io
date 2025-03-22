---
layout: post
title: 🌐 NginX là gì? Hướng dẫn cơ bản về cấu hình và thuật ngữ thường gặp
date: 2025-03-23 04:45 +0700
categories: [DevOps]
tags:
  [
    NginX là gì,
    Cấu hình NginX cơ bản,
    NginX reverse proxy,
    Hướng dẫn dùng NginX,
    Cài đặt NginX Ubuntu,
  ]
image:
  path: /assets/img/nginx-la-gi-va-cau-hinh-co-ban/nginx.jpg
---

## 🎯 NginX là gì?
**NginX** là một **web server mã nguồn mở** nổi tiếng, thường được dùng làm:
- Web server tĩnh (static file server)
- Reverse proxy
- Load balancer
- API gateway

NginX được đánh giá cao vì:
- ✅ Hiệu năng cao
- ✅ Xử lý đồng thời hàng nghìn kết nối
- ✅ Dễ cấu hình, nhẹ, phù hợp cả cho hệ thống nhỏ lẫn lớn

---

## 🔍 Một số thuật ngữ quan trọng

| Thuật ngữ       | Ý nghĩa |
|-----------------|---------|
| **Reverse Proxy** | Trung gian giữa client và server nội bộ (ẩn backend) |
| **Load Balancing** | Phân phối traffic đến nhiều server backend |
| **Upstream**     | Nhóm các backend server mà NginX sẽ chuyển tiếp request đến |
| **Server Block** | Tương đương Virtual Host – cấu hình cho mỗi website/domain |
| **Location Block** | Quy định xử lý URL cụ thể trong server |
| **Static File**  | File tĩnh (HTML, CSS, JS, ảnh...) mà NginX có thể trả về trực tiếp |

---

## 📂 Cấu trúc thư mục NginX (Ubuntu/Debian)
```
/etc/nginx/
├── nginx.conf         # File cấu hình chính
├── sites-available/   # Chứa các server block riêng biệt
├── sites-enabled/     # Nơi chứa symbolic link để kích hoạt site
└── conf.d/            # Nơi đặt các file config bổ sung
```

---

## ⚙️ Ví dụ cấu hình NginX đơn giản
```nginx
server {
    listen 80;
    server_name example.com;

    root /var/www/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
✅ Đây là cấu hình web server cơ bản:
- Lắng nghe cổng 80
- Trả về file tĩnh từ `/var/www/html`
- Nếu không tìm thấy file → trả về lỗi 404

---

## 🔁 Reverse Proxy NginX
```nginx
server {
    listen 80;
    server_name api.example.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
✅ Dùng để chuyển tiếp request từ NginX đến ứng dụng Node.js đang chạy port 3000.

---

## 🔀 Load Balancer đơn giản với NginX
```nginx
upstream backend {
    server 127.0.0.1:3000;
    server 127.0.0.1:3001;
}

server {
    listen 80;
    server_name myapp.com;

    location / {
        proxy_pass http://backend;
    }
}
```
✅ Cân bằng tải giữa 2 server backend trên cùng máy.

---

## 📌 Một số lệnh hữu ích
```bash
sudo nginx -t        # Kiểm tra cấu hình có lỗi không
sudo systemctl restart nginx   # Khởi động lại dịch vụ NginX
sudo systemctl status nginx    # Kiểm tra trạng thái
sudo ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/  # Bật site
```

---

## 🧠 Tổng kết
- **NginX** là công cụ cực kỳ mạnh mẽ cho cả front-end lẫn back-end.
- Cấu hình đơn giản nhưng rất linh hoạt để triển khai:
  - Web server tĩnh
  - Reverse proxy cho backend (Node.js, PHP, Python...)
  - Load balancer cho các hệ thống lớn

🚀 **Dù bạn làm Dev, DevOps hay sysadmin – NginX là kỹ năng không thể thiếu!**