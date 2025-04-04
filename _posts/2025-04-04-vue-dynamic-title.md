---
layout: post
title: 🚀 Hướng dẫn cấu hình Dynamic Title trong Vue.js
date: 2025-04-04 23:01 +0700
categories: [Web Development, VueJs]
tags:
  [
    Vue.js, 
    dynamic title, 
    Vue Router, 
    change title dynamically, 
    SEO, 
    web development
  ]
image:
  path: /assets/img/vue-dynamic-title/vue-dynamic-title.jpg
---

## 🎯 **Giới thiệu về Dynamic Title**
Trong các ứng dụng web hiện đại, việc thay đổi tiêu đề trang (title) dựa trên từng trang cụ thể là rất quan trọng để cải thiện trải nghiệm người dùng và tối ưu hóa SEO. Trong Vue.js, bạn có thể cấu hình **dynamic title** bằng cách sử dụng **Vue Router** để thay đổi tiêu đề của trang một cách tự động khi người dùng chuyển giữa các route.

## 🛠️ **Cấu hình Dynamic Title trong Vue.js**

Để thực hiện cấu hình dynamic title trong Vue.js, bạn có thể sử dụng **Vue Router** và một số cấu hình trong file `router/index.js` của bạn. Dưới đây là các bước chi tiết.

### 🛠️ **Bước 1: Định nghĩa metadata cho mỗi route**
Đầu tiên, bạn cần thêm thông tin về tiêu đề của trang vào trong phần `meta` của mỗi route trong cấu hình router. Điều này giúp bạn xác định tiêu đề cho mỗi trang.

#### Ví dụ cấu hình route trong `router/index.js`:
```javascript
import { createRouter, createWebHistory } from 'vue-router';
import HomeView from '../views/HomeView.vue';

let routes = [
  {
    path: '/',
    name: 'home',
    component: HomeView,
    meta: {
      // Đặt tiêu đề trang cho route này
      title: 'Home - MyWebsite'
    }
  }
]

const router = createRouter({
  history: createWebHistory(),
  routes,
});

router.beforeEach((to, from, next) => {
  // Cập nhật tiêu đề trang dựa trên route
  document.title = to.meta.title || 'Default Title';
  next();
});

export default router;
```

### 🛠️ **Bước 2: Cập nhật tiêu đề trang trong Vue Router**
Sử dụng phương thức `beforeEach` của Vue Router để thay đổi tiêu đề trang mỗi khi người dùng chuyển sang một route mới. Mỗi route có thể có một `meta` với thông tin tiêu đề trang. Trong ví dụ trên, tiêu đề sẽ được lấy từ `to.meta.title` và được cập nhật vào thẻ `<title>` của trang.

#### Chi tiết mã:

```javascript
router.beforeEach((to, from, next) => {
  // Cập nhật tiêu đề trang dựa trên route
  document.title = to.meta.title || 'Default Title';
  next();
});
```

#### Giải thích:
- `document.title = to.meta.title || 'Default Title';`: Đây là dòng mã sẽ cập nhật tiêu đề trang bằng giá trị `title` từ `meta` trong cấu hình route. Nếu không có tiêu đề nào trong `meta`, sẽ mặc định là "Default Title".

### 🧑‍💻 **Bước 3: Đảm bảo các route khác có tiêu đề riêng**
Bạn có thể tiếp tục thêm nhiều route vào cấu hình và chỉ định tiêu đề cho từng route. Việc cấu hình tiêu đề cho mỗi route giúp người dùng dễ dàng nhận diện trang mà họ đang truy cập.

#### Ví dụ thêm một số route khác:

```javascript
let routes = [
  {
    path: '/',
    name: 'home',
    component: HomeView,
    meta: {
      title: 'Home - MyWebsite'
    }
  },
  {
    path: '/about',
    name: 'about',
    component: AboutView,
    meta: {
      title: 'About Us - MyWebsite'
    }
  },
  {
    path: '/contact',
    name: 'contact',
    component: ContactView,
    meta: {
      title: 'Contact - MyWebsite'
    }
  }
]
```

## 🚀 **Tổng kết**
Việc cấu hình **dynamic title** trong Vue.js giúp bạn thay đổi tiêu đề của trang khi người dùng chuyển qua các route khác nhau, làm cho trang web của bạn trở nên thân thiện hơn với người dùng và dễ dàng tối ưu hóa SEO.

- **Đặt tiêu đề cho mỗi route**: Dễ dàng cập nhật tiêu đề cho từng trang.
- **Cập nhật tiêu đề tự động khi thay đổi route**: Vue Router sẽ giúp bạn thay đổi tiêu đề mỗi khi người dùng chuyển trang.