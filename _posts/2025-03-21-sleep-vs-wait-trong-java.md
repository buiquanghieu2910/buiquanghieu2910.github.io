---
layout: post
title: 😴 Sự khác nhau giữa `sleep()` và `wait()` trong Java
date: 2025-03-21 19:04 +0700
categories: [Programming Language, Java]
tags:
  [
    sleep vs wait trong Java,
    Sự khác nhau giữa sleep và wait,
    Cách dùng wait và sleep Java,
    Java multithreading sleep wait,
  ]
image:
  path: /assets/img/sleep-vs-wait-trong-java/sleep-vs-wait-java.jpg
---

Trong Java, cả `sleep()` và `wait()` đều được dùng để **tạm dừng một luồng (thread)**, nhưng chúng có **mục đích, cách hoạt động và ngữ cảnh sử dụng hoàn toàn khác nhau**.

---

## 🧠 Tóm tắt sự khác biệt

| Tiêu chí                | `sleep()`                      | `wait()`                             |
|-------------------------|--------------------------------|--------------------------------------|
| Nằm trong class         | `Thread`                      | `Object`                             |
| Mục đích chính          | Tạm dừng thread một khoảng thời gian cố định | Tạm dừng thread cho đến khi nhận được thông báo (notify/notifyAll) |
| Cần đồng bộ (`synchronized`) | ❌ Không cần               | ✅ Bắt buộc phải dùng trong `synchronized` block |
| Giải phóng lock         | ❌ Không                       | ✅ Có                                 |
| Cách đánh thức          | Tự động sau thời gian         | Phải dùng `notify()` hoặc `notifyAll()` |
| Ném checked exception   | ✅ `InterruptedException`      | ✅ `InterruptedException`            |

---

## 🔧 Cách sử dụng `sleep()`
Phương thức `sleep()` dùng để **ngủ một khoảng thời gian (millisecond hoặc nanosecond)**.
```java
try {
    Thread.sleep(2000); // ngủ 2 giây
} catch (InterruptedException e) {
    e.printStackTrace();
}
```
✅ Không yêu cầu `synchronized`
❌ Không giải phóng lock nếu đang giữ

---

## 🔧 Cách sử dụng `wait()`
Phương thức `wait()` dùng để **chờ cho đến khi một điều kiện được thỏa mãn**, thường dùng trong các tình huống đồng bộ hóa tài nguyên chia sẻ.
```java
synchronized (sharedObject) {
    sharedObject.wait(); // chờ cho đến khi có notify()
}
```
Và ở thread khác:
```java
synchronized (sharedObject) {
    sharedObject.notify(); // đánh thức thread đang wait
}
```
✅ Phải nằm trong block `synchronized`
✅ Giải phóng lock cho thread khác truy cập

---

## 📌 Tình huống sử dụng
- Sử dụng `sleep()` khi bạn **chỉ muốn trì hoãn thực thi**.
  - Ví dụ: chờ giữa 2 lần retry kết nối, mô phỏng delay.
- Sử dụng `wait()` khi bạn **muốn phối hợp giữa nhiều thread** đang dùng chung tài nguyên.
  - Ví dụ: producer-consumer pattern, thread chờ dữ liệu sẵn sàng.

---

## ⚠️ Một số lưu ý quan trọng
- Gọi `wait()` mà không nằm trong block `synchronized` sẽ ném lỗi `IllegalMonitorStateException`
- Cả `sleep()` và `wait()` đều có thể bị **ngắt (interrupted)**, cần bắt `InterruptedException`
- Không nên lạm dụng `sleep()` thay cho cơ chế đồng bộ thread

---

## 🧠 Kết luận
- `sleep()` đơn giản, dùng để **tạm dừng thread theo thời gian**.
- `wait()` mạnh mẽ hơn, dùng để **phối hợp giữa các thread thông qua đồng bộ hóa**.

🚀 **Hiểu rõ sự khác biệt giữa `sleep()` và `wait()` là điều cần thiết để xử lý đa luồng (multithreading) trong Java một cách an toàn và hiệu quả!**