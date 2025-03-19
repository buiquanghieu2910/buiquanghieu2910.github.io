---
layout: post
title: 🚀 Jekyll | Trình Tạo Trang Tĩnh Mạnh Mẽ Cho Blog & Website
date: 2025-03-20 00:01 +0700
categories: [Jekyll]
tags: [Jekyll, Web Development, static-site, ruby]
image:
  path: /assets/img/jekyll-introduction/jekyll_pages.jpg
  width: 800
---

## 📌 1. Jekyll là gì?

Jekyll là một **static site generator** (trình tạo trang web tĩnh) được viết bằng **Ruby**, giúp biên dịch file **Markdown**, **Liquid**, **HTML** và **CSS** thành các trang web tĩnh hoàn chỉnh. Jekyll thích hợp cho **blog**, **trang tài liệu**, **portfolio** hoặc **các trang web cá nhân** nhẹ nhàng.

## 🎯 2. Tại sao nên dùng Jekyll?

### ⚡ **Hiệu suất nhanh**

✅ Tạo trang tĩnh, giúp tối ưu tốc độ tải trang.
✅ Không dùng database, giảm thiểu tài nguyên server.

### 🔒 **Bảo mật cao**

✅ Không có backend, không lo lỗi SQL Injection hay hack database.

### 💰 **Miễn phí hosting với GitHub Pages**

✅ Dễ dàng deploy lên **GitHub Pages** mà không tốn chi phí.

### 📝 **Hỗ trợ Markdown và Liquid**

✅ Viết bài nhanh chóng với **Markdown**.
✅ Sử dụng **Liquid template** để tùy chỉnh giao diện.

## 🔧 3. Cách cài đặt Jekyll

### 🖥 **Cài đặt trên macOS/Linux**

```sh
gem install jekyll bundler
jekyll new my-site
cd my-site
bundle exec jekyll serve
```

📌 Truy cập `http://localhost:4000/` để xem trang web.

### 🖥 **Cài đặt trên Windows**

1. Tải Ruby từ [rubyinstaller.org](https://rubyinstaller.org/).
2. Cài Jekyll:
   ```sh
   gem install jekyll bundler
   jekyll new my-site
   cd my-site
   bundle exec jekyll serve
   ```

## ✍️ 4. Cách tạo bài viết trong Jekyll

📌 Tất cả bài viết được đặt trong thư mục `_posts/` và theo định dạng `YYYY-MM-DD-ten-bai-viet.md`.

📝 **Ví dụ một bài viết:**

```md
---
layout: post
title: "Giới thiệu Jekyll"
date: 2025-03-19
author: "John Doe"
categories: [Jekyll, Blog]
---

Jekyll là một trình tạo trang tĩnh mạnh mẽ giúp bạn xây dựng blog nhanh chóng.
```

## 🎨 5. Tùy chỉnh giao diện trong Jekyll
Jekyll cung cấp nhiều cách để tùy chỉnh giao diện trang web, bao gồm sử dụng **Liquid Template Engine**, thêm **theme**, và chỉnh sửa **CSS**.

### 🔹 **Sử dụng Liquid Template Engine**
Liquid là một template engine mạnh mẽ giúp hiển thị nội dung động trên trang tĩnh.

### 🔹 **Chỉnh sửa giao diện bằng CSS**
Bạn có thể thay đổi kiểu dáng trang web bằng cách chỉnh sửa file CSS trong thư mục `assets/css/`.

📌 **Ví dụ cập nhật file `style.css`**:
```css
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  color: #333;
}
```

### 🔹 **Sử dụng theme có sẵn**
Jekyll hỗ trợ các theme giúp bạn tùy chỉnh giao diện nhanh chóng. Bạn có thể chọn theme trong `_config.yml`.
```yaml
theme: minima
```

## 🎭 6. Cách tìm theme cho Jekyll

Jekyll cho phép sử dụng theme có sẵn hoặc tùy chỉnh.

🔍 **Tìm theme Jekyll tại:**

- 🎨 [Jekyll Themes Directory](https://jekyllrb.com/resources/themes/)
- 🎭 [GitHub Jekyll Themes](https://github.com/topics/jekyll-theme)
- 🖥 [https://jekyllthemes.io/](https://jekyllthemes.io/)
- 🌍 [https://jamstackthemes.dev/ssg/jekyll/](https://jamstackthemes.dev/ssg/jekyll/)

👉 **Cài đặt theme:**

```yaml
# Trong _config.yml
theme: minima
```

## 🚀 7. Deploy Jekyll lên GitHub Pages

Jekyll hỗ trợ deploy miễn phí trên GitHub Pages.

🛠 **Các bước deploy:**

```sh
git init
git add .
git commit -m "Deploy Jekyll site"
git branch -M main
git remote add origin https://github.com/your-username/your-username.github.io.git
git push -u origin main
```

🌍 Truy cập `https://your-username.github.io/` để xem website.

## ⚖️ 8. So sánh Jekyll với WordPress

| 🏷️ Tiêu chí      | 🚀 Jekyll (Static)           | 🌐 WordPress (CMS)                |
| ---------------- | ---------------------------- | --------------------------------- |
| ⚡ **Hiệu suất** | Nhanh, không cần database    | Chậm hơn do dùng MySQL            |
| 🔒 **Bảo mật**   | Cao, không có backend        | Dễ bị tấn công nếu không cập nhật |
| 💰 **Lưu trữ**   | Miễn phí trên GitHub Pages   | Cần hosting                       |
| 🎛 **Dễ dùng**    | Cần biết Markdown, Git       | Giao diện trực quan, dễ sử dụng   |
| 🎨 **Tùy chỉnh** | Dùng Liquid, phải code nhiều | Nhiều plugin hỗ trợ               |

## 🤔 9. Khi nào nên dùng Jekyll?

✅ **Dùng Jekyll khi:**

- ⚡ Bạn muốn trang web nhanh, nhẹ, bảo mật cao.
- 🔧 Bạn không muốn dùng database hay CMS phức tạp.
- 📝 Bạn thích viết bằng Markdown và quản lý nội dung bằng Git.

❌ **Không nên dùng Jekyll khi:**

- 🎛 Bạn cần website có giao diện quản trị dễ sử dụng.
- 💡 Bạn không quen sử dụng Git và dòng lệnh.
- 🌐 Bạn muốn một trang web động có nhiều tính năng phức tạp.

## 🎯 10. Kết luận

Jekyll là công cụ mạnh mẽ cho các **blog** và **trang web tĩnh**.

✅ **Hiệu suất cao, bảo mật tốt.**
✅ **Hỗ trợ Markdown, Liquid.**
✅ **Miễn phí hosting với GitHub Pages.**

👉 **Nếu bạn muốn một trang web nhanh, nhẹ, bảo mật, Jekyll là lựa chọn hoàn hảo!** 🚀
