---
layout: post
title: 🔄 SSE (Server-Sent Events) là gì? Ứng dụng và khi nào nên sử dụng
date: 2025-03-21 21:23 +0700
categories: [Technology]
tags:
  [
    SSE là gì,
    Server-Sent Events,
    Công nghệ SSE trong web,
    Đẩy dữ liệu realtime bằng SSE,
    SSE vs WebSocket,
  ]
image:
  path: /assets/img/sse-server-sent-events-la-gi-ung-dung-thuc-te/sse.jpeg
---

## 🎯 SSE là gì?
**SSE (Server-Sent Events)** là một công nghệ cho phép **server gửi dữ liệu đến client theo thời gian thực** thông qua kết nối HTTP đơn hướng. Khác với WebSocket (2 chiều), SSE chỉ cho phép **server đẩy dữ liệu xuống client**.

SSE được xây dựng dựa trên chuẩn **EventSource API** của trình duyệt, rất đơn giản để sử dụng và triển khai.

---

## 🛠 Cách hoạt động của SSE
1. Client mở kết nối đến server bằng `EventSource`.
2. Server giữ kết nối mở và liên tục gửi dữ liệu dưới định dạng `text/event-stream`.
3. Client lắng nghe sự kiện từ server và xử lý dữ liệu được gửi đến.

### Ví dụ đơn giản (JavaScript - client):
```javascript
const eventSource = new EventSource('/events');

eventSource.onmessage = function (event) {
  console.log('Dữ liệu từ server:', event.data);
};
```

### Phía server (Node.js Express):
```javascript
app.get('/events', (req, res) => {
  res.setHeader('Content-Type', 'text/event-stream');
  res.setHeader('Cache-Control', 'no-cache');
  res.setHeader('Connection', 'keep-alive');

  setInterval(() => {
    res.write(`data: ${new Date().toISOString()}\n\n`);
  }, 2000);
});
```

---

## 🚀 Ứng dụng thực tế của SSE
- 🟢 **Thông báo thời gian thực** (real-time notifications)
- 📈 **Cập nhật biểu đồ, dashboard, giá cổ phiếu, dữ liệu IoT**
- 🧾 **Theo dõi trạng thái đơn hàng, tiến trình xử lý nền**
- 💬 **Hiển thị tin nhắn, log, sự kiện đang diễn ra**
- 🔍 **Tự động reload dữ liệu bảng mà không cần F5**

---

## ✅ Ưu điểm của SSE
✔ Giao tiếp đơn giản – chỉ cần HTTP, không cần socket riêng
✔ Hỗ trợ tốt qua proxy, tường lửa (vì là HTTP)
✔ Tích hợp dễ dàng với trình duyệt qua `EventSource`
✔ Hỗ trợ tự động reconnect khi mất kết nối
✔ Hiệu quả cho việc push dữ liệu **từ server xuống client**

---

## ❌ Nhược điểm của SSE
❌ Chỉ hỗ trợ kết nối đơn hướng (server → client)  
❌ Không hoạt động tốt trên **trình duyệt IE cũ** hoặc **không hỗ trợ mobile tốt như WebSocket**  
❌ Không tối ưu nếu cần giao tiếp 2 chiều như chat, game, remote control  
❌ Hạn chế số lượng kết nối đồng thời tùy thuộc vào server và browser

---

## 🤔 Khi nào nên sử dụng SSE?
✅ Khi bạn cần **đẩy dữ liệu real-time từ server xuống client**, nhưng **client không cần gửi ngược lại**.  
✅ Khi hệ thống cần sử dụng **HTTP thông thường**, dễ triển khai qua proxy/ngrok/CDN.  
✅ Khi bạn muốn tích hợp real-time nhẹ nhàng cho web app mà không cần setup phức tạp như WebSocket.

❌ Không nên dùng nếu:
- Cần giao tiếp 2 chiều thường xuyên → Dùng WebSocket.
- Ứng dụng mobile cần hỗ trợ sâu → Dùng WebSocket hoặc MQTT.
- Yêu cầu mức độ scale siêu lớn → Cần thiết kế kỹ lưỡng hoặc cân nhắc các giải pháp khác như Kafka Stream + WebSocket.

---

## 🧠 Tổng kết
- **SSE** là công nghệ hiệu quả, đơn giản và nhẹ nhàng để **đẩy dữ liệu thời gian thực từ server xuống client**.
- Dù không mạnh mẽ như WebSocket, nhưng SSE vẫn là **lựa chọn phù hợp cho nhiều use case thực tế** như dashboard, log viewer, thông báo hệ thống.

🚀 **Nếu bạn cần một giải pháp realtime đơn giản mà không cần client gửi ngược, hãy bắt đầu với SSE!**