---
layout: post
title: ☕ Lambda Expression và Stream API trong Java – Hiện đại hóa code Java
date: 2025-03-21 20:09 +0700
categories: [Programming Language, Java]
tags:
  [
    Lambda trong Java,
    Stream API Java,
    Biểu thức lambda Java,
    Xử lý dữ liệu với stream,
  ]
image:
  path: /assets/img/lambda-stream-api-trong-java/stream-api.jpg
---

## 🎯 Lambda Expression là gì?
**Lambda Expression** (biểu thức lambda) là cú pháp rút gọn để viết các **functional interface** (interface chỉ có một phương thức).

Lambda giúp:
- ✅ Viết code ngắn gọn, dễ đọc.
- ✅ Giảm boilerplate khi làm việc với interface như `Runnable`, `Comparator`, `Predicate`...

### 🔧 Cú pháp:
```java
(parameters) -> { body }
```

### 🔍 Ví dụ:
```java
// Trước Java 8
Runnable r1 = new Runnable() {
    public void run() {
        System.out.println("Hello");
    }
};

// Sau Java 8 với Lambda
Runnable r2 = () -> System.out.println("Hello");
```

---

## 📦 Functional Interface là gì?
- Interface chỉ có duy nhất **một phương thức trừu tượng**.
- Có thể annotate bằng `@FunctionalInterface`

```java
@FunctionalInterface
interface Greeting {
    void sayHello(String name);
}

Greeting g = (name) -> System.out.println("Hi, " + name);
g.sayHello("Java");
```

---

## 🔁 Stream API là gì?
**Stream API** cho phép xử lý tập hợp dữ liệu (Collection) theo kiểu **functional programming**.

- Hỗ trợ filter, map, sort, collect...
- Cho phép xử lý **tuần tự hoặc song song** (parallel)

### 🔍 Ví dụ:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Duyệt và in tên dài hơn 3 ký tự
names.stream()
     .filter(name -> name.length() > 3)
     .forEach(System.out::println);
```

---

## 🔧 Một số phương thức phổ biến trong Stream API

### 1. `filter()` – Lọc phần tử theo điều kiện
```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);
List<Integer> even = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
System.out.println(even); // [2, 4]
```

### 2. `map()` – Biến đổi phần tử
```java
List<String> names = List.of("Alice", "Bob");
List<Integer> lengths = names.stream()
    .map(String::length)
    .collect(Collectors.toList());
System.out.println(lengths); // [5, 3]
```

### 3. `sorted()` – Sắp xếp phần tử
```java
List<String> unsorted = List.of("Charlie", "Alice", "Bob");
List<String> sorted = unsorted.stream()
    .sorted()
    .collect(Collectors.toList());
System.out.println(sorted); // [Alice, Bob, Charlie]
```

### 4. `collect()` – Thu thập dữ liệu
```java
List<String> names = List.of("A", "B", "C");
String result = names.stream()
    .collect(Collectors.joining(", "));
System.out.println(result); // A, B, C
```

### 5. `limit()` và `skip()` – Giới hạn hoặc bỏ qua phần tử
```java
List<Integer> data = List.of(1, 2, 3, 4, 5);

List<Integer> firstTwo = data.stream()
    .limit(2)
    .collect(Collectors.toList());
System.out.println(firstTwo); // [1, 2]

List<Integer> skipTwo = data.stream()
    .skip(2)
    .collect(Collectors.toList());
System.out.println(skipTwo); // [3, 4, 5]
```

### 6. `count()` – Đếm số lượng phần tử thỏa điều kiện
```java
long count = data.stream()
    .filter(n -> n > 3)
    .count();
System.out.println(count); // 2
```

### 7. `anyMatch()`, `allMatch()`, `noneMatch()` – Kiểm tra điều kiện
```java
boolean hasEven = data.stream().anyMatch(n -> n % 2 == 0); // true
boolean allPositive = data.stream().allMatch(n -> n > 0);  // true
boolean noneNegative = data.stream().noneMatch(n -> n < 0); // true
```

---

## 🧠 Khi nào nên dùng Lambda và Stream?
✅ Khi muốn xử lý Collection ngắn gọn, sạch sẽ  
✅ Khi viết code functional như filter, map, reduce  
✅ Khi cần xử lý dữ liệu lớn với **parallel stream**  
✅ Khi làm việc với API như Java 8 DateTime, Optional, CompletableFuture

---

## ⚠️ Lưu ý khi dùng Stream
- **Không nên lồng nhiều stream gây khó đọc**
- Stream là **chỉ được dùng 1 lần** (không reuse)
- Dùng `.parallel()` cẩn thận với thread-unsafe code

---

## 🌟 Tầm quan trọng của Lambda và Stream API

Việc sử dụng Lambda Expression và Stream API không chỉ là vấn đề "cú pháp ngắn gọn" – mà còn mang lại **nhiều lợi ích lớn trong phát triển phần mềm hiện đại**, bao gồm:

- 🚀 **Cải thiện khả năng đọc và bảo trì code**: Code functional rõ ràng hơn so với vòng lặp truyền thống.
- 🔄 **Giảm lỗi logic**: Hạn chế biến trung gian, cấu trúc rõ ràng hơn.
- ⚙️ **Tăng khả năng mở rộng và tái sử dụng**: Nhờ việc phân tách rõ logic xử lý và dữ liệu.
- 🧵 **Tận dụng đa luồng dễ dàng**: Stream có thể dễ dàng chuyển sang `parallelStream()` để tăng hiệu năng xử lý với dữ liệu lớn.
- 🧪 **Tối ưu cho kiểm thử (testability)**: Viết hàm xử lý riêng biệt, dễ mock và kiểm tra.

✅ Với Lambda và Stream, Java trở nên linh hoạt hơn, hiện đại hơn, và dễ dàng bắt kịp với xu hướng functional programming đang phổ biến hiện nay.

---

## 🚀 Tổng kết
- **Lambda Expression** giúp code Java ngắn gọn hơn với biểu thức hàm.
- **Stream API** là công cụ mạnh mẽ giúp xử lý dữ liệu theo hướng functional, sạch và hiệu quả.

👉 Nếu bạn đang lập trình Java hiện đại (Java 8+), Lambda và Stream là công cụ không thể thiếu để nâng cấp chất lượng và hiệu suất code!