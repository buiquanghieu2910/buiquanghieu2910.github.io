---
layout: post
title: Tạo entity từ table database trên Intellij
date: 2023-10-25 22:35 +0700
categories: [Java, JPA Buddy]
tags: [Spring JPA, JPA Buddy, Tạo entity từ table database]
image:
  path: /assets/img/tao-entity-tu-table-database-tren-intellij/background.jpg
---

<p style="color:red; font-weight:bold;">
Bài viết chỉ mang tính chất tham khảo
</p>

# **1. Cài Plugins**

Tại giao diện màn hình Intellij, chọn File -> Settings
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-1.png)

Tiếp theo chọn Plugins -> Marketplace -> Search từ khóa “JPA Buddy” -> Install
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-2.png)

Quá trình cài đặt hoàn tất, chọn Restart IDE
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-3.png)

<br/>

# **2. Cấu hình**

**Lưu ý:** Trong file pom.xml phải có thư viện JPA. Nếu chưa có, click vào đây để lấy thư viện
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-4.png)

Chọn Package muốn tạo Entity -> New -> JPA Entities form DB
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-5.png)

Click “+” để add connection
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-6.png)

Tab “Data Sources” -> Click “+”
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-7.png)

Database ví dụ của mình có 2 bảng là products & users
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-8.png)

Quay lại giao diện Intellij, điền đầy đủ thông tin kết nối

**Lưu ý:** Nếu không có **“Test Connection”** thì nó sẽ thay thế bằng Install Driver, các bạn install xong test connection
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-9.png)

Khi kết nối thành công thì ở phần Tables sẽ hiển thị đầy đủ những table mà trong db đang có

**Lưu ý:** Trước khi bấm OK thì phải xem mình đang code ngôn ngữ gì để chọn đúng ngôn ngữ, **Kotlin or Java**
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-10.png)

Và đây là thành quả

**_Nếu các table của các bạn có quan hệ, thì khi gen xuống cũng tự có quan hệ trong các entity_**
![Image](/assets/img/tao-entity-tu-table-database-tren-intellij/image-11.png)

<p align="center" >
 CHÚC CÁC BẠN THÀNH CÔNG !
</p>
