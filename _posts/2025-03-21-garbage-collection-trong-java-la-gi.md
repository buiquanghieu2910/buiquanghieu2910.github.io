---
layout: post
title: 🗑️ Garbage Collection trong Java – Cơ chế thu gom rác tự động
date: 2025-03-21 18:59 +0700
categories: [Programming Language, Java]
tags:
  [
    Garbage Collection trong Java,
    Java GC là gì,
    Cơ chế thu gom rác trong JVM,
    Thu hồi bộ nhớ tự động trong Java,
    Java memory management,
  ]
image:
  path: /assets/img/garbage-collection-trong-java-la-gi/gc.jpg
---

## 🎯 Garbage Collection là gì?
**Garbage Collection (GC)** trong Java là quá trình **tự động thu hồi bộ nhớ** của các đối tượng không còn được sử dụng. JVM sẽ định kỳ quét các object không còn tham chiếu và giải phóng bộ nhớ mà chúng chiếm giữ.

📌 Nhờ GC, lập trình viên Java **không cần tự quản lý cấp phát và giải phóng bộ nhớ** như trong C/C++, giúp giảm thiểu lỗi memory leak, dangling pointer...

---

## 🧠 Tại sao cần Garbage Collection?
- Java cấp phát object trong Heap Memory.
- Khi một object không còn được bất kỳ biến hoặc thread nào tham chiếu → nó trở thành **garbage**.
- Nếu không thu gom → ứng dụng sẽ bị **tràn bộ nhớ (OutOfMemoryError)**.

---

## 🔍 Khi nào một object bị coi là "rác"?
- Khi không còn tham chiếu nào trỏ đến object đó.
- Ví dụ:
```java
MyObject obj = new MyObject();
obj = null; // MyObject trước đó giờ trở thành rác
```

---

## ⚙️ Cơ chế hoạt động của GC trong JVM
JVM chia **heap memory** thành các vùng:

| Vùng nhớ      | Mô tả |
|---------------|------|
| **Young Generation** | Chứa object mới tạo. GC xảy ra thường xuyên hơn (Minor GC). |
| **Old Generation**   | Chứa object sống lâu. GC xảy ra ít hơn (Major GC). |
| **Metaspace**        | Lưu trữ metadata của class (từ Java 8 thay thế PermGen). |

### 📌 Quá trình GC thường gồm 2 pha:
1. **Mark phase**: Đánh dấu các object đang được tham chiếu.
2. **Sweep/Compact phase**: Dọn dẹp các object không được đánh dấu và tái tổ chức lại heap.

---

## 🔧 Các thuật toán GC phổ biến trong JVM

| GC Algorithm       | Mô tả |
|---------------------|------|
| **Serial GC**       | Dùng cho máy đơn nhân, đơn luồng. Tốt cho app nhỏ. |
| **Parallel GC**     | Dùng nhiều thread để GC. Hiệu suất tốt với hệ thống có nhiều core. |
| **CMS (Concurrent Mark Sweep)** | Giảm thời gian stop-the-world. Thích hợp cho app cần phản hồi nhanh. |
| **G1 GC**           | Chia heap thành nhiều vùng nhỏ (region), tối ưu GC theo vùng. Default từ Java 9+. |
| **ZGC, Shenandoah** | GC thế hệ mới, latency rất thấp, dùng cho ứng dụng lớn, real-time. |

---

## 🛠 Cách kích hoạt GC thủ công (ít dùng):
```java
System.gc(); // Gợi ý JVM thực hiện GC, không đảm bảo chạy ngay
```

---

## 📊 Theo dõi & tối ưu GC
- Dùng flag JVM:
  - `-XX:+PrintGCDetails`, `-Xlog:gc`, `-Xmx`, `-Xms`, `-XX:+UseG1GC`
- Dùng công cụ:
  - **VisualVM**
  - **JConsole**
  - **Java Mission Control**

---

## ✅ Ưu điểm của GC trong Java
✔ Giải phóng bộ nhớ tự động  
✔ Giảm lỗi lập trình do quản lý bộ nhớ thủ công  
✔ Hỗ trợ nhiều chiến lược GC cho các use case khác nhau  
✔ Tích hợp tốt với các công cụ theo dõi hiệu suất

---

## ❌ Nhược điểm
❌ GC vẫn gây **pause (stop-the-world)** dù có tối ưu  
❌ Nếu không cấu hình đúng → dễ gây **GC overhead**, hiệu năng giảm  
❌ Không kiểm soát trực tiếp thời điểm GC chạy

---

## 🧠 Tổng kết
- **Garbage Collection** là một phần cốt lõi giúp Java quản lý bộ nhớ hiệu quả và an toàn.
- Việc hiểu cách hoạt động của GC giúp bạn **viết code tối ưu hơn, tránh leak memory, và cải thiện hiệu năng hệ thống**.

🚀 **Nếu bạn đang làm việc với ứng dụng Java lớn, đừng bỏ qua cách JVM thu gom rác!**