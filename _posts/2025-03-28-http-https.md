---
layout: post
title: 🚀 HTTP/HTTPS – Giao thức truyền tải siêu văn bản
date: 2025-03-28 02:58 +0700
categories: [Network]
tags: [
    HTTP là gì,
    HTTPS là gì,
    SSL/TLS,
    HTTP vs HTTPS,
    Cách chuyển từ HTTP sang HTTPS
]
image:
  path: /assets/img/http-https/http-https.jpg
---

## 🎯 **Giới thiệu về HTTP và HTTPS**
**HTTP (Hypertext Transfer Protocol)** là giao thức truyền tải siêu văn bản, cho phép các trình duyệt web và máy chủ web giao tiếp với nhau. HTTP là nền tảng của mọi trang web, giúp truyền tải thông tin từ máy chủ tới trình duyệt người dùng.

Tuy nhiên, **HTTP** không cung cấp bất kỳ phương thức bảo mật nào, vì vậy thông tin truyền tải có thể bị tấn công hoặc theo dõi. Để khắc phục vấn đề này, **HTTPS (Hypertext Transfer Protocol Secure)** ra đời. HTTPS là phiên bản bảo mật của HTTP, kết hợp với các giao thức bảo mật như **SSL/TLS** (Secure Sockets Layer/Transport Layer Security) để mã hóa thông tin và bảo vệ dữ liệu khi truyền qua mạng.

## 🛠️ **HTTP (Hypertext Transfer Protocol)**

### ✅ **Cách thức hoạt động của HTTP**
HTTP là giao thức **không kết nối** (stateless), có nghĩa là mỗi yêu cầu HTTP giữa trình duyệt và máy chủ đều là một kết nối độc lập. Khi người dùng yêu cầu một trang web, trình duyệt sẽ gửi một yêu cầu HTTP đến máy chủ, và máy chủ sẽ phản hồi bằng cách gửi lại dữ liệu cần thiết (HTML, CSS, JavaScript, v.v.).

Ví dụ về yêu cầu HTTP từ trình duyệt:
```http
GET /index.html HTTP/1.1
Host: www.example.com
```
Yêu cầu này sẽ yêu cầu máy chủ www.example.com gửi trang index.html.

### ✅ **Đặc điểm của HTTP**
1️⃣ **Không mã hóa:** Dữ liệu truyền qua HTTP không được mã hóa, khiến nó dễ bị tấn công như **Man-in-the-Middle (MITM)**.

2️⃣ **Không bảo mật:** HTTP không cung cấp bất kỳ cơ chế bảo mật nào, khiến dữ liệu có thể bị đánh cắp hoặc sửa đổi trong quá trình truyền tải.

## 🛠️ **HTTPS (Hypertext Transfer Protocol Secure)**

### ✅ **Cách thức hoạt động của HTTPS**
1️⃣ **HTTPS** sử dụng giao thức **SSL/TLS** để mã hóa kết nối giữa máy khách và máy chủ. Điều này giúp bảo vệ tính toàn vẹn và bảo mật của dữ liệu, ngăn chặn việc lắng nghe và sửa đổi dữ liệu trong quá trình truyền tải.

2️⃣ Khi người dùng truy cập một trang web sử dụng HTTPS, trình duyệt sẽ thiết lập một kết nối bảo mật với máy chủ. Máy chủ sẽ gửi một **SSL/TLS certificate** để xác minh danh tính và bắt đầu quá trình mã hóa.

### ✅ **Lợi ích của HTTPS**
1️⃣ **Mã hóa**: HTTPS sử dụng **SSL/TLS** để mã hóa tất cả các thông tin truyền qua mạng, bảo vệ dữ liệu khỏi việc bị nghe lén hoặc sửa đổi.

2️⃣ **Xác thực**: HTTPS xác nhận rằng người dùng đang kết nối với đúng máy chủ và không phải là một kẻ giả mạo.

3️⃣ **Bảo vệ tính toàn vẹn của dữ liệu**: HTTPS đảm bảo rằng dữ liệu không bị thay đổi trong quá trình truyền tải, giúp ngăn chặn các cuộc tấn công như **man-in-the-middle**.

### ✅ **SSL/TLS – Mã hóa trong HTTPS**
**SSL (Secure Sockets Layer)** và **TLS (Transport Layer Security)** là các giao thức bảo mật được sử dụng trong HTTPS để mã hóa kết nối giữa trình duyệt và máy chủ. Mặc dù SSL đã lỗi thời và bị thay thế bởi TLS, thuật ngữ **SSL** vẫn thường được sử dụng để chỉ cả hai giao thức.

