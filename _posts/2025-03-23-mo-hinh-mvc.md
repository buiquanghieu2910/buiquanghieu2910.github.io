---
layout: post
title: 📐 Mô Hình MVC (Model-View-Controller)
date: 2025-03-23 15:39 +0700
categories: [Design Pattern]
tags:
  [
    mô hình mvc,
    mvc là gì,
    kiến trúc mvc,
    cấu trúc mvc,
    mvc pattern,
    ứng dụng mô hình mvc,
    ưu điểm mvc,
    ví dụ mvc,
  ]
image:
  path: /assets/img/mo-hinh-mvc/mvc.jpg
---

## 📝 Giới thiệu

**MVC** là một mẫu thiết kế phần mềm phổ biến trong phát triển ứng dụng, đặc biệt là web.  
Mục tiêu của mô hình này là **tách biệt rõ ràng** giữa các thành phần của ứng dụng để dễ dàng **quản lý, bảo trì và mở rộng**.

### 🔍 MVC gồm 3 thành phần chính:

- **🧮 Model (M)** – Quản lý dữ liệu và logic nghiệp vụ.
- **🖼️ View (V)** – Hiển thị giao diện người dùng, nhận dữ liệu từ Model.
- **🎮 Controller (C)** – Điều phối giữa Model và View, xử lý yêu cầu người dùng.

---

## ⚙️ Cấu trúc chi tiết

### 1. 📊 Model – Dữ liệu & Nghiệp vụ

- Quản lý dữ liệu, xử lý logic.
- Giao tiếp với cơ sở dữ liệu hoặc dịch vụ bên ngoài.
- Không xử lý giao diện hay đầu vào người dùng.

📌 _Ví dụ:_ Truy vấn danh sách sản phẩm từ database.

---

### 2. 🖼️ View – Giao diện người dùng

- Hiển thị dữ liệu từ Model.
- Không can thiệp xử lý logic nghiệp vụ.
- Cập nhật giao diện khi dữ liệu thay đổi.

📌 _Ví dụ:_ HTML, JSX, template EJS hiển thị danh sách sản phẩm.

---

### 3. 🎮 Controller – Bộ điều khiển

- Nhận và xử lý yêu cầu từ người dùng (HTTP Request).
- Gọi Model xử lý, sau đó cập nhật View.
- Kết nối giữa View và Model.

📌 _Ví dụ:_ Khi người dùng bấm "Thêm sản phẩm", Controller tiếp nhận dữ liệu, lưu vào Model rồi yêu cầu View cập nhật lại danh sách.

---

## 🔄 Sơ đồ hoạt động

👁️ View ⟷ 🎮 Controller ⟷ 🧮 Model

1. Người dùng tương tác với **View**
2. **Controller** tiếp nhận sự kiện và xử lý
3. **Model** thực hiện thao tác dữ liệu
4. Kết quả trả về View để hiển thị cho người dùng

---

## 🚀 Lợi ích của mô hình MVC

✅ **Tách biệt rõ ràng** giữa UI và logic  
✅ **Dễ bảo trì** và nâng cấp từng phần riêng biệt  
✅ **Tăng khả năng tái sử dụng mã** (Reuse)  
✅ **Hỗ trợ teamwork hiệu quả**  
✅ **Dễ kiểm thử** từng thành phần riêng lẻ

---

## 🤔 Khi nào nên dùng MVC?

- Khi xây dựng **ứng dụng web có giao diện phức tạp**
- Khi cần **mở rộng hệ thống trong tương lai**
- Khi muốn **tối ưu quy trình phát triển theo nhóm**

---

## 🌐 Ví dụ thực tế: App quản lý công việc (To-do list)

- **Model:** Chứa dữ liệu các "task" và logic thêm/sửa/xóa.
- **View:** Giao diện hiển thị danh sách công việc và nút thao tác.
- **Controller:** Xử lý sự kiện thêm công việc, gửi dữ liệu cho Model và View.

---

## 🛠️ Một số framework hỗ trợ MVC

| Framework         | Ngôn ngữ   |
| ----------------- | ---------- |
| Laravel           | PHP        |
| Spring Boot       | Java       |
| ASP.NET MVC       | C#         |
| Express (Node.js) | JavaScript |
| Ruby on Rails     | Ruby       |

---

## 🏁 Kết luận

> **MVC** là một kiến trúc mạnh mẽ, giúp cho ứng dụng trở nên **dễ phát triển**, **dễ bảo trì** và **chuyên nghiệp** hơn.

Dù mô hình này có thể **rườm rà với ứng dụng nhỏ**, nhưng với các ứng dụng lớn, MVC thực sự là một lựa chọn tối ưu 💪.

---
