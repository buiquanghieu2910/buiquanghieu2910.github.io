---
layout: post
title: 🌱 Giới thiệu về Spring & Spring Boot
date: 2025-03-21 18:53 +0700
categories: [Java, Spring Boot]
tags:
  [
    Spring Boot là gì,
    Giới thiệu Spring Framework,
    Spring vs Spring Boot,
    Spring IoC và DI,
    Ứng dụng thực tế Spring Boot,
  ]
image:
  path: /assets/img/gioi-thieu-spring-va-spring-boot/spring.png
---

## 🎯 Spring Framework là gì?
**Spring Framework** là một framework mã nguồn mở, mạnh mẽ và phổ biến trong cộng đồng Java, được thiết kế để giúp việc phát triển ứng dụng **Java enterprise** dễ dàng hơn. Spring cung cấp **cấu trúc linh hoạt**, cho phép xây dựng các ứng dụng theo mô hình hướng đối tượng, module hóa, dễ bảo trì.

📌 Spring ra đời nhằm giải quyết các vấn đề rườm rà trong lập trình Java truyền thống, như việc khởi tạo đối tượng, quản lý phụ thuộc, giao tiếp với cơ sở dữ liệu, bảo mật, v.v.

---

## 🧠 IoC Container và Dependency Injection (DI) trong Spring

### 🔄 IoC (Inversion of Control) là gì?
**Inversion of Control** là nguyên lý lập trình mà trong đó **việc tạo đối tượng và quản lý phụ thuộc không do chính class đảm nhiệm**, mà được giao cho **container bên ngoài**.

Trong Spring, IoC được hiện thực thông qua **IoC Container** – chịu trách nhiệm:
- Tạo đối tượng (bean)
- Quản lý vòng đời của bean
- Tiêm phụ thuộc giữa các bean (DI)

### 📦 Bean là gì?
- Là một đối tượng Java do Spring IoC quản lý.
- Được đánh dấu bằng các annotation như `@Component`, `@Service`, `@Repository`, `@Controller`, v.v.

### 🧩 Dependency Injection (DI) là gì?
**Dependency Injection** là kỹ thuật giúp "tiêm" đối tượng phụ thuộc vào class thay vì để class tự khởi tạo chúng.

#### Ví dụ:
```java
@Component
public class UserService {
    private final UserRepository userRepository;

    // Spring sẽ tự động tiêm UserRepository vào đây
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```
Annotation `@Component` đánh dấu class là một bean, và Spring sẽ **quét, tạo đối tượng**, rồi **tiêm tự động (autowire)** các phụ thuộc vào constructor hoặc field.

### ⚙️ Các cách tiêm phụ thuộc trong Spring:

| Phương pháp      | Mô tả |
|------------------|------|
| Constructor Injection | Khuyến khích sử dụng – an toàn, bất biến |
| Setter Injection | Dễ kiểm soát, có thể thay đổi sau khi tạo |
| Field Injection  | Ngắn gọn nhưng khó test, ít khuyến khích |

### 📌 Lợi ích của IoC và DI:
- ✅ Giảm sự phụ thuộc chặt chẽ giữa các lớp (loose coupling)
- ✅ Dễ bảo trì, mở rộng, kiểm thử (unit test, mock)
- ✅ Dễ dàng thay thế implementation khác nhau mà không thay đổi code logic chính

---

## 🔧 Các module chính của Spring Framework

| Module         | Mô tả |
|----------------|------|
| **Core**       | Xử lý Dependency Injection (DI) và Inversion of Control (IoC) |
| **Spring MVC** | Xây dựng web app theo mô hình Model - View - Controller |
| **Spring AOP** | Lập trình hướng khía cạnh (Aspect-Oriented Programming) |
| **Spring Security** | Quản lý xác thực và phân quyền |
| **Spring JDBC / ORM** | Kết nối và thao tác với cơ sở dữ liệu |
| **Spring Test** | Hỗ trợ kiểm thử ứng dụng Spring |

---

## ⚡ Spring Boot là gì?
**Spring Boot** là một extension của Spring Framework, giúp **tự động cấu hình và đơn giản hóa việc phát triển ứng dụng Spring**.

📌 Thay vì phải cấu hình phức tạp hàng loạt file XML, Spring Boot cho phép bạn:
- **Tạo ứng dụng Java nhanh hơn** với cấu hình mặc định.
- **Tích hợp sẵn server (Tomcat)**, không cần triển khai WAR file.
- **Chạy bằng một dòng lệnh duy nhất** (`java -jar app.jar`).
- **Hỗ trợ sẵn các starter**, giúp quản lý dependency dễ dàng qua Maven/Gradle.

---

## 🚀 So sánh Spring & Spring Boot

| Tiêu chí                | Spring Framework | Spring Boot |
|-------------------------|------------------|-------------|
| Cấu hình                | Phức tạp (XML, JavaConfig) | Tự động, nhanh gọn |
| Khởi tạo dự án         | Thủ công        | Spring Initializr (https://start.spring.io) |
| Phụ thuộc (dependency) | Chọn và cấu hình thủ công | Có starter hỗ trợ sẵn |
| Web Server              | Cần cấu hình ngoài (Tomcat, Jetty) | Tích hợp sẵn embedded server |
| Mục tiêu sử dụng        | Linh hoạt cho mọi kiểu ứng dụng Java | Tối ưu cho RESTful API, Microservices |

---

## 📦 Spring Boot hỗ trợ gì?
- ✅ RESTful API (Spring Web)
- ✅ Giao tiếp DB (Spring Data JPA, JDBC)
- ✅ Bảo mật (Spring Security)
- ✅ Kiểm thử (Spring Boot Test)
- ✅ Cấu hình dễ dàng (`application.yml` hoặc `application.properties`)
- ✅ Tích hợp tốt với Docker, Kubernetes, CI/CD

---

## 📱 Ứng dụng thực tế sử dụng Spring Boot
- Hệ thống API backend cho web & mobile
- Ứng dụng thương mại điện tử, CRM, ERP
- Hệ thống tài chính, ngân hàng
- Microservices cho nền tảng cloud-native
- Web app nội bộ doanh nghiệp

---

## 🛠 Một số lệnh Spring Boot cơ bản
```bash
# Tạo project từ Spring Initializr (UI)
https://start.spring.io

# Chạy ứng dụng (sau khi build bằng Maven)
./mvnw spring-boot:run

# Biên dịch và tạo file jar
./mvnw clean package

# Chạy app
java -jar target/myapp.jar
```

---

## ✅ Ưu điểm khi dùng Spring Boot
✔ Khởi tạo nhanh, cấu hình tối giản  
✔ Dễ tích hợp với các công nghệ khác (MySQL, Redis, Kafka...)  
✔ Cộng đồng lớn, tài liệu nhiều  
✔ Phù hợp cho microservices, RESTful API  
✔ Tích hợp tốt với DevOps, CI/CD

---

## 🧠 Tổng kết
- **Spring Framework** cung cấp nền tảng vững chắc cho việc phát triển ứng dụng Java.
- **Spring Boot** giúp đơn giản hóa và tăng tốc độ phát triển ứng dụng.

🚀 **Nếu bạn là lập trình viên Java, Spring Boot là công cụ không thể thiếu để xây dựng các ứng dụng hiện đại, nhanh, gọn và mạnh mẽ!**