####    **TLS Handshake**
Trong quá trình thiết lập kết nối HTTPS, **TLS** thực hiện một quy trình gọi là **handshake**, trong đó máy khách và máy chủ thỏa thuận các yếu tố bảo mật, bao gồm việc tạo khóa mã hóa.

####    **Mã hóa phiên**
Sau khi handshake hoàn tất, một **session key** được tạo ra và sử dụng để mã hóa tất cả dữ liệu trong suốt phiên làm việc.

## 🧑‍💻 **Sự khác biệt giữa HTTP và HTTPS**

| Tiêu chí                     | HTTP                           | HTTPS                               |
|-----------------------------|--------------------------------|-------------------------------------|
| **Bảo mật**                  | Không có mã hóa, không bảo mật | Mã hóa dữ liệu bằng SSL/TLS        |
| **Cổng mặc định**            | Cổng 80                        | Cổng 443                           |
| **Giới hạn sử dụng**         | Chỉ dùng trong môi trường không quan trọng về bảo mật | Dùng cho các trang web yêu cầu bảo mật (ví dụ: ngân hàng, thanh toán online) |
| **Sử dụng SSL/TLS**          | Không sử dụng                  | Sử dụng SSL/TLS để mã hóa và xác thực |
| **Khả năng bị tấn công**     | Dễ bị tấn công (MITM, sniffing) | Bảo vệ chống lại tấn công MITM và sniffing |

## ✅ **Khi nào nên sử dụng HTTPS?**

1️⃣ **Trang web yêu cầu bảo mật**: Nếu bạn điều hành một trang web yêu cầu bảo mật, như dịch vụ ngân hàng trực tuyến, thanh toán hoặc đăng nhập người dùng, bạn cần phải sử dụng HTTPS.

2️⃣ **Bảo vệ dữ liệu nhạy cảm**: Nếu ứng dụng của bạn xử lý dữ liệu nhạy cảm như mật khẩu, thông tin tài khoản, hoặc thông tin thẻ tín dụng, việc sử dụng HTTPS là bắt buộc.

3️⃣ **SEO và xếp hạng trên Google**: Google sử dụng HTTPS như một yếu tố xếp hạng, vì vậy nếu bạn muốn cải thiện khả năng tìm kiếm của trang web, việc chuyển sang HTTPS là rất quan trọng.

## 🛠️ **Cách chuyển từ HTTP sang HTTPS**

### ✅ **1. Cài đặt SSL/TLS Certificate**
Để sử dụng HTTPS, bạn cần phải có một **SSL/TLS certificate** hợp lệ từ một nhà cung cấp chứng chỉ (ví dụ: **Let’s Encrypt**, **DigiCert**). Chứng chỉ này sẽ xác minh danh tính của bạn và mã hóa kết nối giữa máy khách và máy chủ.

### ✅ **2. Cấu hình máy chủ web**
Sau khi có chứng chỉ SSL, bạn cần cấu hình máy chủ web của mình để hỗ trợ HTTPS. Ví dụ, với **Nginx**, bạn có thể thay đổi cấu hình của mình như sau:

```nginx
server {
    listen 443 ssl;
    server_name www.yourwebsite.com;

    ssl_certificate /path/to/certificate.crt;
    ssl_certificate_key /path/to/private.key;

    # Các cấu hình SSL khác
}
```

### ✅ **3. Chuyển hướng HTTP sang HTTPS**
- Bạn cũng nên cấu hình máy chủ web để chuyển hướng tất cả các yêu cầu HTTP sang HTTPS để đảm bảo tất cả người dùng đều được bảo mật.
- Ví dụ với Nginx:

```nginx
server {
    listen 80;
    server_name www.yourwebsite.com;
    return 301 https://$host$request_uri;
}
```

## 🚀 **Tổng kết**
**HTTP** và **HTTPS** đều là các giao thức truyền tải thông tin quan trọng trên web, nhưng **HTTPS** cung cấp một lớp bảo mật đáng tin cậy nhờ vào mã hóa SSL/TLS. Việc chuyển từ HTTP sang HTTPS giúp bảo vệ dữ liệu người dùng, đảm bảo tính toàn vẹn và bảo mật của thông tin, và đồng thời giúp cải thiện SEO cho trang web của bạn.