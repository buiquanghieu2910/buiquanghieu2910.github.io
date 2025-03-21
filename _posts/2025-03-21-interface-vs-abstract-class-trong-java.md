---
layout: post
title: 🔍 Sự khác nhau giữa Interface và Abstract Class trong Java
date: 2025-03-21 20:05 +0700
categories: [Programming Language, Java]
tags:
  [
    Interface vs abstract class trong Java,
    Sự khác nhau giữa interface và abstract,
    Java abstract class và interface,
  ]
image:
  path: /assets/img/interface-vs-abstract-class-trong-java/interface-vs-abstract-class-java.jpg
---

## 🎯 Interface và Abstract Class là gì?
Trong Java, cả **interface** và **abstract class** đều được dùng để **thiết kế cấu trúc cơ bản (blueprint)** cho các class con. Chúng là **công cụ của tính trừu tượng (abstraction)** trong lập trình hướng đối tượng (OOP).

- **Interface**: Định nghĩa **hành vi** mà một class phải thực hiện. Không chứa state hay logic (trước Java 8).
- **Abstract class**: Là class không thể khởi tạo, cung cấp một phần logic mặc định và cho phép class con **kế thừa và triển khai tiếp**.

👉 Mục tiêu chung: Cho phép xây dựng các hệ thống **mở rộng dễ dàng, thay đổi linh hoạt**.

---

## 🔧 So sánh chi tiết Interface vs Abstract class

| Tiêu chí                     | Interface                                      | Abstract Class                              |
|-----------------------------|------------------------------------------------|---------------------------------------------|
| Từ khóa                     | `interface`                                    | `abstract class`                            |
| Kế thừa                     | Class có thể implement nhiều interface         | Class chỉ kế thừa được 1 abstract class     |
| Phương thức cụ thể          | Từ Java 8: có `default` và `static` method     | Có thể có cả abstract và non-abstract method|
| Biến thành viên             | `public static final` (hằng số)                | Có mọi modifier: private, protected, etc.   |
| Constructor                 | ❌ Không có constructor                        | ✅ Có constructor                            |
| Access Modifier             | Chỉ được `public` (method/field)               | Linh hoạt hơn (`private`, `protected`, ...) |
| Dùng trong pattern/design   | Strategy, Adapter (API hợp đồng)               | Template Method (định nghĩa khung xử lý)    |

---

## 🧪 Ví dụ minh họa

### Interface:
```java
interface Animal {
    void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Gâu gâu");
    }
}
```
👉 Dùng để định nghĩa hành vi (sound), không quan tâm con chó kêu thế nào.

### Abstract class:
```java
abstract class Shape {
    abstract double getArea();

    void printType() {
        System.out.println("This is a shape");
    }
}

class Circle extends Shape {
    double radius;
    Circle(double r) { this.radius = r; }

    double getArea() {
        return Math.PI * radius * radius;
    }
}
```
👉 Dùng khi muốn vừa có logic mặc định (`printType()`), vừa yêu cầu class con định nghĩa `getArea()`.

---

## 📌 Khi nào nên dùng cái nào?

| Trường hợp sử dụng                        | Nên dùng gì?        | Giải thích |
|-------------------------------------------|----------------------|-------------|
| Chỉ định nghĩa hành vi, không cần trạng thái | ✅ Interface        | Gọn nhẹ, hỗ trợ đa kế thừa |
| Có logic chung cần tái sử dụng            | ✅ Abstract Class    | Kế thừa dùng lại logic |
| Framework, plugin cần định nghĩa hợp đồng | ✅ Interface         | Giúp tích hợp dễ dàng |
| Nhiều class cần kế thừa chung một cấu trúc | ✅ Abstract Class    | Dùng chung constructor, method mặc định |

---

## ⚠️ Lưu ý & Sai lầm thường gặp
- ❌ Không nên dùng abstract class nếu bạn **chỉ định nghĩa hành vi, không có state** → Interface phù hợp hơn.
- ❌ Không nên cố dùng interface để chia sẻ logic (vì không chứa logic trước Java 8).
- ✅ Kết hợp cả 2 khi cần: Interface để định nghĩa hợp đồng, Abstract class để cung cấp logic cơ bản.

---

## 🔄 Một số tính năng từ Java 8 trở đi:
- Interface có thể có **default method**, `static method`.
- Nhưng abstract class vẫn linh hoạt hơn khi có **state, constructor, access level đa dạng**.

---

## 🧠 Tổng kết
- **Interface** = "Bạn phải làm gì" – chỉ định hành vi mà class phải thực hiện.
- **Abstract class** = "Làm như thế nào" + một phần bạn phải làm – cung cấp logic + khung xử lý.

🚀 **Hiểu rõ sự khác nhau giữa Interface và Abstract Class sẽ giúp bạn thiết kế hệ thống phần mềm linh hoạt, mở rộng dễ dàng và áp dụng tốt các nguyên lý SOLID!**