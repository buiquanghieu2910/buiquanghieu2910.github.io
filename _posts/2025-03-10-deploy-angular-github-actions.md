---
layout: post
title: Hướng Dẫn Deploy Angular Lên GitHub Pages Bằng GitHub Actions
date: 2025-03-10 21:40 +0700
categories: [DevOps]
tags:
  [
    Angular,
    GitHub Actions,
    Deploy Angular,
    GitHub Pages,
    CORS,
    API Proxy,
    CI/CD,
  ]
image:
  path: /assets/img/deploy-angular-github-actions/github-actions-angular.png
  width: 800
---

# 🚀 Hướng Dẫn Deploy Angular Lên GitHub Pages Bằng GitHub Actions

_Dành cho developer muốn tận dụng GitHub Actions để tự động build và deploy Angular, đồng thời call API từ máy chủ khác một cách tối ưu._

---

## 📌 1. Giới thiệu

GitHub Actions giúp tự động hóa quá trình **build** và **deploy** Angular lên **GitHub Pages**, giảm thiểu công việc thủ công.\
Bài viết này hướng dẫn:\
✅ Cách cấu hình **GitHub Actions** để tự động build & deploy Angular.\
✅ Cách xử lý lỗi **404 Not Found** khi refresh trang trên GitHub Pages.\
✅ Cách call API từ máy chủ khác mà không bị lỗi CORS.

---

## 🛠 2. Cấu hình GitHub Actions để Deploy Angular

Tạo thư mục `.github/workflows/` và thêm file `deploy.yml`:

```yaml
name: Deploy Angular to GitHub Pages

on:
  push:
    branches:
      - main # Thay bằng branch chính của bạn nếu khác

permissions:
  contents: write # Cần quyền ghi để deploy lên GitHub Pages

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: 🚀 Checkout code
        uses: actions/checkout@v3

      - name: 📦 Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: 📥 Install dependencies
        run: npm install

      - name: 🔨 Build Angular
        run: npm run build -- --output-path=dist --base-href /your-repo-name/

      - name: 🚀 Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          branch: gh-pages
          folder: dist # Thư mục build của Angular
```

🔹 **Lưu ý**:

- \*\*Thay \*\*`` bằng tên repository của bạn.
- Nếu branch chính không phải `main`, sửa `branches: - main` thành `branches: - tên_branch_của_bạn`.
- Khi \*\*push code lên branch \*\*``, GitHub Actions sẽ tự động deploy.

---

## ⚙ 3. Cấu hình GitHub Pages

### 🔹 Bật GitHub Pages trong repository

1. Vào **Settings** → **Pages**.
2. Ở phần **Source**, chọn branch `gh-pages` (nếu chưa có, GitHub Actions sẽ tự tạo).
3. Nhấn **Save**.

---

## 🌍 4. Xử lý lỗi 404 khi refresh trên GitHub Pages

Vì Angular là SPA, khi F5 trang, GitHub Pages không tìm thấy file tương ứng và trả về lỗi **404 Not Found**. Cách khắc phục:

### 🔹 Cách 1: Dùng Hash Mode (`useHash: true`)

Mở `app.module.ts`, sửa lại `RouterModule`:

```ts
imports: [RouterModule.forRoot(routes, { useHash: true })];
```

Lúc này, URL sẽ có dạng:

```
https://your-username.github.io/#/about
```

### 🔹 Cách 2: Thêm file `404.html` để redirect

Tạo file `404.html` trong thư mục `dist` với nội dung:

```html
<script>
  window.location.replace("/?" + document.location.pathname.substring(1));
</script>
```

---

## 🔌 5. Call API từ máy chủ khác

### 🔹 Vấn đề CORS khi gọi API

Nếu API server không bật CORS, khi Angular gọi API từ GitHub Pages, bạn sẽ gặp lỗi:

```
Access to fetch at 'https://api.yourserver.com/data' from origin 'https://your-username.github.io' has been blocked by CORS policy.
```

### 🔹 Cách khắc phục

#### 1️⃣ Cấu hình CORS trên backend (tốt nhất)

Ví dụ với **Node.js Express**:

```js
const cors = require("cors");
app.use(cors({ origin: "https://your-username.github.io" }));
```

Với **PHP**:

```php
header("Access-Control-Allow-Origin: https://your-username.github.io");
```

#### 2️⃣ Dùng Reverse Proxy (nếu không chỉnh backend được)

Nếu không thể chỉnh server API, bạn có thể dùng **CORS proxy server** như `cors-anywhere`:

```ts
const apiUrl =
  "https://cors-anywhere.herokuapp.com/https://api.yourserver.com/data";
this.http.get(apiUrl).subscribe((data) => console.log(data));
```

#### 3️⃣ Cấu hình Proxy trong Angular (`proxy.conf.json`)

Nếu bạn test API trên **localhost**, tạo file `proxy.conf.json`:

```json
{
  "/api": {
    "target": "https://api.yourserver.com",
    "secure": false,
    "changeOrigin": true,
    "pathRewrite": { "^/api": "" }
  }
}
```

Chạy Angular với proxy:

```sh
ng serve --proxy-config proxy.conf.json
```

Sau đó gọi API như sau:

```ts
this.http.get("/api/data").subscribe((data) => console.log(data));
```

---

## 🎯 6. Kết luận

✅ **GitHub Actions** giúp **tự động build & deploy** Angular lên GitHub Pages.\
✅ **Cấu hình Hash Mode hoặc 404.html** để tránh lỗi 404 khi refresh.\
✅ **Call API từ máy chủ khác**, xử lý lỗi CORS bằng backend hoặc proxy.

🔥 Với cách này, bạn chỉ cần **push code lên GitHub**, mọi thứ sẽ được **deploy tự động**! 🚀
