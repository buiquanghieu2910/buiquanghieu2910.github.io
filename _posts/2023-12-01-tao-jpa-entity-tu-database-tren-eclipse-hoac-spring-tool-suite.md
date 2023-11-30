---
layout: post
title: Tạo JPA Entity từ Database trên Eclipse hoặc Spring Tool Suite
date: 2023-12-01 00:23 +0700
categories: [Java, JPA Entity]
tags: [JPA Entity, Eclipse, Java, G9]
image:
  path: /assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/background.jpg
  width: 800
---

## Cài đặt Extensions

Trong IDE các bạn vào Help -> Eclipse MarketPlace -> Search từ khóa G9 -> Install g9 Datase Import (như hình bên dưới)
Đợi quá trình Install diễn ra khoảng 7-10p, sau đó có thông báo Restart IDE
![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-1.png)

## Cấu hình

Click chuột phải vào project cần generate -> Import -> Import( như hình)
![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-2.png)

Tìm đến folder g9 -> Chọn Import Database Model
![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-3.png)

```yaml
JDBC Driver: // chọn JDBC tương ứng với database đang dùng
Hostname:    // Thông thường sẽ là "localhost", nếu ai dùng db trên server thì điền IP Address Public
Database:    // Tên database
Username:    // Tên user quản trị
Password:    // Mật khẩu tương ứng với user
```
Sau đó bấm Fetch để kết nối
<br>
Nếu kết nối thành công thì bấm chọn Next (Như hình bên dưới)

![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-4.png)

Root package: Điền tên package chứa đựng entity
<br>
Select all để chọn tất cả các table cần generate hoặc select table cần generate
<br>
Lưu ý: Có thể tùy biến Class name bằng cách select bất kỳ dòng nào muốn tùy biến ở cột Class name sau đó chọn Edit
<br>
Cuối cùng chọn Finsh để quá trình generate được diễn ra
<br>
(Như hình bên dưới)

![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-5.png)

Đây là kết quả sau khi generate
![Image](/assets/img/tao-jpa-entity-tu-database-tren-eclipse-hoac-spring-tool-suite/image-6.png)

**_Chúc các bạn thành công !!!_**
````
