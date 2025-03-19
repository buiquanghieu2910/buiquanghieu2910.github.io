---
layout: post
title: 🚀 Giới Thiệu Chi Tiết Về Git
date: 2025-03-19 23:18 +0700
categories: [Git]
tags: [Git là gì, Git cơ bản, Cách sử dụng Git, Git tutorial]
image:
  path: /assets/img/git-introduction/git.png
  width: 800
---

## 1. 🧑‍💻 Git là gì?

Git là một hệ thống quản lý phiên bản phân tán (Distributed Version Control System - DVCS), giúp theo dõi lịch sử thay đổi của mã nguồn trong các dự án phần mềm. Nó giúp lập trình viên làm việc nhóm hiệu quả hơn, quản lý mã nguồn dễ dàng và khôi phục phiên bản khi cần thiết.

## 2. ⚡ Các tính năng chính của Git

- **🔄 Phân tán:** Mỗi máy tính trong hệ thống đều có một bản sao đầy đủ của kho lưu trữ.
- **🚀 Nhanh chóng:** Git hoạt động nhanh hơn các hệ thống quản lý phiên bản khác.
- **🌿 Hỗ trợ nhánh (Branch) mạnh mẽ:** Cho phép làm việc trên nhiều tính năng cùng lúc.
- **♻️ Khôi phục dữ liệu dễ dàng:** Có thể quay lại phiên bản cũ nhanh chóng.
- **👥 Hỗ trợ làm việc nhóm tốt:** Dễ dàng chia sẻ mã nguồn với người khác.

## 3. 🏗️ Các thành phần chính trong Git

### 3.1 📂 Repository (Kho lưu trữ)
Là nơi chứa toàn bộ mã nguồn của dự án, bao gồm cả lịch sử thay đổi. Repository có thể là cục bộ (local) hoặc từ xa (remote).

### 3.2 ⏳ Commit
Mỗi lần thay đổi mã nguồn được lưu lại trong Git, nó được gọi là một commit. Mỗi commit có một mã hash duy nhất để theo dõi.

### 3.3 🌿 Branch (Nhánh)
Nhánh giúp làm việc với nhiều tính năng khác nhau mà không ảnh hưởng đến mã nguồn chính. Branch có thể được tạo, chỉnh sửa, hợp nhất hoặc xóa.

### 3.4 🌍 Remote (Kho lưu trữ từ xa)
Là phiên bản của repository được lưu trên máy chủ hoặc nền tảng như GitHub, GitLab, giúp chia sẻ mã nguồn giữa nhiều người.

### 3.5 📥 Staging Area (Vùng tạm lưu)
Là nơi chứa các thay đổi trước khi chúng được commit. Giúp lập trình viên kiểm tra lại trước khi lưu vào lịch sử Git.

### 3.6 🔄 Merge vs. Rebase
#### 🔹 Merge và Rebase để làm gì?
Merge và Rebase đều được sử dụng để kết hợp các thay đổi từ một nhánh khác vào nhánh hiện tại, nhưng cách thức hoạt động của chúng khác nhau.

| Merge | Rebase |
|--------|--------|
| Tạo một commit hợp nhất mới | Áp dụng lại các commit từ nhánh hiện tại lên nhánh chính |
| Lịch sử commit có thể trở nên rối | Lịch sử commit gọn gàng hơn |
| Dễ xử lý xung đột hơn | Có thể gây khó khăn khi xử lý xung đột |

#### 🔹 Khi nào sử dụng?
- **Sử dụng Merge** khi muốn giữ lại toàn bộ lịch sử commit, đặc biệt khi làm việc nhóm để mọi người dễ theo dõi.
- **Sử dụng Rebase** khi muốn có một lịch sử commit sạch sẽ và gọn gàng, giúp dễ dàng kiểm tra lại các thay đổi.

### 3.7 🔁 Fetch vs. Pull
#### 🔹 Fetch và Pull để làm gì?
Fetch và Pull đều được dùng để lấy dữ liệu từ kho lưu trữ từ xa, nhưng cách chúng xử lý dữ liệu khác nhau.

| Fetch | Pull |
|--------|--------|
| Chỉ lấy dữ liệu về máy, không thay đổi mã nguồn cục bộ | Lấy dữ liệu về và tự động hợp nhất vào nhánh hiện tại |
| Kiểm tra thay đổi trước khi hợp nhất | Không có bước kiểm tra trước |
| Dùng khi muốn kiểm tra trước khi thay đổi | Dùng khi muốn cập nhật ngay lập tức |

#### 🔹 Khi nào sử dụng?
- **Sử dụng Fetch** khi bạn muốn xem trước những thay đổi mới trước khi hợp nhất.
- **Sử dụng Pull** khi bạn muốn cập nhật nhanh nhất với phiên bản mới nhất từ repository từ xa.

### 3.8 🍒 Cherry Pick
Cherry-pick giúp chọn một commit cụ thể từ nhánh khác và áp dụng nó vào nhánh hiện tại mà không cần merge toàn bộ nhánh.

### 3.9 🎯 HEAD
HEAD là con trỏ trỏ đến commit hiện tại của repository.

### 3.10 🔄 Git Reset: Phân biệt `git reset`, `git reset --soft`, `git reset --hard`

Lệnh `git reset` được sử dụng để đưa nhánh hiện tại về một trạng thái commit trước đó. Nó có ba chế độ chính:

| Lệnh | Mô tả |
|------|------|
| `git reset` | Đưa commit về trạng thái trước đó nhưng giữ nguyên thay đổi trong working directory |
| `git reset --soft` | Giữ nguyên thay đổi ở cả working directory và staging area (chỉ di chuyển HEAD) |
| `git reset --hard` | Xóa tất cả các thay đổi trong working directory và staging area, hoàn toàn quay lại commit được chỉ định |

## 4. 🛠️ Các câu lệnh cơ bản của Git
```sh
# Cấu hình Git
git config --global user.name "Tên của bạn"
git config --global user.email "email@example.com"

# Khởi tạo Git trong thư mục hiện tại
git init

# Sao chép một kho lưu trữ từ GitHub hoặc GitLab
git clone https://github.com/user/repository.git

# Kiểm tra trạng thái của kho lưu trữ
git status

# Thêm tệp vào vùng staging
git add file.txt
git add .

# Lưu thay đổi vào Git
git commit -m "Mô tả ngắn gọn về thay đổi"

# Xem lịch sử commit
git log
```

## 5. 🌍 Các dịch vụ mã nguồn phổ biến sử dụng Git
### 5.1 GitHub
GitHub là nền tảng lưu trữ mã nguồn phổ biến nhất hiện nay, cung cấp nhiều tính năng hỗ trợ làm việc nhóm.
👉 [Truy cập GitHub](https://github.com/)

### 5.2 GitLab
GitLab cũng là một nền tảng quản lý mã nguồn mạnh mẽ, có hỗ trợ CI/CD.
👉 [Truy cập GitLab](https://gitlab.com/)

### 5.3 Bitbucket
Bitbucket chủ yếu được sử dụng bởi các nhóm phát triển sử dụng Atlassian, hỗ trợ tích hợp tốt với Jira.
👉 [Truy cập Bitbucket](https://bitbucket.org/)

## 6. ✅ Kết luận
Git là một công cụ không thể thiếu đối với lập trình viên, giúp quản lý mã nguồn hiệu quả. Nếu bạn muốn làm việc nhóm chuyên nghiệp, hãy sử dụng Git cùng các dịch vụ như GitHub, GitLab hoặc Bitbucket. 🚀
