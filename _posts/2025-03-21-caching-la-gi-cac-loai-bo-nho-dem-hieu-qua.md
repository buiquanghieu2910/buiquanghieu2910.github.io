---
layout: post
title: 🚀 Giới thiệu về Caching – Tăng tốc hệ thống hiệu quả
date: 2025-03-21 20:19 +0700
categories: [Technology]
tags:
  [
    Caching là gì,
    Các loại bộ nhớ đệm,
  ]
image:
  path: /assets/img/caching-la-gi-cac-loai-bo-nho-dem-hieu-qua/cache.jpg
---

## 🎯 Caching là gì?
**Caching (bộ nhớ đệm)** là kỹ thuật lưu trữ tạm thời dữ liệu được truy xuất thường xuyên, nhằm **tăng tốc độ truy cập**, **giảm tải cho hệ thống backend hoặc database**, và **tối ưu hóa trải nghiệm người dùng**.

Thay vì mỗi lần người dùng truy cập đều phải tính toán lại hoặc truy xuất từ database, hệ thống sẽ lấy dữ liệu từ **cache** – nơi đã lưu sẵn kết quả ở lần truy cập trước. Điều này giúp giảm thời gian xử lý và cải thiện hiệu suất hệ thống.

📌 Ví dụ đơn giản:
- Khi bạn truy cập một trang web lần đầu, trình duyệt sẽ tải toàn bộ nội dung.
- Lần sau truy cập lại, phần nội dung đó có thể được tải từ **cache** trên trình duyệt → **nhanh hơn rất nhiều**.

---

## ⚙️ Các loại caching phổ biến

### 🖥️ 1. **Client-side caching (Frontend)**
Lưu dữ liệu ở phía người dùng (trình duyệt hoặc thiết bị).
- **Browser Cache**: Lưu HTML, CSS, JS, hình ảnh tĩnh. Trình duyệt sẽ dùng lại nếu chưa hết hạn.
- **LocalStorage / SessionStorage**: Lưu dữ liệu JSON như token, profile, cache response của API.
- **Service Worker Cache (Progressive Web App)**: Giúp website hoạt động offline.

### 🗄️ 2. **Server-side caching (Backend)**
Lưu dữ liệu trên máy chủ để tránh xử lý lại mỗi lần request.
- **Page Cache**: Lưu toàn bộ trang HTML render sẵn.
- **Fragment Cache**: Cache từng phần của trang (VD: sidebar, banner).
- **Data Cache**: Lưu dữ liệu lấy từ database hoặc API.
- **Query Cache**: Cache kết quả truy vấn SQL hoặc MongoDB.

### 🌐 3. **CDN cache (Content Delivery Network)**
Dịch vụ trung gian giúp cache và phân phối nội dung tĩnh (image, CSS, JS, video) từ server gần nhất với người dùng.
- Ví dụ: **Cloudflare, AWS CloudFront, Akamai, Fastly**.

### 🧠 4. **Application-level cache (Logic hoặc trạng thái)**
Dành cho lập trình viên frontend/backend:
- **React Query, SWR** (React): Cache API response, hỗ trợ revalidation.
- **Apollo Client** (GraphQL): Cache query theo schema.
- **In-memory Cache (Node.js, Python)**: Lưu biến toàn cục tạm thời trong bộ nhớ RAM.

---

## 🔥 Lợi ích của caching
✅ **Tăng hiệu suất hệ thống** – Giảm thời gian phản hồi cho người dùng.
✅ **Giảm tải cho server/database** – Tránh việc xử lý lặp lại.
✅ **Tiết kiệm băng thông và chi phí** – Đặc biệt khi dùng CDN.
✅ **Tăng độ ổn định hệ thống** – Hệ thống vẫn phản hồi dù backend tạm thời bị quá tải.
✅ **Tối ưu SEO & Core Web Vitals** – Nhờ vào tốc độ tải trang nhanh hơn.

---

