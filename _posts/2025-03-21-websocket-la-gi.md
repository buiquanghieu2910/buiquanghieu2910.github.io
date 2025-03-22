---
layout: post
title: 🔌 WebSocket là gì? Ứng dụng và khi nào nên sử dụng
date: 2025-03-21 21:27 +0700
categories: [Technology]
tags:
  [
    WebSocket là gì,
    Công nghệ WebSocket,
    Realtime communication,
    So sánh WebSocket và SSE,
  ]
image:
  path: /assets/img/websocket-la-gi/websocket.jpg
---

## 🎯 WebSocket là gì?
**WebSocket** là giao thức mạng cung cấp một **kết nối song công (full-duplex)**, lâu dài và hiệu quả giữa **client và server** thông qua **một kết nối TCP duy nhất**.

Không giống như HTTP truyền thống (request-response), WebSocket cho phép **client và server có thể gửi dữ liệu cho nhau bất kỳ lúc nào**, không cần request mới.

---

## 🔧 Cách hoạt động của WebSocket
1. Client gửi request nâng cấp kết nối (HTTP handshake → WebSocket handshake).
2. Nếu server đồng ý, kết nối chuyển sang chế độ WebSocket.
3. Cả hai bên có thể gửi/nhận dữ liệu qua kết nối này **liên tục, theo thời gian thực**.

### Ví dụ đơn giản (client JavaScript):
```javascript
const socket = new WebSocket('ws://localhost:3000');

socket.onopen = () => {
  console.log('Kết nối thành công');
  socket.send('Xin chào server!');
};

socket.onmessage = (event) => {
  console.log('Tin nhắn từ server:', event.data);
};
```

### Server WebSocket (Node.js - ws):
```javascript
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 3000 });

wss.on('connection', ws => {
  ws.on('message', message => {
    console.log('Client gửi:', message);
    ws.send('Server nhận được: ' + message);
  });
});
```

---

## 🚀 Ứng dụng thực tế của WebSocket
- 💬 **Chat trực tuyến (real-time chat)**
- 🧠 **Trò chơi đa người chơi (multiplayer games)**
- 📦 **Theo dõi đơn hàng, vị trí vận chuyển**
- 📈 **Realtime dashboard, phân tích dữ liệu**
- ⚠️ **Giám sát hệ thống, thiết bị IoT, log streaming**
- 📡 **Ứng dụng remote control, video call**

---

## ✅ Ưu điểm của WebSocket
✔ Giao tiếp **2 chiều, thời gian thực**
✔ Tốc độ nhanh, hiệu quả hơn polling hoặc long-polling
✔ Kết nối được giữ liên tục – không cần tạo request mới
✔ Dữ liệu truyền có thể là JSON, văn bản, nhị phân
✔ Phù hợp cho ứng dụng realtime phức tạp

---

## ❌ Nhược điểm của WebSocket
❌ Không tương thích tốt với **HTTP cache, proxy, firewall**  
❌ Cần cấu hình riêng nếu chạy qua CDN hoặc bảo mật (WSS)  
❌ Phức tạp hơn để scale (cần sticky session hoặc Pub/Sub layer)  
❌ Không phù hợp nếu chỉ cần push dữ liệu 1 chiều đơn giản (dùng SSE)

---

## 🤔 Khi nào nên sử dụng WebSocket?
✅ Khi cần **giao tiếp 2 chiều liên tục giữa client và server**  
✅ Khi dữ liệu cần được cập nhật tức thì (chat, game, giao dịch tài chính)  
✅ Khi ứng dụng cần realtime và lượng dữ liệu trao đổi lớn, tần suất cao  

❌ Không nên dùng nếu:
- Chỉ cần đẩy dữ liệu 1 chiều từ server (→ nên dùng SSE)
- Hệ thống khó kiểm soát socket (quá nhiều client, không cần giữ kết nối)

---

## 🔄 So sánh nhanh WebSocket và SSE
| Tiêu chí               | WebSocket      | SSE (Server-Sent Events) |
|------------------------|----------------|---------------------------|
| Kết nối                | 2 chiều        | 1 chiều (server → client) |
| Chuẩn hỗ trợ           | WebSocket API  | EventSource API           |
| Hỗ trợ trình duyệt     | Tốt (trừ IE cũ) | Tốt (trừ IE, hạn chế mobile) |
| Proxy/CDN compatibility| ❌ Phức tạp    | ✅ Tốt hơn (vì HTTP)      |
| Tự động reconnect      | Cần code thêm  | ✅ Có sẵn                 |
| Ứng dụng phù hợp       | Chat, game     | Dashboard, notification   |

---

## 📊 So sánh WebSocket với các công nghệ realtime tương tự

### 🔧 Các công nghệ phổ biến

| Công nghệ             | Giao tiếp       | Ưu điểm chính                          | Nhược điểm                      |
|----------------------|------------------|----------------------------------------|----------------------------------|
| **WebSocket**        | 2 chiều          | Realtime mạnh, phản hồi nhanh           | Cần kiểm soát kết nối, khó scale |
| **SSE**              | 1 chiều (server → client) | Đơn giản, dễ dùng, hỗ trợ tốt proxy   | Không giao tiếp 2 chiều         |
| **Long Polling**     | 1 chiều (vòng lặp) | Dễ triển khai với HTTP                 | Độ trễ cao, không tối ưu tài nguyên |
| **MQTT**             | 2 chiều (Pub/Sub) | Nhẹ, phù hợp IoT, mạng yếu             | Cần broker riêng, không hỗ trợ trình duyệt |
| **GraphQL Subscriptions** | 2 chiều qua WebSocket | Tích hợp tốt với hệ GraphQL         | Cần cấu hình backend phức tạp   |

### 📌 Khi nào nên dùng công nghệ nào?

| Tình huống                          | Công nghệ phù hợp         |
|------------------------------------|----------------------------|
| Chat, game, realtime tương tác cao | WebSocket                 |
| Cập nhật đơn giản từ server        | SSE                       |
| Web cũ hoặc không hỗ trợ socket    | Long Polling              |
| IoT, thiết bị nhẹ, mạng yếu        | MQTT                      |
| Backend dùng GraphQL               | GraphQL Subscriptions     |

---
- **WebSocket** là công nghệ mạnh mẽ, tối ưu cho các ứng dụng **realtime, tương tác cao và cần giao tiếp liên tục 2 chiều**.
- Tuy nhiên, WebSocket đòi hỏi **quản lý kết nối chặt chẽ** và không phù hợp với mọi trường hợp.

🚀 **Nếu bạn đang phát triển ứng dụng realtime như chat, multiplayer, dashboard cập nhật liên tục... WebSocket là lựa chọn hoàn hảo!**