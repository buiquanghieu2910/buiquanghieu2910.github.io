---
layout: post
title: 🚀 Interceptor trong Spring Boot – Giải pháp xử lý trước và sau khi yêu cầu được xử lý
date: 2025-03-29 18:59 +0700
categories: [Java, Spring Boot]
tags: [
    Interceptor trong Spring Boot, 
    Sử dụng Interceptor, 
    Cấu hình Interceptor, 
    Spring Boot request interceptor, 
    Spring Boot logging interceptor
]
image:
  path: /assets/img/spring-boot-interceptor/spring-boot-interceptor.png
---

## 🎯 **Giới thiệu về Interceptor trong Spring Boot**
**Interceptor** trong Spring Boot là một công cụ mạnh mẽ được sử dụng để can thiệp vào chuỗi xử lý của HTTP requests và responses. Interceptor giúp bạn có thể thực hiện một số thao tác trước khi yêu cầu được gửi tới Controller hoặc sau khi Controller trả về kết quả cho client. Nó tương tự như **filters** trong Java, nhưng có thể được sử dụng để thực hiện các tác vụ phức tạp hơn trong quá trình xử lý HTTP requests.

Interceptor thường được sử dụng trong các tình huống như:
- Ghi lại log mỗi lần yêu cầu vào hoặc ra.
- Kiểm tra quyền truy cập của người dùng.
- Chuyển đổi dữ liệu yêu cầu hoặc kết quả trả về.
- Thực hiện các thao tác chuẩn bị trước khi yêu cầu vào hoặc xử lý sau khi phản hồi ra.

## 🛠️ **Cấu hình Interceptor trong Spring Boot**
Để cấu hình và sử dụng **Interceptor** trong Spring Boot, bạn cần thực hiện một số bước cơ bản:

### ✅ **1. Tạo một lớp Interceptor**
Đầu tiên, bạn cần tạo một lớp implement interface `HandlerInterceptor`. Trong lớp này, bạn có thể override các phương thức `preHandle()`, `postHandle()`, và `afterCompletion()` để thực hiện các tác vụ cần thiết.

```java
import org.springframework.web.servlet.HandlerInterceptor;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        // Thực hiện một số thao tác trước khi yêu cầu được gửi tới controller
        System.out.println("Pre-handle: Request is about to be handled");
        return true; // Return true để yêu cầu tiếp tục, false nếu muốn dừng yêu cầu
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        // Thực hiện các thao tác sau khi controller xử lý yêu cầu, nhưng trước khi trả về view
        System.out.println("Post-handle: Request has been handled, but before rendering the view");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        // Thực hiện các thao tác sau khi request hoàn tất và view đã được render
        System.out.println("After-completion: Request has been completed");
    }
}
```

### ✅ **2. Đăng ký Interceptor trong Spring Boot**
Sau khi tạo lớp Interceptor, bạn cần đăng ký Interceptor trong ứng dụng Spring Boot của mình. Điều này có thể thực hiện bằng cách cấu hình nó trong một lớp WebMvcConfigurer để Spring Boot có thể nhận diện và thực thi Interceptor.

```java
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new MyInterceptor())
                .addPathPatterns("/**") // Áp dụng cho tất cả các yêu cầu
                .excludePathPatterns("/login", "/register"); // Loại trừ các URL không cần xử lý
    }
}
```

### ✅ **3. Kết quả khi sử dụng Interceptor**
Khi bạn sử dụng Interceptor, bất cứ khi nào có yêu cầu đến từ người dùng, các phương thức trong lớp Interceptor của bạn sẽ được gọi theo thứ tự preHandle(), postHandle(), và afterCompletion().

Ví dụ:
- preHandle(): Được gọi trước khi yêu cầu được gửi đến controller. Bạn có thể kiểm tra thông tin người dùng, kiểm tra quyền truy cập, hoặc thực hiện các tác vụ trước khi yêu cầu được xử lý.
- postHandle(): Được gọi sau khi controller xử lý yêu cầu nhưng trước khi trả về kết quả. Thường được sử dụng để thay đổi kết quả trả về, thêm thông tin hoặc xử lý dữ liệu.
- afterCompletion(): Được gọi sau khi yêu cầu hoàn tất và view đã được render. Thường dùng để ghi log hoặc thực hiện các tác vụ dọn dẹp.

## 🧑‍💻 **Khi nào nên sử dụng Interceptor?**

### ✅ **1. Ghi log và theo dõi**
Nếu bạn muốn ghi lại các yêu cầu và phản hồi của người dùng cho mục đích phân tích hoặc theo dõi, **Interceptor** là một công cụ hữu ích. Bạn có thể ghi lại thông tin về thời gian yêu cầu, địa chỉ IP, thông tin của người dùng hoặc các chi tiết khác.

### ✅ **2. Kiểm tra quyền truy cập của người dùng**
**Interceptor** có thể được sử dụng để kiểm tra quyền truy cập của người dùng trước khi cho phép họ truy cập vào một số tài nguyên trong ứng dụng. Ví dụ, bạn có thể kiểm tra **token xác thực** của người dùng trong phương thức `preHandle()`.

### ✅ **3. Xử lý dữ liệu trước khi yêu cầu**
**Interceptor** cũng có thể được sử dụng để thay đổi hoặc bổ sung thông tin trong yêu cầu trước khi chúng được gửi tới controller. Ví dụ: bạn có thể thay đổi **headers** của yêu cầu, hoặc xử lý các tham số truy vấn.

### ✅ **4. Chuyển hướng người dùng**
Nếu người dùng chưa đăng nhập hoặc không có quyền truy cập vào tài nguyên cụ thể, bạn có thể sử dụng **Interceptor** để chuyển hướng họ đến trang đăng nhập hoặc trang báo lỗi.

## 🚀 **Tổng kết**
**Interceptor** trong **Spring Boot** là một công cụ mạnh mẽ để can thiệp vào quá trình xử lý HTTP requests và responses. Với khả năng thực hiện các tác vụ trước và sau khi yêu cầu được xử lý, **Interceptor** có thể giúp bạn:
- Ghi log, kiểm tra quyền truy cập,
- Thay đổi dữ liệu yêu cầu hoặc kết quả,
- Thực hiện các thao tác khác.

### **Ưu điểm khi sử dụng Interceptor**:
- Ghi log và theo dõi các yêu cầu và phản hồi.
- Kiểm tra quyền truy cập của người dùng trước khi yêu cầu được xử lý.
- Thay đổi dữ liệu yêu cầu hoặc kết quả trước khi trả về client.
- Giảm thiểu mã lặp lại trong controller bằng cách xử lý các logic chung.

### **Khi nào nên dùng?**
- Khi bạn cần xử lý các yêu cầu HTTP ở cấp độ toàn cục.
- Khi bạn muốn thực hiện các tác vụ như ghi log, kiểm tra quyền truy cập hoặc xử lý dữ liệu trước khi gửi tới controller.