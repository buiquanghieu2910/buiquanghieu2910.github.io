---
layout: post
title: 🧩 Serializable trong Java là gì? Cách sử dụng và lưu ý quan trọng
date: 2025-03-21 19:08 +0700
categories: [Programming Language, Java]
tags:
  [
    Serializable trong Java,
    Serialization là gì,
    serialVersionUID là gì,
  ]
image:
  path: /assets/img/serializable-trong-java-la-gi/Serialization-in-Java.jpg
---

## 🎯 Serializable là gì?
**Serializable** trong Java là một **marker interface** (không có phương thức) trong package `java.io`, cho phép **chuyển đổi đối tượng (object) thành chuỗi byte** để:

- ✅ Lưu trữ vào file, database (persistence)
- ✅ Gửi qua mạng (network)
- ✅ Gửi giữa các tiến trình (IPC)

Quá trình chuyển đối tượng thành byte gọi là **serialization**, ngược lại là **deserialization**.

---

## 🔧 Cách dùng Serializable trong Java

### 1. Cài đặt interface `Serializable`
```java
import java.io.Serializable;

public class User implements Serializable {
    private String name;
    private int age;

    // constructor, getter, setter
}
```

### 2. Ghi object ra file (serialize)
```java
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("user.ser"));
out.writeObject(user);
out.close();
```

### 3. Đọc object từ file (deserialize)
```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("user.ser"));
User user = (User) in.readObject();
in.close();
```

---

## 📌 `serialVersionUID` là gì?
```java
private static final long serialVersionUID = 1L;
```
- Là ID phiên bản của class.
- Giúp JVM kiểm tra tính tương thích khi deserialize object.
- Nên khai báo thủ công để tránh lỗi khi class thay đổi nhưng dữ liệu cũ vẫn được load.

---

## 🚫 Biến không muốn serialize thì sao?
Dùng từ khóa `transient`:
```java
private transient String password;
```
- Biến `transient` sẽ không được ghi vào byte stream khi serialize.

---

## ✅ Khi nào nên dùng Serializable?
- Khi cần **lưu trạng thái object** ra file, database...
- Khi muốn **gửi object qua mạng (Socket, RMI, gRPC)**
- Khi dùng thư viện/framework yêu cầu hỗ trợ Serializable (ví dụ: Java Messaging, caching, session clustering)

---

## ❌ Những điều cần lưu ý
- Không hỗ trợ tốt cho versioning nếu không dùng `serialVersionUID`
- Không tự động serialize các object bên trong không implement `Serializable`
- Hiệu suất thấp hơn so với thư viện như **Kryo, Protobuf** nếu cần performance cao

---

## 🧠 So sánh: Serializable vs Externalizable

| Tiêu chí             | Serializable        | Externalizable        |
|----------------------|---------------------|------------------------|
| Ghi & đọc dữ liệu    | Tự động             | Lập trình viên tự định nghĩa |
| Đơn giản             | ✅ Dễ dùng          | ❌ Phức tạp hơn         |
| Hiệu suất            | Trung bình          | Tốt hơn nếu viết chuẩn |
| Linh hoạt            | ❌ Ít kiểm soát      | ✅ Hoàn toàn kiểm soát |

---

## 🧠 Tổng kết
- `Serializable` là cách đơn giản, nhanh chóng để **biến object thành chuỗi byte** và khôi phục lại.
- Dùng tốt cho các tác vụ lưu trữ, truyền dữ liệu, session, caching...

🚀 **Hiểu rõ Serializable giúp bạn làm chủ luồng dữ liệu object trong Java – một kỹ năng quan trọng trong lập trình thực tế!**