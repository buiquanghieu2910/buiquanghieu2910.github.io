---
layout: post
title: 🔐Xử lý Token Introspection trong Spring Boot với Keycloak
date: 2025-03-05 03:07 +0700
categories: [Java, Spring Boot]
tags:
  [
    Keycloak logout,
    Spring Boot Keycloak token introspection,
    OAuth2 Resource Server Keycloak,
    Spring Security Keycloak,
    Revoke Keycloak token in Spring Boot,
    Spring Boot OAuth2 opaque token
  ]
---
## 📌 1. Giới thiệu

Trong **Spring Boot**, khi sử dụng **OAuth2 Resource Server**, bạn có hai cách để kiểm tra token từ **Keycloak**:

1️⃣ **Dùng JWT (`jwt.issuer-uri`)** → Token tự kiểm tra bằng chữ ký số, nhanh nhưng **không kiểm tra được nếu token bị revoke**.  
2️⃣ **Dùng Token Introspection (`opaque-token.introspection-uri`)** → Mỗi lần request sẽ **gửi token lên Keycloak để kiểm tra tính hợp lệ**.

---

## ⚙️ 2. Cấu hình Resource Server với Token Introspection

Để sử dụng **Token Introspection**, cần cấu hình **Spring Boot gửi token lên Keycloak** thay vì tự giải mã JWT.

### 📄 **Cấu hình `application.yml`**

```yaml
server:
  port: 8081
  servlet:
    context-path: /resource-server-jwt

spring:
  security:
    oauth2:
      resourceserver:
        opaque-token:
          introspection-uri: http://localhost:8083/auth/realms/rasool/protocol/openid-connect/token/introspect
          client-id: change-me
          client-secret: change-me
```

🔹 **Lưu ý:**

- 🛠 `introspection-uri`: API kiểm tra token từ Keycloak, lấy từ **`.well-known/openid-configuration`**.
- 🔑 `client-id` & `client-secret`: Thông tin client đăng ký trong Keycloak.

---

### 📄 **Cấu hình `SecurityConfig.java`**

Nếu bạn dùng **Java config** thay vì file `.yml`, bạn có thể làm như sau:

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
public class SecurityConfig {
    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(auth -> auth.anyRequest().authenticated())
            .oauth2ResourceServer(oauth2 -> oauth2.opaqueToken());
        return http.build();
    }
}
```

---

## ⚖️ 3. So sánh JWT vs Token Introspection

| ✅ **Cách** | 🚀 **Ưu điểm** | ⚠️ **Nhược điểm** |
|--------------------------------|----------------------------------|--------------------------------|
| **JWT (`jwt.issuer-uri`)** | ✅ Hiệu suất cao vì không gọi Keycloak | ❌ Không kiểm tra được token bị revoke |
| **Token Introspection (`opaque-token.introspection-uri`)** | ✅ Kiểm tra token mỗi lần request, bảo mật hơn | ❌ Hiệu suất thấp hơn do phải gọi Keycloak |

---

## 🎯 4. Kết luận

✔️ Nếu bạn cần **hiệu suất cao**, hãy dùng **JWT**.  
✔️ Nếu bạn muốn **kiểm tra token đã bị revoke hay chưa**, hãy dùng **Token Introspection**. 🚀

---

## 🔗 5. Tham khảo

📌 [Cách cấu hình Spring Boot để xác thực JWT token qua introspection endpoint](https://stackoverflow.com/questions/73266668/how-to-configure-spring-boot-to-validate-jwt-token-with-call-instropection-endpo)