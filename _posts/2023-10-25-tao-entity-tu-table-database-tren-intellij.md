---
layout: post
title: 🛠️Tạo entity từ table database trên Intellij
date: 2023-10-25 22:35 +0700
categories: [Java, JPA Buddy]
tags: [Spring JPA, JPA Buddy, Tạo entity từ table database]
image:
  path: /assets/img/tao-entity-tu-table-database-tren-intellij/background.jpg
---
> ⚠️ **Lưu ý:** Bài viết này chỉ mang tính chất tham khảo!

---

## 🚀 Cài đặt Plugin JPA Buddy

📌 Để tạo Entity từ database một cách nhanh chóng, bạn cần cài đặt **JPA Buddy** trong **IntelliJ IDEA**.

### 🔹 Các bước cài đặt:
1️⃣ **Mở IntelliJ IDEA**, vào `File -> Settings`
   
   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-1.png)

2️⃣ Chọn `Plugins -> Marketplace` → **Tìm kiếm** `JPA Buddy`

3️⃣ **Nhấn `Install`** để cài đặt.
   
   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-2.png)

4️⃣ Sau khi cài đặt xong, **khởi động lại IntelliJ IDEA**.
   
   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-3.png)

📌 **Bây giờ bạn đã sẵn sàng để kết nối database và tạo Entity!**

---

## ⚙️ Cấu hình kết nối Database

📌 **Trước khi tạo Entity, hãy kiểm tra file `pom.xml` để đảm bảo đã có thư viện JPA.**

Nếu chưa có, hãy thêm vào hoặc cài đặt theo hướng dẫn:

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-4.png)

---

### 🔹 Các bước kết nối database

1️⃣ **Chọn package nơi bạn muốn tạo Entity**

2️⃣ Nhấp chuột phải → `New -> JPA Entities from DB`

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-5.png)

3️⃣ Nhấn **`+`** để thêm kết nối mới

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-6.png)

4️⃣ Trong tab **Data Sources**, nhấn **`+`** để thêm database mới

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-7.png)

📌 **Ví dụ:** Ở đây, database của mình có **2 bảng**: `products` & `users`.

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-8.png)

---

### 🔹 Cấu hình kết nối Database

📌 **Điền đầy đủ thông tin kết nối database:**

- **Hostname**: `localhost` hoặc địa chỉ server.
- **Database**: Tên database bạn muốn kết nối.
- **Username**: Tài khoản đăng nhập database.
- **Password**: Mật khẩu của database.

📌 **Lưu ý:** Nếu bạn thấy nút **`Install Driver`**, hãy nhấn vào đó để cài đặt driver trước khi **Test Connection**.

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-9.png)

5️⃣ Khi kết nối thành công, danh sách **Tables** sẽ hiển thị đầy đủ.

📌 **Trước khi bấm `OK`, hãy kiểm tra ngôn ngữ bạn đang code (Java hoặc Kotlin) và chọn đúng.** ✅

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-10.png)

---

## 🎯 Thành quả sau khi tạo Entity

📌 **JPA Buddy sẽ tự động tạo Entity có quan hệ giữa các bảng.** 

   ![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-11.png)

✅ Nếu database của bạn có **quan hệ giữa các bảng**, các Entity sẽ tự động có **các annotation @OneToMany, @ManyToOne, @JoinColumn**, v.v.

---

## 🎉 Kết luận

✔️ **JPA Buddy giúp bạn tiết kiệm thời gian** khi tạo **JPA Entity từ database**.  
✔️ **Tích hợp tốt với IntelliJ IDEA**, dễ dàng kết nối nhiều loại database.  
✔️ **Hỗ trợ cả Java & Kotlin**, tùy chỉnh Entity theo nhu cầu.  

🚀 **Chúc các bạn thành công!** 🎯