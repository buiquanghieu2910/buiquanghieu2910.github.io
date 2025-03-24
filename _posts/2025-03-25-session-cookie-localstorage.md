---
layout: post
title: 🛠️ Session, Cookie, LocalStorage – Sự khác biệt và khi nào nên dùng
date: 2025-03-25 01:08 +0700
categories: [Web Development]
tags:
  [
    Session, Cookie, LocalStorage là gì,
    So sánh Session, Cookie, LocalStorage,
    Khi nào sử dụng Session, Cookie, LocalStorage,
    Phương pháp lưu trữ dữ liệu trong web,
    Bảo mật với Session, Cookie, và LocalStorage,
  ]
image:
  path: /assets/img/session-cookie-localstorage/local-storage-vs-session-storage-vs-cookie.jpg
---

## 🎯 **Giới thiệu chung**
Trong quá trình phát triển ứng dụng web, chúng ta thường xuyên phải làm việc với **Session**, **Cookie**, và **LocalStorage** để lưu trữ dữ liệu của người dùng. Mỗi phương pháp này có những ưu nhược điểm riêng và được sử dụng trong các tình huống khác nhau. Việc hiểu rõ về chúng sẽ giúp bạn lựa chọn giải pháp lưu trữ phù hợp nhất cho ứng dụng của mình.

## 🔧 **Session**
**Session** là một phương pháp lưu trữ dữ liệu trên máy chủ. Mỗi người dùng sẽ có một **session ID** duy nhất được lưu trên máy chủ và có thể lưu trữ thông tin người dùng tạm thời trong suốt thời gian người dùng duy trì phiên làm việc.

### ✅ **Ưu điểm của Session**
- 🔒 **Bảo mật cao**: Dữ liệu được lưu trữ trên máy chủ, giúp tránh việc bị đánh cắp qua client.
- 🧑‍💻 **Quản lý dễ dàng**: Máy chủ có thể kiểm soát toàn bộ session của người dùng, như kéo dài thời gian phiên làm việc hay xóa dữ liệu khi người dùng đăng xuất.
- 🌍 **Không phụ thuộc vào trình duyệt**: Session có thể được sử dụng trên nhiều trình duyệt hoặc trên nhiều tab mà không gặp vấn đề.

### ❌ **Nhược điểm của Session**
- 💾 **Giới hạn bộ nhớ máy chủ**: Dữ liệu lưu trữ trên máy chủ sẽ tiêu tốn tài nguyên của server.
- ⏳ **Không bền vững**: Dữ liệu chỉ tồn tại trong suốt phiên làm việc, khi người dùng đóng trình duyệt hoặc session hết hạn, dữ liệu sẽ bị mất.

### 🔧 **Khi nào nên sử dụng Session?**
- 🛒 Khi bạn cần lưu trữ thông tin tạm thời, ví dụ như thông tin đăng nhập, giỏ hàng.
- 🔐 Khi bạn cần bảo mật cao và không muốn dữ liệu lưu trữ client-side.
- 📊 Khi bạn cần kiểm soát hoàn toàn dữ liệu phiên của người dùng.

---

## 🍪 **Cookie**
**Cookie** là một phương pháp lưu trữ dữ liệu trên client-side (trình duyệt). Dữ liệu được lưu trữ dưới dạng các cặp key-value và được gửi cùng với mỗi yêu cầu HTTP.

### ✅ **Ưu điểm của Cookie**
- 🕰️ **Lưu trữ lâu dài**: Cookie có thể tồn tại lâu dài nếu được cấu hình thời gian hết hạn.
- 📉 **Lưu trữ nhỏ gọn**: Cookie có kích thước giới hạn (4KB) và có thể dễ dàng gửi cùng với mỗi yêu cầu HTTP, giúp duy trì thông tin giữa các yêu cầu.
- 🌐 **Được hỗ trợ rộng rãi**: Hầu hết các trình duyệt đều hỗ trợ cookie, và các cookie có thể được chia sẻ giữa các subdomains.

### ❌ **Nhược điểm của Cookie**
- ⚠️ **Giới hạn kích thước**: Cookie có kích thước giới hạn (4KB), không phù hợp để lưu trữ dữ liệu lớn.
- 🕵️‍♂️ **Bảo mật thấp**: Cookie có thể bị đánh cắp qua các cuộc tấn công XSS (Cross-Site Scripting) hoặc CSRF (Cross-Site Request Forgery), đặc biệt là khi không sử dụng tính năng **Secure** hoặc **HttpOnly**.
- 🐢 **Tốc độ truy cập thấp**: Vì cookie được gửi cùng mỗi yêu cầu HTTP, nó sẽ làm tăng dung lượng của mỗi request/response.

### 🔧 **Khi nào nên sử dụng Cookie?**
- 👤 Khi bạn cần lưu trữ các thông tin nhỏ, ví dụ như mã nhận dạng người dùng, token xác thực.
- ⏳ Khi bạn cần dữ liệu tồn tại lâu dài (ví dụ: lưu trữ dữ liệu đăng nhập).
- 🔄 Khi bạn cần chia sẻ dữ liệu giữa các subdomains hoặc trên các phiên làm việc khác nhau.

