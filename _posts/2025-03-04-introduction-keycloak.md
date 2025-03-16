---
layout: post
title: Giới thiệu Keycloak
date: 2025-03-04 02:54 +0700
categories: [Keycloak]
tags: [Keycloak, Giới thiệu Keycloak, Introduction Keycloak]
image:
  path: /assets/img/introduction-keycloak/Keycloak.png
  width: 800
---
# 🔐 Keycloak là gì?

**Keycloak** là một nền tảng quản lý danh tính và truy cập (**Identity and Access Management - IAM**) mã nguồn mở, được phát triển bởi **Red Hat**. Keycloak cung cấp các tính năng **xác thực**, **ủy quyền**, và **quản lý người dùng** mạnh mẽ, giúp các ứng dụng dễ dàng tích hợp cơ chế **đăng nhập một lần (Single Sign-On - SSO)** mà không cần phải tự xây dựng hệ thống xác thực riêng.

---

# 🚀 Các tính năng chính của Keycloak

## 1️⃣ **Single Sign-On (SSO)**
✔ Người dùng chỉ cần đăng nhập một lần để truy cập nhiều ứng dụng khác nhau.  
✔ Hỗ trợ đăng nhập qua các giao thức tiêu chuẩn như **OpenID Connect, OAuth 2.0, và SAML 2.0**.

## 2️⃣ **Quản lý người dùng**
✔ Cung cấp giao diện quản trị để quản lý **người dùng, nhóm, và vai trò**.  
✔ Hỗ trợ tích hợp với **LDAP và Active Directory**.

## 3️⃣ **Xác thực và ủy quyền**
✔ Hỗ trợ **xác thực hai yếu tố (2FA)** với nhiều phương thức như **OTP, WebAuthn**.  
✔ Hỗ trợ **chính sách truy cập** dựa trên **vai trò (RBAC)** và **thuộc tính (ABAC)**.

## 4️⃣ **Tích hợp mạng xã hội và đăng nhập bên thứ ba**
✔ Hỗ trợ đăng nhập qua **Google, Facebook, GitHub, Twitter, v.v.**  
✔ Cho phép đăng nhập bằng **tài khoản doanh nghiệp** thông qua **SAML hoặc OpenID Connect**.

## 5️⃣ **Quản lý phiên làm việc và đăng xuất toàn bộ (Single Logout - SLO)**
✔ Người dùng có thể **đăng xuất khỏi tất cả các ứng dụng cùng một lúc**.  
✔ Hỗ trợ **theo dõi phiên làm việc** và **buộc đăng xuất** khi cần.

## 6️⃣ **Tùy chỉnh và mở rộng**
✔ Cung cấp khả năng **tùy chỉnh giao diện** đăng nhập, đăng ký và xác thực.  
✔ Hỗ trợ viết các **extension** để mở rộng tính năng của Keycloak.

---

# 🏗 Kiến trúc của Keycloak

Keycloak có kiến trúc linh hoạt gồm các thành phần chính:

1. **🖥️ Keycloak Server** - Thành phần trung tâm xử lý xác thực, ủy quyền và quản lý phiên.
2. **⚙️ Admin Console** - Giao diện quản trị giúp quản lý người dùng, vai trò và cấu hình hệ thống.
3. **👤 Account Console** - Giao diện cho người dùng cuối quản lý tài khoản của họ.
4. **📦 Adapters** - Các thư viện giúp ứng dụng dễ dàng tích hợp với Keycloak thông qua các giao thức **OAuth 2.0, OpenID Connect, và SAML**.

---

# 🛠 Cách sử dụng Keycloak

## 1️⃣ **Cài đặt Keycloak**

🔹 Chạy trực tiếp bằng Java:
```bash
java -jar keycloak-<version>.jar start-dev
```

🔹 Cài đặt bằng Docker:
```bash
docker run -d --name keycloak \
  -p 8080:8080 \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=admin \
  quay.io/keycloak/keycloak:latest start-dev
```

## 2️⃣ **Truy cập giao diện quản trị**
Sau khi cài đặt, bạn có thể truy cập **Admin Console** tại:  
🌐 `http://localhost:8080/admin/`

## 3️⃣ **Tạo Realm và Client**
- **🗄️ Realm**: Môi trường quản lý người dùng riêng biệt.
- **🔑 Client**: Ứng dụng sẽ sử dụng Keycloak để xác thực.

## 4️⃣ **Tích hợp Keycloak vào ứng dụng**
- Sử dụng thư viện **`keycloak-js`** cho ứng dụng frontend.
- Sử dụng thư viện **`spring-boot-starter-keycloak`** cho ứng dụng backend.

---

# 🏆 Kết luận

**Keycloak** là một giải pháp **IAM** mạnh mẽ, giúp doanh nghiệp và nhà phát triển dễ dàng quản lý danh tính người dùng một cách **bảo mật và linh hoạt**. Với khả năng **tích hợp linh hoạt**, Keycloak đang trở thành lựa chọn phổ biến trong các hệ thống xác thực hiện đại.

📌 **Nếu bạn đang tìm kiếm một nền tảng IAM mạnh mẽ, Keycloak là một lựa chọn tuyệt vời!**


