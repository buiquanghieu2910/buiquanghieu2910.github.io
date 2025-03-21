---
layout: post
title: 🛠️Tạo JPA Entity từ Database trên Eclipse hoặc Spring Tool Suite
date: 2023-12-01 00:23 +0700
categories: [Java]
tags: [JPA Entity, Eclipse, Java, G9]
image:
  path: /assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/background.jpg
  width: 800
---
## 🚀 Cài đặt Extensions

📌 Để hỗ trợ việc tạo **JPA Entity** từ database một cách nhanh chóng, bạn cần cài đặt **G9 Database Import** trong **Eclipse** hoặc **Spring Tool Suite**.

### 🔹 Các bước cài đặt:
###### 1️⃣ **Vào menu**: `Help -> Eclipse Marketplace`
###### 2️⃣ **Tìm kiếm**: Nhập từ khóa **G9** vào ô tìm kiếm.
###### 3️⃣ **Cài đặt**: Chọn `G9 Database Import` và nhấn **Install**.
###### 4️⃣ **Chờ đợi**: Quá trình cài đặt diễn ra khoảng **7-10 phút**.
###### 5️⃣ **Khởi động lại IDE**: Khi cài đặt xong, **Restart IDE** để hoàn tất quá trình cài đặt.

📌 **Sau khi cài đặt xong, bạn có thể tiến hành import database để tạo JPA Entity.**

---

## ⚙️ Cấu hình kết nối Database

### 📌 Các bước thực hiện:

###### 1️⃣ **Click chuột phải** vào project cần generate.
###### 2️⃣ Chọn `Import` → `Import...`
###### 3️⃣ Tìm đến thư mục **`G9`** → Chọn **`Import Database Model`**.

📌 **Cấu hình kết nối Database:**

```yaml
JDBC Driver:  // Chọn JDBC tương ứng với database đang dùng
Hostname:     // Thông thường là "localhost", nếu dùng DB trên server thì nhập IP Public
Database:     // Nhập tên database cần kết nối
Username:     // Nhập tài khoản quản trị database
Password:     // Nhập mật khẩu tương ứng với tài khoản
```

###### 4️⃣ **Bấm `Fetch` để kiểm tra kết nối**.
###### 5️⃣ **Nếu kết nối thành công**, bấm `Next` để tiếp tục.

📌 **Sau khi kết nối thành công, giao diện sẽ hiển thị danh sách bảng trong database.**

---

## 📂 Chọn bảng & Tùy chỉnh Entity

###### 1️⃣ **Root package**: Nhập tên package chứa các entity.
###### 2️⃣ **Chọn bảng**: Nhấn **`Select All`** để chọn tất cả các bảng hoặc chọn từng bảng muốn tạo Entity.
###### 3️⃣ **Tùy chỉnh Class Name**:
   - Chọn bảng muốn chỉnh sửa ở cột `Class Name`.
   - Nhấn **`Edit`** để thay đổi tên class tương ứng.
   
###### 4️⃣ **Nhấn `Finish`** để bắt đầu quá trình generate Entity từ database.

📌 **Sau khi hoàn tất, JPA Entity sẽ được tạo tự động trong project.** ✅

---

## 🎯 Kết quả

📌 Sau khi **generate thành công**, các entity sẽ xuất hiện trong package đã chọn.

🚀 **Bây giờ bạn có thể sử dụng các entity này để thao tác với database thông qua JPA!**

---

## 🎉 Kết luận

✔️ **G9 Database Import** giúp bạn tiết kiệm thời gian khi tạo **JPA Entity** từ database.  
✔️ **Hỗ trợ kết nối nhanh chóng** với nhiều loại database khác nhau.  
✔️ **Tùy chỉnh tên class linh hoạt** trước khi generate.

🚀 **Chúc các bạn thành công!** 🎯