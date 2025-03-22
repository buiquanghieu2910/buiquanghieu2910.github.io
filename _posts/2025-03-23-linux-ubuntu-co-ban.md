---
layout: post
title: 🐧 Giới thiệu Hệ điều hành Linux & Ubuntu – Cơ bản cho người mới bắt đầu
date: 2025-03-23 04:40 +0700
categories: [OS]
tags:
  [
    Linux là gì,
    Ubuntu cơ bản,
    Lệnh Linux cho người mới,
    Ubuntu dùng để làm gì,
  ]
image:
  path: /assets/img/linux-ubuntu-co-ban/linux-ubuntu.png
---

## 🎯 Linux là gì?
**Linux** là một hệ điều hành mã nguồn mở, nổi tiếng về sự ổn định, bảo mật và khả năng tùy biến cao. Linux được sử dụng phổ biến trong server, cloud, thiết bị IoT, hệ thống nhúng, và cả máy tính cá nhân.

Linux không phải là một hệ điều hành đơn lẻ, mà là một **họ hệ điều hành** (distribution / distro), ví dụ: Ubuntu, Debian, CentOS, Fedora, Arch Linux...

---

## 🟠 Ubuntu là gì?
**Ubuntu** là một bản phân phối (distro) phổ biến nhất của Linux dành cho người dùng phổ thông và lập trình viên. 
- Phát triển bởi Canonical.
- Giao diện thân thiện (Ubuntu Desktop).
- Có phiên bản server nhẹ, nhanh, phù hợp triển khai hệ thống (Ubuntu Server).

Ubuntu rất được ưa chuộng để:
- Phát triển phần mềm
- Chạy server web (LAMP, Nginx)
- Dùng trong cloud, VPS, container (Docker base image)

---

## 📦 Ưu điểm của Linux & Ubuntu
- ✅ Miễn phí, mã nguồn mở
- ✅ Bảo mật cao, ít bị virus
- ✅ Tiêu tốn ít tài nguyên hệ thống
- ✅ Tùy biến dễ dàng, có nhiều bản phân phối phù hợp mục đích
- ✅ Hỗ trợ tốt cho lập trình viên, devops, sysadmin

---

## 💻 Một số lệnh Linux thường dùng
### 🔹 Cập nhật & cài phần mềm
```bash
sudo apt update             # Cập nhật danh sách gói
sudo apt upgrade            # Nâng cấp hệ thống
sudo apt install nginx      # Cài Nginx
sudo apt remove <package>  # Gỡ gói đã cài
```

### 🔹 Quản lý tệp & thư mục
```bash
ls                # Liệt kê file/thư mục
cd <dir>          # Di chuyển thư mục
pwd               # Hiển thị đường dẫn hiện tại
mkdir <ten>       # Tạo thư mục
rm <file>         # Xóa file
rm -r <folder>    # Xóa thư mục
cp <src> <dst>    # Copy file/thư mục
mv <src> <dst>    # Di chuyển/đổi tên
```

### 🔹 Quản lý người dùng
```bash
adduser username        # Thêm user
usermod -aG sudo user   # Thêm user vào nhóm sudo
passwd user             # Đặt lại mật khẩu
```

### 🔹 Quyền & tiến trình
```bash
chmod +x file.sh      # Cấp quyền thực thi
chown user:group file # Thay đổi quyền sở hữu
ps aux                # Liệt kê tiến trình đang chạy
kill <PID>            # Dừng tiến trình
```

### 🔹 Khác
```bash
clear                 # Xóa màn hình terminal
reboot                # Khởi động lại hệ thống
shutdown now          # Tắt máy
```

---

## 📌 Khi nào nên dùng Ubuntu/Linux?
- Khi bạn làm **lập trình web, backend, DevOps**
- Khi cần **môi trường ổn định để triển khai server**
- Khi học về **bảo mật, hệ điều hành, quản trị mạng**
- Khi muốn dùng máy cũ hiệu quả hơn

---

## 🧠 Tổng kết
- **Linux** là nền tảng mạnh mẽ, an toàn, linh hoạt, rất phù hợp cho người làm IT.
- **Ubuntu** là bản phân phối dễ tiếp cận, đầy đủ tài liệu, cộng đồng lớn.
- Nắm vững các lệnh cơ bản sẽ giúp bạn làm chủ hệ thống và làm việc hiệu quả hơn trong môi trường server, VPS, cloud.

🚀 **Bắt đầu với Ubuntu ngay hôm nay để bước vào thế giới Linux – nơi sức mạnh của lập trình và hệ thống hội tụ!**
