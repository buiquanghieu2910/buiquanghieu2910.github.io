---
layout: post
title: 🔄 HTTP Methods & Status Codes trong API – Cách dùng đúng chuẩn
date: 2025-03-23 21:50 +0700
categories: [API]
tags:
  [
    http methods trong api, 
    status code api,
    status code thường gặp, 
    xử lý lỗi api
  ]
image:
  path: /assets/img/http-methods-va-status-code-trong-api/http-status-code.jpg
---

## 📌 HTTP Methods là gì?

Khi bạn gọi một API (qua trình duyệt, code, hoặc Postman), bạn thường thấy các từ như `GET`, `POST`, `PUT`, `DELETE`… Đó chính là **HTTP Methods** – cách bạn nói cho server biết mình muốn làm gì với dữ liệu.

---

## 🚦 Các HTTP Methods phổ biến

| Method   | Mục đích chính             | Ví dụ sử dụng                |
|----------|-----------------------------|-------------------------------|
| 🟢 **GET**    | Lấy dữ liệu                 | Lấy danh sách sản phẩm         |
| 🟡 **POST**   | Tạo mới dữ liệu            | Tạo đơn hàng mới               |
| 🔵 **PUT**    | Cập nhật toàn bộ           | Cập nhật thông tin người dùng |
| 🟣 **PATCH**  | Cập nhật một phần          | Chỉ cập nhật số điện thoại     |
| 🔴 **DELETE** | Xoá dữ liệu                | Xoá bài viết                   |

📌 **Ghi nhớ:** `PUT` thường cập nhật toàn bộ object, còn `PATCH` chỉ cập nhật phần thay đổi.

---

## 🧪 Ví dụ dùng phương thức HTTP

```json
GET: /api/products

POST: /api/users
Body:
{
  "name": "Nguyễn Văn A",
  "email": "nva@example.com"
}
```

## ⚠️ HTTP Status Codes – Mã trạng thái thường dùng trong API

Mỗi khi gọi API, server sẽ trả về một **status code** để thông báo kết quả xử lý. Dưới đây là danh sách các mã phổ biến và thường gặp nhất:

### ✅ **1xx – Informational (Thông tin)**

| Mã  | Ý nghĩa                          | Ghi chú                                                  |
|-----|----------------------------------|-----------------------------------------------------------|
| 100 | 🕐 Continue                      | Tiếp tục gửi phần còn lại của request                    |
| 101 | 🔄 Switching Protocols           | Chuyển đổi giao thức (ví dụ: HTTP → WebSocket)          |
| 102 | ⏳ Processing                     | Đang xử lý (WebDAV) – Server nhận và đang thực thi       |
| 103 | 📢 Early Hints                   | Gợi ý trước khi trả về response đầy đủ (tăng tốc tải tài nguyên) |

---

### ✅ **2xx – Success (Thành công)**

| Mã  | Ý nghĩa                          | Khi nào dùng                                              |
|-----|----------------------------------|------------------------------------------------------------|
| 200 | ✅ OK                            | Xử lý thành công, có dữ liệu trả về                       |
| 201 | 🆕 Created                       | Tạo mới thành công (POST)                                 |
| 202 | ⏳ Accepted                      | Đã nhận request, đang xử lý (async, hàng đợi...)          |
| 203 | 🪪 Non-Authoritative Information | Trả dữ liệu từ bên thứ ba (proxy), không phải gốc server  |
| 204 | 🚫 No Content                   | Thành công nhưng không có nội dung trả về                 |
| 205 | 🧼 Reset Content                | Thành công – yêu cầu client reset form (hiếm dùng)        |
| 206 | 🧩 Partial Content              | Trả về một phần dữ liệu (thường dùng cho video/audio)     |
| 207 | 📦 Multi-Status                 | Trả nhiều kết quả cho một request (WebDAV)                |
| 208 | 🔁 Already Reported             | Tài nguyên đã được báo cáo (trong cùng một collection)    |
| 226 | ⚙️ IM Used                      | Server đã sử dụng bộ nén (delta encoding) để trả kết quả  |