## ❗️Nhược điểm & lưu ý
❌ **Dữ liệu bị cũ (stale)** nếu không cập nhật đúng thời điểm.  
❌ **Khó invalidate (làm mới) cache chính xác khi dữ liệu thay đổi.**  
❌ **Bộ nhớ RAM bị chiếm dụng nếu dùng in-memory quá nhiều.**  
❌ **Tăng độ phức tạp khi kết hợp nhiều tầng cache (CDN + App + DB).**

---

## 🧠 Một số kỹ thuật & công cụ caching phổ biến

| **Loại Cache**       | **Công nghệ phổ biến** |
|----------------------|-------------------------|
| In-memory cache      | `Redis`, `Memcached` |
| CDN cache            | `Cloudflare`, `CloudFront`, `Fastly` |
| Application cache    | `React Query`, `Apollo`, `SWR` |
| Database cache       | `MySQL Query Cache`, `PostgreSQL Materialized View` |
| HTTP header cache    | `Cache-Control`, `ETag`, `Last-Modified` |
| File-based caching   | Laravel Cache, Rails Fragment Caching |

📌 **Redis** thường là lựa chọn số 1 cho caching tốc độ cao phía server.

---

## 🔄 Cache Invalidation – Làm mới dữ liệu cache

### Câu hỏi quan trọng: **"Khi nào dữ liệu trong cache cần làm mới?"**

### 📅 1. **Time-based (TTL - Time To Live)**
- Dữ liệu cache tự động hết hạn sau một khoảng thời gian.
- Ví dụ: Cache bài viết blog trong 5 phút.

### 🔄 2. **Event-based**
- Invalidate cache ngay khi có hành động cập nhật (VD: admin cập nhật bài viết → xóa cache bài viết đó).

### 👨‍💻 3. **Manual refresh**
- Cho phép người dùng hoặc quản trị viên bấm nút "Làm mới cache".

### 🤖 4. **Stale-while-revalidate** (cơ chế hiện đại)
- Trả về cache cũ ngay lập tức, nhưng đồng thời lấy dữ liệu mới để cập nhật lại cache.
- Được áp dụng trong **SWR, React Query**, hoặc **CDN như Cloudflare**.

---

## 🧪 Các chiến lược caching phổ biến

| **Chiến lược**                  | **Mô tả** |
|--------------------------------|----------|
| **Cache Aside** (Lazy loading) | Chỉ cache khi có request truy cập và chưa có cache. |
| **Write Through**              | Mỗi khi ghi vào database → ghi vào cache luôn. |
| **Read Through**              | App chỉ truy cập cache → nếu cache miss, cache sẽ gọi DB và lưu kết quả lại. |
| **Refresh Ahead**              | Làm mới cache định kỳ trước khi hết hạn TTL. |

---

## 📦 Khi nào nên dùng caching?
✔ Dữ liệu được truy cập lặp lại nhiều lần.  
✔ Hệ thống có lượng người dùng lớn, request cao.  
✔ API hoặc database có thời gian phản hồi lâu.  
✔ Nội dung ít thay đổi thường xuyên (bài viết, thông tin sản phẩm...).  
❌ Không nên cache nếu dữ liệu cần tính toán real-time như: đơn hàng, tài chính, thống kê liên tục.

---

## 🏆 Kết luận
Caching là một trong những kỹ thuật **cốt lõi** để xây dựng hệ thống **nhanh hơn, tiết kiệm hơn và mở rộng tốt hơn**.

✅ Hiểu đúng caching → Tránh lỗi stale data và tăng hiệu suất.  
✅ Biết chọn loại cache phù hợp → Giảm chi phí và tăng trải nghiệm người dùng.  
✅ Bắt đầu từ đơn giản: **browser cache, Redis, hoặc CDN** là những cách hiệu quả nhất để cải thiện tốc độ ứng dụng ngay lập tức.

🚀 **Bạn đang làm frontend, backend hay DevOps? Caching đều sẽ giúp bạn tạo ra hệ thống mạnh hơn!** 😎