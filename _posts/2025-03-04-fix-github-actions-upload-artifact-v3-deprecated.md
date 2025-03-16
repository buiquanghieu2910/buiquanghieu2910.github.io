---
layout: post
title: 🚀Cách sửa lỗi "Build failed because it uses a deprecated version of actions/upload-artifact v3"
date: 2025-03-04 02:43 +0700
categories: [Github]
tags: [Github, Github Actions, actions/upload-artifact:v3]
---
## ❌ Nguyên nhân
GitHub Actions đã **ngừng hỗ trợ** các phiên bản cũ của một số actions quan trọng, trong đó có **`actions/upload-artifact@v3`**. Nếu bạn đang sử dụng phiên bản cũ trong workflow của mình, quá trình build có thể bị lỗi.

---

## 🛠 Cách khắc phục
Bạn cần **cập nhật** các action bị deprecated lên **phiên bản mới nhất** bằng cách chỉnh sửa file workflow YAML.

### 🔄 Cập nhật phiên bản mới
Dưới đây là danh sách các action cũ và phiên bản mới cần cập nhật:

| ⚠️ **Old value** | ✅ **New value** |
|-----------------|----------------|
| `actions/cache@v3` | `actions/cache@v4` |
| `actions/configure-pages@v3` | `actions/configure-pages@v5` |
| `actions/deploy-pages@v2` | `actions/deploy-pages@v4` |
| `actions/upload-pages-artifact@v2` | `actions/upload-pages-artifact@v3` |
| `peaceiris/actions-hugo@v2` | `peaceiris/actions-hugo@v3` |

### 📝 Cách chỉnh sửa file workflow
1️⃣ Mở file `.github/workflows/{workflow_name}.yml` trong repository của bạn.  
2️⃣ Tìm kiếm các dòng sử dụng các phiên bản cũ.  
3️⃣ Thay đổi thành phiên bản mới theo bảng trên.  
4️⃣ 💾 Lưu lại và **commit** các thay đổi.  
5️⃣ 📤 **Push** lên repository để GitHub Actions chạy lại với phiên bản mới.  

🔹 **Ví dụ**: Nếu workflow của bạn có dòng:
```yaml
- uses: actions/upload-artifact@v3
```
Bạn cần thay đổi thành:
```yaml
- uses: actions/upload-artifact@v4
```

---

## ✅ Kiểm tra lại
Sau khi cập nhật, kiểm tra lại workflow bằng cách:
- 🏗 **Truy cập** tab **Actions** trên GitHub repository.
- 📌 **Kiểm tra** xem các job đã chạy thành công chưa.
- 🔎 Nếu vẫn gặp lỗi, **đọc kỹ log** để xem có action nào khác cần cập nhật.

---

## 🎯 Kết luận
Việc **cập nhật lên phiên bản mới** giúp **tránh lỗi build** và đảm bảo workflow của bạn **chạy ổn định**. Hãy kiểm tra định kỳ và cập nhật các action cần thiết để đảm bảo tính **tương thích lâu dài**. 🚀