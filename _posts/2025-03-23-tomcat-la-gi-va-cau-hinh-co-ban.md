---
layout: post
title: ☕ Tomcat là gì? Hướng dẫn cơ bản về thuật ngữ và cấu hình
date: 2025-03-23 04:50 +0700
categories: [DevOps]
tags:
  [
    Tomcat là gì,
    Cấu hình Tomcat cơ bản,
    Tomcat deploy WAR,
    Apache Tomcat cho Java web,
    Hướng dẫn cài Tomcat,
  ]
image:
  path: /assets/img/tomcat-la-gi-va-cau-hinh-co-ban/tomcat.jpg
---

## 🎯 Giới thiệu Tomcat
**Apache Tomcat** là một **Java Servlet Container** mã nguồn mở, dùng để **chạy các ứng dụng web viết bằng Java** (Servlet, JSP...). Đây là lựa chọn phổ biến để triển khai các hệ thống Java web trong môi trường production hoặc học tập.

Tomcat không phải là một web server thuần túy như NginX hay Apache HTTPD, mà là **ứng dụng server chạy Java EE (Enterprise Edition)**.

---

## 🧩 Một số thuật ngữ thường gặp trong Tomcat

| Thuật ngữ          | Ý nghĩa |
|--------------------|---------|
| **Servlet**        | Thành phần Java xử lý HTTP request/response |
| **JSP (JavaServer Pages)** | Mã HTML + Java được dịch sang servlet |
| **WAR File**       | Web Archive – dạng đóng gói ứng dụng Java web |
| **Catalina**       | Engine chính điều khiển Tomcat |
| **Context**        | Một ứng dụng web được deploy trong Tomcat |
| **Connector**      | Kết nối HTTP, AJP... để Tomcat giao tiếp với client |
| **Server.xml**     | File cấu hình chính của Tomcat |
| **Webapps/**       | Thư mục chứa các ứng dụng web (deploy tại đây)

---

## 📁 Cấu trúc thư mục Tomcat
```
apache-tomcat/
├── bin/             # File khởi động (startup.sh / startup.bat)
├── conf/            # File cấu hình (server.xml, web.xml...)
├── logs/            # Log hệ thống và ứng dụng
├── webapps/         # Nơi deploy ứng dụng (đặt file .war hoặc folder)
├── lib/             # Thư viện Java (JAR)
└── temp/ work/      # Thư mục tạm thời
```

---

## ⚙️ Cấu hình Tomcat cơ bản
### 1. **Cấu hình cổng mặc định** trong `conf/server.xml`
```xml
<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```
➡️ Có thể sửa `port="8080"` thành 80 để chạy trên HTTP mặc định.

### 2. **Triển khai ứng dụng Java web**
- Đóng gói file `.war`
- Copy vào thư mục `webapps/`
- Tomcat sẽ tự động giải nén và khởi chạy

Hoặc bạn có thể dùng:
```bash
curl -T myapp.war http://localhost:8080/manager/text/deploy?path=/myapp \
  --user admin:yourpassword
```

### 3. **Tạo user để truy cập Tomcat Manager** (conf/tomcat-users.xml)
```xml
<role rolename="manager-gui"/>
<user username="admin" password="123456" roles="manager-gui"/>
```

---

## 📌 Một số lệnh quản trị Tomcat (Linux)
```bash
./bin/startup.sh     # Khởi động Tomcat
./bin/shutdown.sh    # Dừng Tomcat
tail -f logs/catalina.out   # Xem log realtime
```

---

## 🧠 Khi nào nên dùng Tomcat?
- Khi bạn phát triển ứng dụng Java Servlet / JSP / Spring MVC
- Khi muốn deploy WAR file Java nhanh chóng mà không cần build lại app
- Khi cần server nhẹ hơn so với các Java EE server phức tạp (WildFly, WebLogic...)

---

## ✅ Tổng kết
- **Tomcat** là lựa chọn phổ biến để chạy ứng dụng web Java nhờ sự nhẹ, dễ cấu hình, và mạnh mẽ.
- Hiểu rõ các thành phần như **servlet, context, connector** giúp bạn cấu hình và quản lý Tomcat hiệu quả.
- Nắm vững cấu trúc thư mục, cách deploy và quản trị user là nền tảng để sử dụng Tomcat chuyên nghiệp.

🚀 **Tomcat là bước đệm lý tưởng để triển khai ứng dụng Java trong thực tế – từ học tập đến doanh nghiệp.**