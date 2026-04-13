---
layout: post
title: "🔐 Identity Service - Nền tảng IAM tập trung cho doanh nghiệp"
date: 2026-04-14 01:40 +0700
categories: [Product]
tags:
  [
    Identity Service,
    IAM,
    SSO,
    OAuth2,
    OIDC,
    Spring Boot,
    Vue 3,
    Redis,
    PostgreSQL,
    Security Platform,
  ]
---

## 🧭 Nền tảng IAM tập trung thể hiện năng lực xây dựng sản phẩm bảo mật ở quy mô doanh nghiệp

## 1) 🎯 Sản phẩm này giải quyết vấn đề gì?

**Identity Service** giải quyết bài toán cốt lõi của các hệ thống nhiều ứng dụng:
- Đăng nhập tập trung (SSO)
- Quản trị quyền truy cập theo mô hình nghiệp vụ
- Đồng bộ quyền nhanh và nhất quán giữa các dịch vụ

Đây là nhóm bài toán khó, vừa cần chuẩn bảo mật, vừa cần kiến trúc linh hoạt cho nhiều đội phát triển.

## 2) ✨ Điểm nổi bật về tính năng

- Đăng nhập OAuth2/OIDC theo Authorization Code + PKCE
- Quản trị tập trung: Application, User, Role, Group, Resource, Scope, Permission
- Permission Matrix phục vụ authorize ở hệ thống downstream
- Cache quyền bằng Redis + cơ chế versioning để đảm bảo nhất quán
- Revoke session khi đổi phân quyền để quyền mới có hiệu lực ngay
- Cấu hình Identity Provider (Google SSO)
- Bảo vệ admin API theo membership ứng dụng

## 3) 💎 Giá trị cốt lõi của sản phẩm

- **Tập trung hóa bảo mật**: mọi ứng dụng dùng chung một chuẩn định danh và phân quyền.
- **Linh hoạt theo nghiệp vụ**: mô hình phân quyền bám sát domain thực tế của doanh nghiệp.
- **Hiệu năng trong vận hành**: tối ưu đọc quyền với Redis cache và chiến lược invalidation rõ ràng.
- **Mở rộng bền vững**: kiến trúc module hóa giúp thêm ứng dụng mới mà không phá vỡ hệ thống cũ.
- **Khả năng kiểm soát cao**: hỗ trợ audit, revoke, và quản lý session ở mức toàn nền tảng.

## 4) 🚀 Các tính năng hay, tạo khác biệt

1. **Permission Matrix theo từng ứng dụng**  
Cho phép downstream service kiểm tra quyền theo `clientId` nhanh và rõ ràng.

2. **Claim `app_client_hashes` trong access token**  
Giúp backend xác thực membership ứng dụng mà không cần gọi IAM cho mọi request.

3. **Cơ chế đồng bộ quyền gần thời gian thực**  
Khi role/group/permission thay đổi, cache được invalidate và session có thể bị revoke ngay.

4. **Chính sách đăng nhập theo từng application**  
Mỗi ứng dụng có thể bật/tắt độc lập: user/password, Google login, self-registration.

5. **Bảng điều khiển quản trị đầy đủ**  
Từ quản lý ứng dụng đến users/roles/groups/resources/scopes/permissions đều có UI vận hành trực tiếp.

## 5) 🛠️ Năng lực công nghệ thể hiện qua sản phẩm

### ⚙️ Backend

- **Java + Spring Boot + Spring Authorization Server**
- Thiết kế API quản trị IAM rõ domain
- Tùy biến JWT claims (`app_client_hashes`) cho kiểm tra quyền nhanh
- Tích hợp PostgreSQL (dữ liệu nghiệp vụ) + Redis (tối ưu hiệu năng)

### 🎨 Frontend

- **Vue 3 + Vite + PrimeVue**
- Màn hình quản trị đầy đủ cho vận hành IAM hằng ngày
- Router theo module, tổ chức UI theo luồng nghiệp vụ rõ ràng
- Hỗ trợ đa ngôn ngữ (i18n)

### 🧱 Kỹ thuật hệ thống

- Luồng token rõ ràng: cấp mới, refresh, introspect, revoke
- Kiểm soát session toàn hệ thống và theo từng application
- Tách lớp service/repository/component/filter cho khả năng mở rộng tốt

## 6) 🧑‍💼 Giá trị với nhà tuyển dụng

Sản phẩm này cho thấy ứng viên/đội ngũ có khả năng:
- Thiết kế kiến trúc sản phẩm ở mức platform
- Làm chủ cả backend bảo mật lẫn frontend quản trị
- Tư duy domain-driven cho mô hình phân quyền phức tạp
- Tối ưu hiệu năng và tính nhất quán dữ liệu trong hệ phân tán
- Xây dựng giải pháp có thể đưa vào vận hành thực tế, không chỉ dừng ở demo kỹ thuật

## 7) 🖼️ Hình ảnh sản phẩm

### 🔐 Đăng nhập SSO
![Đăng nhập](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/login-page.png)

### 📦 Quản lý ứng dụng
![Quản lý ứng dụng](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/applications.png)

### ⚙️ Cài đặt chi tiết ứng dụng
![Cài đặt ứng dụng](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/application-settings.png)

### 🛡️ Quản lý phân quyền theo Permission
![Quản lý permission](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/application-authorization-permissions.png)

### 👥 Quản lý người dùng
![Quản lý người dùng](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/users.png)

### 📊 Chi tiết người dùng và Permission Matrix
![Chi tiết người dùng](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/user-detail.png)

### 🧾 Quản lý phiên đăng nhập
![Quản lý phiên](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/sessions.png)

### 🌐 Cấu hình nhà cung cấp định danh
![Nhà cung cấp định danh](/assets/img/identity-service-nen-tang-iam-tap-trung-cho-doanh-nghiep/pitch/identity-providers.png)

## 8) ⚖️ So sánh định vị sản phẩm (ngắn gọn)

- **So với Keycloak**: Identity Service tập trung vào bài toán nghiệp vụ nội bộ cụ thể, dễ may đo theo quy trình doanh nghiệp.
- **So với IdentityServer (.NET)**: Identity Service là sản phẩm đã có sẵn màn hình quản trị nghiệp vụ, giảm effort tự xây từ đầu.

---

## ✅ Thông điệp chốt cho hồ sơ ứng tuyển

**Identity Service là minh chứng cho năng lực xây dựng một sản phẩm platform bảo mật end-to-end: đúng chuẩn, đúng nghiệp vụ, và sẵn sàng vận hành ở môi trường nhiều ứng dụng.**

