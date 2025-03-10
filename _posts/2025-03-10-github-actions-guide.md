---
layout: post
title: Giới thiệu Github Actions
date: 2025-03-10 21:33 +0700
categories: [Github]
tags: [GitHub Actions, CI/CD, DevOps, Workflow, Automation, GitHub]
image:
  path: /assets/img/github-actions-guide/github_actions.jpg
  width: 800
---
# 🚀 GitHub Actions

GitHub Actions là một dịch vụ CI/CD (Continuous Integration/Continuous Deployment) giúp tự động hóa các quy trình phát triển phần mềm ngay trong repository của GitHub.

## 📝 1. Tổng quan

GitHub Actions cho phép bạn tạo các workflow để:
- ✅ Tự động hóa quá trình build, test và deploy ứng dụng.
- 🔄 Chạy script theo lịch trình hoặc khi có sự kiện cụ thể xảy ra (push code, mở pull request, tạo release,...).
- 🔗 Tích hợp với các dịch vụ bên thứ ba hoặc quản lý hạ tầng.

## 🏗 2. Cấu trúc của GitHub Actions

### 📜 Workflow
- Là một tập hợp các job được định nghĩa trong file YAML trong thư mục `.github/workflows/`.
- Ví dụ file workflow `ci.yml`:
  
  ```yaml
  name: CI Pipeline
  on: [push, pull_request]

  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - name: Checkout repository
          uses: actions/checkout@v4
        
        - name: Set up Node.js
          uses: actions/setup-node@v3
          with:
            node-version: '18'
        
        - name: Install dependencies
          run: npm install

        - name: Run tests
          run: npm test
  ```

### 🏗 Job
- Một tập hợp các bước (steps) chạy trên cùng một runner.
- Có thể chạy song song hoặc theo thứ tự nhất định.

### 🔧 Step
- Một bước trong job, có thể là chạy command hoặc sử dụng một action có sẵn.

### 💻 Runner
- Môi trường thực thi workflow (Ubuntu, Windows, macOS, hoặc self-hosted runner).

## 🚀 3. Cách tạo một GitHub Actions đơn giản

1. **📂 Tạo thư mục và file workflow**
   ```sh
   mkdir -p .github/workflows
   touch .github/workflows/main.yml
   ```
2. **✍️ Viết nội dung file `main.yml`**
   ```yaml
   name: Hello GitHub Actions
   on: [push]
   
   jobs:
     hello-world:
       runs-on: ubuntu-latest
       steps:
         - name: Print Hello World
           run: echo "Hello, GitHub Actions!"
   ```
3. **📤 Commit và push code lên GitHub**
   ```sh
   git add .
   git commit -m "Add GitHub Actions workflow"
   git push origin main
   ```

4. **🔍 Kiểm tra workflow trên GitHub**
   - Vào repository → Tab `Actions` để xem trạng thái workflow.

## ⚙️ 4. Các Action hữu ích
- 🛠 `actions/checkout@v4`: Lấy source code từ repository.
- 🏗 `actions/setup-node@v3`: Thiết lập Node.js.
- 🐳 `docker/build-push-action`: Xây dựng và đẩy Docker image.
- 🔍 `github/super-linter`: Chạy linter để kiểm tra code.

## 🚀 5. Triển khai ứng dụng với GitHub Actions
Ví dụ deploy lên Vercel:
```yaml
name: Deploy to Vercel
on: push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Deploy to Vercel
        run: npx vercel --token ${{ secrets.VERCEL_TOKEN }}
```

## 🎯 6. Kết luận
GitHub Actions là một công cụ mạnh mẽ giúp tự động hóa quá trình phát triển phần mềm. Việc hiểu và áp dụng đúng cách sẽ giúp tăng hiệu suất và giảm thiểu công việc thủ công trong quy trình DevOps.