---

## 💾 **LocalStorage**
**LocalStorage** là một phương pháp lưu trữ dữ liệu trong trình duyệt của người dùng dưới dạng key-value. Dữ liệu trong LocalStorage được lưu trữ vĩnh viễn cho đến khi người dùng xóa chúng hoặc cho đến khi trình duyệt bị xóa.

### ✅ **Ưu điểm của LocalStorage**
- 📅 **Lưu trữ lâu dài**: Dữ liệu sẽ tồn tại ngay cả khi người dùng đóng trình duyệt hoặc tắt máy.
- 🔒 **Không bị gửi qua HTTP**: Dữ liệu không bị gửi cùng với mỗi yêu cầu HTTP như cookie, giúp giảm thiểu băng thông.
- 🏋️‍♂️ **Lưu trữ dung lượng lớn**: LocalStorage cho phép lưu trữ lên đến 5MB dữ liệu, gấp nhiều lần so với cookie.

### ❌ **Nhược điểm của LocalStorage**
- 🕵️‍♀️ **Bảo mật thấp**: Dữ liệu trong LocalStorage có thể bị truy cập bởi bất kỳ script nào chạy trên trang web, dễ bị tấn công XSS.
- 🚫 **Không hỗ trợ cross-tab hoặc cross-domain**: Dữ liệu chỉ có thể truy cập trong cùng một tab của trình duyệt và không thể chia sẻ giữa các tab hoặc giữa các trình duyệt khác nhau.
- 🕐 **Không có thời gian hết hạn**: Dữ liệu trong LocalStorage sẽ tồn tại vô thời hạn cho đến khi bị xóa thủ công.

### 🔧 **Khi nào nên sử dụng LocalStorage?**
- 📈 Khi bạn cần lưu trữ dữ liệu lớn hơn (lên đến 5MB).
- 🌍 Khi dữ liệu không cần phải được gửi cùng với mỗi yêu cầu HTTP và không yêu cầu bảo mật cao.
- 🛠️ Khi bạn cần lưu trữ dữ liệu vĩnh viễn, ví dụ như thông tin cài đặt người dùng, lịch sử tìm kiếm, hoặc bộ nhớ cache.

---

## 📊 **So sánh Session, Cookie, LocalStorage**

| Tiêu chí                | Session                        | Cookie                          | LocalStorage                  |
|-------------------------|--------------------------------|---------------------------------|--------------------------------|
| **Vị trí lưu trữ**      | Máy chủ                        | Trình duyệt (client-side)       | Trình duyệt (client-side)      |
| **Kích thước**          | Không giới hạn (tùy theo máy chủ) | Giới hạn 4KB                    | Lên đến 5MB                    |
| **Thời gian lưu trữ**   | Tạm thời (khi session kết thúc) | Cấu hình thời gian hết hạn      | Vĩnh viễn (cho đến khi xóa)    |
| **Bảo mật**             | Cao (dữ liệu không nằm trên client) | Thấp (có thể bị đánh cắp qua XSS/CSRF) | Thấp (dễ bị truy cập qua XSS) |
| **Truy cập**            | Chỉ trong phiên làm việc của người dùng | Gửi với mỗi yêu cầu HTTP       | Chỉ trong cùng một tab của trình duyệt |
| **Khi nào nên dùng**    | Lưu trữ thông tin phiên làm việc (đăng nhập, giỏ hàng) | Lưu trữ thông tin nhỏ và dài hạn (token xác thực, ngôn ngữ, cài đặt) | Lưu trữ dữ liệu lớn và lâu dài (lịch sử, cấu hình người dùng) |

---

## 🚀 **Tổng kết**
- **Session** là sự lựa chọn tốt khi cần lưu trữ thông tin tạm thời và bảo mật cao, như thông tin đăng nhập hoặc giỏ hàng.
- **Cookie** là lựa chọn phù hợp khi bạn cần lưu trữ dữ liệu nhỏ và chia sẻ chúng giữa các yêu cầu HTTP, đặc biệt là với các dịch vụ xác thực hoặc dữ liệu người dùng.
- **LocalStorage** phù hợp với các ứng dụng cần lưu trữ dữ liệu lâu dài mà không yêu cầu bảo mật cao, như cài đặt người dùng hoặc bộ nhớ cache.

Việc lựa chọn giữa **Session**, **Cookie**, và **LocalStorage** phụ thuộc vào nhu cầu cụ thể của ứng dụng và các yếu tố bảo mật, hiệu suất và dung lượng lưu trữ.

---

Bài viết này sẽ giúp bạn hiểu rõ hơn về **Session**, **Cookie**, và **LocalStorage** để có thể lựa chọn phương pháp lưu trữ phù hợp cho ứng dụng của mình.