---

### ⚠️ **3xx – Redirection (Chuyển hướng)**

| Mã  | Ý nghĩa                          | Ghi chú                                                   |
|-----|----------------------------------|------------------------------------------------------------|
| 300 | 🔃 Multiple Choices              | Có nhiều lựa chọn phản hồi (hiếm dùng)                    |
| 301 | 🔁 Moved Permanently             | Đã chuyển vĩnh viễn sang URL khác                         |
| 302 | 🔂 Found                         | Chuyển tạm thời sang URL khác                             |
| 303 | 📥 See Other                     | Yêu cầu GET tới URL khác (sau POST)                       |
| 304 | 📦 Not Modified                  | Tài nguyên không thay đổi (thường dùng với caching)       |
| 305 | 🧭 Use Proxy                     | Phải truy cập thông qua proxy (đã không còn được khuyến nghị) |
| 306 | 🚫 Switch Proxy                  | Không còn được sử dụng (đã deprecated)                    |
| 307 | 🔁 Temporary Redirect            | Chuyển hướng tạm thời, giữ nguyên HTTP method             |
| 308 | 🔁 Permanent Redirect            | Chuyển hướng vĩnh viễn, giữ nguyên HTTP method            |

📌 *Lưu ý:* Nhóm mã 1xx và 3xx ít gặp khi bạn chỉ làm việc với REST API đơn thuần, nhưng khi làm việc với proxy, caching, video streaming, HTTP nâng cao... thì cực kỳ hữu ích để debug chính xác.

---

### ❌ **4xx – Client Error (Lỗi từ phía client)**

| Mã  | Ý nghĩa                         | Khi nào gặp                                         |
|-----|----------------------------------|-----------------------------------------------------|
| 400 | ❌ Bad Request                   | Request sai định dạng, thiếu dữ liệu, sai kiểu dữ liệu |
| 401 | 🔐 Unauthorized                  | Chưa đăng nhập, thiếu hoặc sai token xác thực       |
| 402 | 💳 Payment Required              | Cần thanh toán để tiếp tục (hiếm dùng)              |
| 403 | ⛔ Forbidden                     | Có xác thực nhưng không đủ quyền truy cập           |
| 404 | 🔍 Not Found                     | Không tìm thấy tài nguyên hoặc endpoint yêu cầu     |
| 405 | 📛 Method Not Allowed            | Dùng sai HTTP method (ví dụ: dùng POST cho /users/:id) |
| 406 | 📄 Not Acceptable                | Không hỗ trợ định dạng dữ liệu mà client yêu cầu     |
| 407 | 🔑 Proxy Authentication Required | Cần xác thực với proxy (ít gặp)                    |
| 408 | ⏱️ Request Timeout               | Server chờ quá lâu mà không nhận được request hoàn chỉnh |
| 409 | ⚔️ Conflict                      | Dữ liệu bị xung đột (trùng email, version xung đột...) |
| 410 | 🗑️ Gone                          | Tài nguyên không còn tồn tại và không có địa chỉ mới |
| 411 | 📏 Length Required               | Server yêu cầu header Content-Length nhưng không có |
| 412 | 🧩 Precondition Failed           | Điều kiện tiên quyết không thoả mãn                 |
| 413 | 📦 Payload Too Large             | Request gửi lên quá lớn so với giới hạn server cho phép |
| 414 | 🔗 URI Too Long                  | URL quá dài (gửi dữ liệu sai cách qua query params) |
| 415 | 🧬 Unsupported Media Type        | Loại dữ liệu không được hỗ trợ (ví dụ gửi XML khi chỉ hỗ trợ JSON) |
| 416 | 📼 Range Not Satisfiable         | Client yêu cầu phần dữ liệu không hợp lệ (video, file...) |
| 417 | 🎯 Expectation Failed            | Server không đáp ứng được header `Expect`           |
| 422 | 🧾 Unprocessable Entity          | Dữ liệu hợp lệ về mặt cú pháp nhưng sai về logic (validate form sai) |
| 426 | ⬆️ Upgrade Required              | Server yêu cầu nâng cấp giao thức (thường là TLS/HTTPS) |
| 429 | 🧨 Too Many Requests             | Quá nhiều request trong thời gian ngắn (rate limit) |

