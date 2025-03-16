---
layout: post
title: 🚀Deploy project Vuejs trên Github
date: 2023-10-26 18:13 +0700
categories: [DevOps]
tags: [DevOps, Deploy VueJs, VueJs, Github page, Deploy VueJs to Github]
image:
  path: /assets/img/deploy-vue-to-github/background.jpg
---

## 🌍 Giới thiệu GitHub Pages

**GitHub Pages** là nơi chúng ta có thể **hosting miễn phí** các project trực tiếp từ các repository trên **GitHub**. Với GitHub Pages, bạn có thể dễ dàng **host trang web cá nhân, landing page, hoặc các project Vue.js** của mình chỉ trong vài bước đơn giản.

Hôm nay, mình sẽ hướng dẫn các bạn cách **deploy Vue.js project lên GitHub Pages**, giúp bạn có thể hosting project Vue.js của mình một cách nhanh chóng và hoàn toàn miễn phí. 🚀

---

## 🏗 Tạo project Vue.js

Đầu tiên, bạn cần cài đặt **Vue CLI**. Nếu chưa có, hãy chạy lệnh sau:

```sh
npm install -g @vue/cli
```

Sau đó, tạo một project Vue.js mới:

```sh
vue create deploy_vue_to_github
```

---

## 🛠 Kiểm tra project Vue.js

Sau khi tạo thành công project Vue.js, bạn kéo thư mục chứa project vào **Visual Studio Code** hoặc IDE mà bạn sử dụng.

Mở **terminal** trên IDE và chạy lệnh:

```sh
npm run serve
```

📌 **Khi chạy thành công**, bạn sẽ thấy URL **localhost** xuất hiện. Hãy mở trình duyệt và kiểm tra xem project Vue.js có hoạt động đúng không. ✅

---

## ⚙️ Build project để deploy

Sau khi kiểm tra xong, hãy chỉnh sửa file **`vue.config.js`** như sau:

```js
module.exports = {
  publicPath:
    process.env.NODE_ENV === "production"
      ? "/deploy_vue_to_github/" // Thay tên repository của bạn
      : "/",
};
```

📌 **Lưu ý:** Thay thế **`deploy_vue_to_github`** bằng tên repository của bạn trên GitHub.

Tiếp theo, quay lại terminal và chạy lệnh build:

```sh
npm run build
```

🏗 **Sau khi build thành công**, một thư mục **`dist`** sẽ xuất hiện chứa các file HTML, CSS và JS cần deploy.

---

## 🔄 Deploy lên GitHub Pages

Mở terminal và chạy lần lượt các lệnh sau để đẩy project lên GitHub:

```sh
cd dist

git init
git add -A
git commit -m "deploy_vue_to_github"
git push -f https://github.com/<tên-user-github>/<tên-repo>.git master:gh-pages
```

📌 **Lưu ý:** Thay **`<tên-user-github>`** và **`<tên-repo>`** bằng thông tin repository của bạn.

🚀 **Sau khi push thành công**, vào GitHub và kiểm tra tab **Actions** để đảm bảo quá trình deploy thành công.

---

## 🔗 Truy cập trang web đã deploy

Cuối cùng, mở trình duyệt và nhập đường dẫn:

```
https://<tên-user-github>.github.io/<tên-repo>/
```

Ví dụ: [Xem demo tại đây](https://buiquanghieu2910.github.io/deploy_vue_to_github) 🌐

---

## 🎉 Kết luận

🔥 **Chúc mừng!** Bạn đã hoàn thành việc deploy Vue.js project lên GitHub Pages thành công! 🚀🎯

💡 **Tips:**
- **Cập nhật code**: Mỗi khi bạn thay đổi code, chỉ cần chạy lại `npm run build` và **push lại lên branch `gh-pages`**.
- **Kiểm tra lỗi**: Nếu có lỗi khi deploy, kiểm tra tab **Actions** trên GitHub để xem log chi tiết.

🛠 **Chúc các bạn thành công!** 🎯