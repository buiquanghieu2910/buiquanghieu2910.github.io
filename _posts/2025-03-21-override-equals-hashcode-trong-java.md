---
layout: post
title: 🔁 Override `hashCode()` và `equals()` trong Java – Khi nào và tại sao?
date: 2025-03-21 20:02 +0700
categories: [Programming Language, Java]
tags:
  [
    Override equals hashCode Java,
    So sánh object trong Java,
    equals() và hashCode() là gì,
  ]
image:
  path: /assets/img/override-equals-hashcode-trong-java/equals-and-hashcode-in-java.jpg
---

## 🎯 Mục đích của `equals()` và `hashCode()`
Trong Java, hai phương thức này là **rất quan trọng để so sánh object** và dùng object làm **key trong các collection như `HashMap`, `HashSet`, `Hashtable`...**

- `equals()` → so sánh 2 object có "bằng nhau" hay không.
- `hashCode()` → trả về mã băm (hash code), dùng để xác định **vị trí lưu trữ object trong Hash-based collections**.

---

## 🧠 Mặc định thì sao?
Khi không override:
- `equals()` so sánh theo địa chỉ bộ nhớ (==).
- `hashCode()` trả về giá trị hash dựa trên địa chỉ object.

⛔ Điều này có thể gây lỗi logic nếu bạn so sánh theo giá trị field bên trong object.

---

## 🛠 Ví dụ không override
```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

Person p1 = new Person("Alice", 25);
Person p2 = new Person("Alice", 25);
System.out.println(p1.equals(p2)); // false ❌
```

---

## ✅ Cách override `equals()` và `hashCode()` chuẩn
```java
class Person {
    String name;
    int age;

    // Constructor, getter, setter...

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return age == person.age && name.equals(person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age); // từ Java 7
    }
}
```
✅ Sau khi override:
```java
Person p1 = new Person("Alice", 25);
Person p2 = new Person("Alice", 25);
System.out.println(p1.equals(p2)); // true ✅
```

---

## 📌 Tại sao phải override cả `equals()` và `hashCode()`?
Nếu chỉ override `equals()` mà **không override `hashCode()`**, các collection như `HashSet`, `HashMap` sẽ hoạt động **không đúng**.

### Ví dụ:
```java
Set<Person> set = new HashSet<>();
set.add(new Person("Alice", 25));
System.out.println(set.contains(new Person("Alice", 25))); // false ❌ nếu không có hashCode
```

📌 Quy tắc: **Nếu 2 object `a.equals(b)` là true → `a.hashCode() == b.hashCode()` phải đúng!**

---

## 🤔 Khi nào cần override?
- Khi object của bạn **dùng làm key cho HashMap**, hoặc phần tử trong HashSet.
- Khi bạn cần **so sánh object dựa trên giá trị thuộc tính thay vì địa chỉ**.
- Khi làm việc với framework cần equals/hashCode (Hibernate, JPA, caching...)

---

## 🧠 Tổng kết
- `equals()` giúp so sánh nội dung object.
- `hashCode()` hỗ trợ cấu trúc dữ liệu hash.
- **Nên override cả hai** nếu bạn cần làm việc với tập hợp (Set, Map) hoặc so sánh object theo logic riêng.

🚀 **Override đúng equals() và hashCode() là kỹ năng Java nền tảng – đừng bỏ qua nhé!**