---
layout: post
title: 🚫 Fix lỗi 413 Request Entity Too Large khi upload file với NginX
date: 2025-03-23 05:04 +0700
categories: [DevOps]
tags:
  [
    413 Request Entity Too Large,
    NginX upload file bị lỗi,
    client_max_body_size NginX,
    Fix lỗi upload lớn NginX,
    Cấu hình NginX tăng giới hạn file,
  ]
image:
  path: /assets/img/fix-413-request-entity-too-large-nginx/nginx-413-request-entity-too-large-error.jpg
---

## ❗ Vấn đề
Khi người dùng upload file lớn qua form (HTML, API...), NginX có thể trả về lỗi:
```
413 Request Entity Too Large
```

Đây là lỗi phổ biến do **giới hạn dung lượng file mặc định mà NginX cho phép trong request**. Mặc định, giới hạn là 1MB.

---

## 🛠 Cách khắc phục lỗi 413 trong NginX

### 🔧 Bước 1: Thêm hoặc chỉnh lại `client_max_body_size`
Mở file cấu hình NginX:
```bash
sudo nano /etc/nginx/nginx.conf
```

Thêm hoặc sửa dòng sau trong block `http {}`, `server {}` hoặc `location {}`:
```nginx
http {
    ...
    client_max_body_size 50M;
}
```
Hoặc nếu bạn chỉ muốn áp dụng cho 1 server/domain cụ thể:
```nginx
server {
    listen 80;
    server_name example.com;

    client_max_body_size 50M;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### 📂 Nếu bạn dùng cấu hình riêng trong `conf.d/`, `sites-available/`
Thêm `client_max_body_size` vào đúng block `server {}` hoặc `location {}` bạn đang cấu hình.

---

### 🔁 Bước 2: Kiểm tra và restart lại NginX
```bash
sudo nginx -t          # Kiểm tra cấu hình
sudo systemctl reload nginx   # Reload NginX không gián đoạn
```

Nếu bạn muốn chắc chắn, có thể restart hẳn:
```bash
sudo systemctl restart nginx
```

---

## ✅ Kiểm tra lại
- Upload lại file từ frontend hoặc Postman
- Kiểm tra trình duyệt/log nếu lỗi vẫn còn
- Nếu phía backend (PHP, Node, v.v.) có giới hạn upload riêng → kiểm tra thêm config backend

---

## 🧠 Một số lưu ý bổ sung
- Nếu dùng **NginX làm reverse proxy**, hãy đặt `client_max_body_size` trong block proxy:
```nginx
location /api/ {
    client_max_body_size 100M;
    proxy_pass http://localhost:3000;
}
```

- Nếu dùng **PHP**, kiểm tra thêm file `php.ini`:
```ini
upload_max_filesize = 50M
post_max_size = 50M
```

---

## 🔗 Tham khảo
- [StackOverflow: 413 Request Entity Too Large Issue](https://stackoverflow.com/questions/24306335/413-request-entity-too-large-file-upload-issue){:target="_blank"}
- [Tài liệu chính thức NginX](https://nginx.org/en/docs/http/ngx_http_core_module.html#client_max_body_size){:target="_blank"}

---

## ✅ Tổng kết

| Vấn đề               | Nguyên nhân                      | Cách xử lý                           |
|----------------------|----------------------------------|--------------------------------------|
| 413 Request Entity Too Large | File vượt quá giới hạn mặc định | Sửa `client_max_body_size` trong NginX |

🚀 Sau khi chỉnh `client_max_body_size`, bạn có thể upload file lớn hơn mà không gặp lỗi 413 nữa!

---