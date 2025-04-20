---
layout: post
title: 📁 SFTP (SSH File Transfer Protocol)
date: 2025-04-21 01:39 +0700
categories: [Technology]
tags: [
    SFTP,
    SSH File Transfer Protocol,
    Truyền tệp an toàn,
    SFTP là gì,
    Cách sử dụng SFTP,
    Bảo mật SFTP,
  ]
image:
  path: /assets/img/sftp-ssh-file-transfer-protocol/sftp.jpg
---
SFTP, hay **SSH File Transfer Protocol**, là một giao thức truyền tải tệp an toàn, được sử dụng để truyền tải tệp giữa các máy tính qua kết nối mạng. Nó là một phần của **SSH (Secure Shell)** và cung cấp một phương thức bảo mật để truy cập, truyền và quản lý tệp trên các máy chủ từ xa.

## 🛡️ Tính Năng Của SFTP

- **Bảo mật cao**: SFTP sử dụng mã hóa **SSH**, đảm bảo an toàn cho các tệp trong quá trình truyền tải.
- **Xác thực người dùng**: SFTP yêu cầu xác thực qua tên người dùng và mật khẩu hoặc khóa SSH, đảm bảo chỉ người có quyền mới có thể truy cập dữ liệu.
- **Truyền tệp và quản lý tệp từ xa**: Bạn có thể tải lên, tải xuống và quản lý các tệp từ xa trên máy chủ.
- **Chế độ truyền tải an toàn**: Tất cả các giao dịch đều được mã hóa, giúp bảo vệ tệp khỏi các cuộc tấn công như nghe lén hoặc giả mạo.

## 🖥️ Cách Hoạt Động Của SFTP

SFTP hoạt động trên cơ sở **SSH**, với các lệnh chính như:

- `get`: Tải tệp từ máy chủ về máy tính cục bộ.
- `put`: Tải tệp từ máy tính cục bộ lên máy chủ.
- `ls`: Liệt kê các tệp và thư mục trên máy chủ.
- `cd`: Thay đổi thư mục làm việc trên máy chủ.
- `rm`: Xóa tệp trên máy chủ.

## 🌐 Cách Kết Nối với Máy Chủ qua SFTP

Để kết nối với máy chủ qua SFTP, bạn cần có một máy chủ hỗ trợ SSH và cài đặt phần mềm SFTP trên máy tính của mình. Các bước cơ bản như sau:

1. **Mở terminal hoặc công cụ SFTP** (ví dụ: FileZilla, WinSCP, hoặc lệnh `sftp` trong terminal).
2. **Kết nối đến máy chủ**:
   ```bash
   sftp username@hostname
   ```
3. **Nhập mật khẩu hoặc sử dụng khóa SSH để xác thực.**
4. **Sử dụng các lệnh SFTP để truyền tải và quản lý tệp.***

## 🔒 Lợi Ích Của Việc Sử Dụng SFTP

- **Bảo mật tuyệt đối**: SFTP mã hóa tất cả dữ liệu khi truyền, ngăn chặn các mối đe dọa bảo mật.
- **Quản lý dễ dàng**: Các công cụ như FileZilla, WinSCP giúp người dùng dễ dàng sử dụng giao thức SFTP mà không cần phải thao tác qua dòng lệnh.
- **Tính linh hoạt**: Hỗ trợ nhiều hệ điều hành khác nhau, bao gồm Linux, macOS, và Windows.

## 🚀 Sử Dụng SFTP trong Các Dự Án Thực Tế

SFTP rất hữu ích trong các tình huống yêu cầu truyền tải tệp an toàn, chẳng hạn như:

- Truyền tệp giữa các máy chủ và máy tính cá nhân trong các dự án phát triển phần mềm.
- Sao lưu dữ liệu từ máy tính lên máy chủ từ xa.
- Chuyển tệp giữa các máy chủ khi triển khai ứng dụng hoặc cập nhật phần mềm.

## 🧑‍💻 Các Công Cụ SFTP Phổ Biến

- **FileZilla**: Một trong những công cụ phổ biến nhất giúp người dùng dễ dàng truyền tệp qua SFTP.
- **WinSCP**: Công cụ SFTP cho Windows, giúp việc truyền tệp trở nên dễ dàng và hiệu quả.
- **Cyberduck**: Dành cho người dùng macOS và Windows, hỗ trợ SFTP, FTP, và nhiều giao thức khác.

## 🔧 Kết Luận

SFTP là một công cụ quan trọng trong việc truyền tải tệp an toàn qua mạng, giúp bảo vệ dữ liệu khỏi các mối đe dọa bên ngoài. Việc sử dụng SFTP mang lại nhiều lợi ích, đặc biệt là về bảo mật và tính linh hoạt khi truyền tệp giữa các máy tính và máy chủ từ xa. Hãy đảm bảo rằng bạn đang sử dụng SFTP trong các dự án quan trọng để bảo vệ dữ liệu của mình.