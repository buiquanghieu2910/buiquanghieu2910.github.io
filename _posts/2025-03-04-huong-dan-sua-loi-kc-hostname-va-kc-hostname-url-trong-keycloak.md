---
layout: post
title: 🔧Hướng Dẫn Sửa Lỗi KC_HOSTNAME và KC_HOSTNAME_URL trong Keycloak
date: 2025-03-04 02:28 +0700
categories: [Keycloak]
tags: [Keycloak, KC_HOSTNAME, KC_HOSTNAME_URL]
---
## 🛑 **1. Mô Tả Lỗi**
Khi chạy Keycloak với Docker, bạn có thể gặp lỗi sau:

```sh
ERROR: Failed to start quarkus
ERROR: You can not set both 'hostname' and 'hostname-url' options
```

❌ **Lỗi này xảy ra do Keycloak không cho phép cấu hình đồng thời** `KC_HOSTNAME` và `KC_HOSTNAME_URL`.

---

## 🛠 **2. Cách Khắc Phục**

### 🔹 **Cách 1: Chỉ sử dụng `KC_HOSTNAME_URL`** (✅ **Khuyến nghị**)
Cách tốt nhất là **chỉ sử dụng `KC_HOSTNAME_URL`** và bỏ `KC_HOSTNAME`.

✅ **Cấu hình đúng:**

```yaml
services:
  keycloak:
    image: quay.io/keycloak/keycloak:24.0.2
    container_name: sso-keycloak
    environment:
      KC_HOSTNAME_URL: "https://domain.com"
      KC_HOSTNAME_ADMIN_URL: "https://domain.com"
```

📌 **Khi nào dùng?**
👉 Nếu bạn muốn Keycloak **luôn sử dụng HTTPS**, hãy dùng `KC_HOSTNAME_URL`.

---

### 🔹 **Cách 2: Chỉ sử dụng `KC_HOSTNAME`**
Nếu Keycloak được chạy phía sau **Nginx hoặc Proxy**, bạn có thể chỉ dùng `KC_HOSTNAME`.

✅ **Cấu hình đúng:**

```yaml
services:
  keycloak:
    image: quay.io/keycloak/keycloak:24.0.2
    container_name: sso-keycloak
    environment:
      KC_HOSTNAME: "domain.com"
```

📌 **Khi nào dùng?**
👉 Nếu bạn có **Nginx hoặc Reverse Proxy** đảm nhận HTTPS, hãy dùng `KC_HOSTNAME`.

---

## 🔄 **3. Khởi Động Lại Keycloak**
Sau khi chỉnh sửa cấu hình, chạy lại Keycloak:

```sh
docker-compose down
docker-compose up -d
```

✅ **Bây giờ, Keycloak sẽ khởi động mà không bị lỗi!** 🚀