📌 *Lưu ý:* Không nhất thiết phải hỗ trợ toàn bộ mã trên, nhưng bạn nên **xử lý rõ ràng ít nhất các mã từ 400 đến 429** để API chuyên nghiệp hơn.

---

### 💥 **5xx – Server Error (Lỗi từ phía server)**

| Mã  | Ý nghĩa                         | Khi nào xảy ra                                                     |
|-----|----------------------------------|--------------------------------------------------------------------|
| 500 | 💥 Internal Server Error         | Lỗi không xác định từ server, thường do exception, lỗi logic      |
| 501 | 🛠️ Not Implemented              | Chức năng chưa được hỗ trợ hoặc chưa triển khai                   |
| 502 | ⚡ Bad Gateway                   | Gateway (ví dụ: API Gateway, proxy) nhận phản hồi lỗi từ upstream server |
| 503 | 💤 Service Unavailable           | Server đang bảo trì hoặc quá tải, không thể xử lý tại thời điểm đó |
| 504 | ⏱️ Gateway Timeout              | Gateway không nhận được phản hồi kịp thời từ server gốc           |
| 505 | 📼 HTTP Version Not Supported    | Server không hỗ trợ phiên bản HTTP mà client gửi                  |
| 506 | 🔄 Variant Also Negotiates       | Server cấu hình sai khi phản hồi content negotiation               |
| 507 | 🗄️ Insufficient Storage          | Server không đủ bộ nhớ để xử lý request                           |
| 508 | 🔁 Loop Detected                 | Phát hiện vòng lặp trong request (thường là WebDAV)                |
| 510 | 🔓 Not Extended                  | Cần thêm phần mở rộng để server xử lý request                     |
| 511 | 🔐 Network Authentication Required | Yêu cầu xác thực mạng (thường trong captive portal Wi-Fi công cộng) |

📌 *Lưu ý:* Trong thực tế, mã 500–504 là nhóm phổ biến nhất cần quan tâm khi phát triển API. Tuy nhiên, nắm rõ các mã còn lại giúp **debug hệ thống hiệu quả hơn**.

---

📌 **Lưu ý khi thiết kế API**:
- Trả về **mã đúng với ý nghĩa xử lý thực tế**.
- Khi trả về lỗi 4xx/5xx, nên kèm theo **thông điệp chi tiết trong body** để client dễ hiểu và xử lý.

---
## 🧠 Gợi ý khi thiết kế API

- ✅ **Luôn trả về status code phù hợp** với kết quả xử lý (200, 201, 400, 404...).
- 🧾 **Gửi thông điệp rõ ràng trong body** khi xảy ra lỗi để client dễ xử lý.
- 💡 **Sử dụng các phương thức đúng mục đích**:  
  `GET` để đọc, `POST` để tạo, `PUT/PATCH` để cập nhật, `DELETE` để xoá – giúp API RESTful hơn.

---

## 🧠 Tổng kết

> **HTTP Methods + Status Code** là nền tảng quan trọng khi làm việc với API – dù bạn là **frontend**, **backend** hay **tester**.

Việc hiểu và sử dụng đúng giúp bạn:

- ✨ Viết code **rõ ràng và có tổ chức**
- 🛠 Dễ **debug và bảo trì**
- 📦 Xây dựng API **chuẩn RESTful**, dễ tích hợp và mở rộng

---
