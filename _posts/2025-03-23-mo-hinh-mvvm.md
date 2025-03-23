---
layout: post
title: 🧭 Mô Hình MVVM (Model - View - ViewModel)
date: 2025-03-23 17:14 +0700
tags:
  [
    mô hình MVVM,
    MVVM là gì,
    kiến trúc MVVM,
    MVVM pattern,
  ]
image:
  path: /assets/img/mo-hinh-mvvm/mvvm.jpg
---

## 📝 Giới thiệu

**MVVM** là viết tắt của **Model - View - ViewModel**, một mô hình kiến trúc phần mềm hiện đại, thường được sử dụng trong phát triển **ứng dụng frontend**, đặc biệt với các framework như **React**, **Vue**, **Angular**, **WPF**, **Flutter**, v.v.

Mục tiêu chính của MVVM là **tách biệt rõ ràng** giữa giao diện người dùng (UI), logic xử lý và dữ liệu, đồng thời hỗ trợ **binding hai chiều (two-way binding)** giữa View và ViewModel.

---

## 🔍 Thành phần trong MVVM

### 1. 🧮 Model – Dữ liệu & Nghiệp vụ

- Đại diện cho dữ liệu, trạng thái và các logic nghiệp vụ.
- Là phần "backend" của ứng dụng frontend.
- Có thể tương tác với API, cơ sở dữ liệu hoặc các service khác.

📌 *Ví dụ:* Danh sách sản phẩm, thông tin người dùng, xử lý giỏ hàng...

---

### 2. 🖼️ View – Giao diện người dùng

- Là phần hiển thị dữ liệu cho người dùng.
- Không chứa logic xử lý nghiệp vụ.
- Thường là HTML, JSX, XML UI (tuỳ framework).

📌 *Ví dụ:* Giao diện form, danh sách sản phẩm, bảng hiển thị dữ liệu.

---

### 3. 🔁 ViewModel – Bộ trung gian thông minh

- Kết nối View với Model.
- Chứa logic giao tiếp, validate, xử lý trạng thái.
- Tự động cập nhật View khi Model thay đổi (và ngược lại).

📌 *Ví dụ:* Xử lý form nhập liệu, binding dữ liệu vào UI, gọi API từ ViewModel.

---

## 🔄 Luồng hoạt động MVVM
👁️ View ⟷ 🧠 ViewModel ⟷ 🧮 Model

### Giải thích:

1. Người dùng tương tác với **View** (UI).
2. **ViewModel** tiếp nhận sự kiện và gọi **Model** để xử lý dữ liệu.
3. Khi dữ liệu thay đổi, **ViewModel** cập nhật lại **View** (và ngược lại nếu có two-way binding).

---

## 🧠 Ưu điểm của MVVM

✅ **Tách biệt giao diện và logic xử lý**  
✅ **Two-way binding** giúp cập nhật dữ liệu tự động  
✅ **Dễ test unit ViewModel** mà không phụ thuộc giao diện  
✅ **Tái sử dụng ViewModel ở nhiều View khác nhau**

---

## ⚠️ Nhược điểm

❌ Phức tạp khi ứng dụng nhỏ hoặc không cần binding hai chiều  
❌ ViewModel có thể trở nên nặng nếu xử lý quá nhiều logic  
❌ Cần framework hỗ trợ tốt để triển khai hiệu quả (Vue, Angular, Knockout, v.v.)

---

## 📦 MVVM phù hợp với công nghệ nào?

| Công nghệ / Framework | Hỗ trợ MVVM |
|------------------------|-------------|
| Vue.js                 | ✅          |
| Angular                | ✅          |
| WPF (.NET)             | ✅          |
| React (hook/state)     | ⚠️ Gián tiếp |
| Flutter (Provider, Bloc) | ✅        |
| Knockout.js            | ✅          |

---

## 🌐 Ví dụ thực tế: Form thêm người dùng

- **Model:** chứa cấu trúc `User` (tên, email, tuổi...) và logic gọi API tạo người dùng.
- **View:** là giao diện nhập form gồm các trường thông tin.
- **ViewModel:** chứa các hàm validate, binding dữ liệu giữa Model và View, xử lý submit và hiển thị trạng thái loading, lỗi, thành công.

---

## 🏁 Kết luận

Mô hình **MVVM** giúp việc phát triển giao diện người dùng trở nên **hiện đại, linh hoạt** và dễ quản lý hơn, đặc biệt khi làm việc với các ứng dụng có **tương tác phức tạp**. Tuy nhiên, để triển khai hiệu quả, bạn cần chọn đúng framework hoặc thư viện phù hợp.

---

**Tác giả:** [Tên của bạn]  
**Ngày viết:** 23/03/2025
