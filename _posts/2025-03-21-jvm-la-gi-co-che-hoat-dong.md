---
layout: post
title: 🔥 Giới thiệu về JVM – Java Virtual Machine
date: 2025-03-21 18:48 +0700
categories: [Java]
tags:
  [
    JVM là gì,
    Java Virtual Machine,
    Cơ chế hoạt động của JVM,
    JVM và JDK khác nhau như thế nào,
    Cấu trúc bộ nhớ JVM,
  ]
image:
  path: /assets/img/jvm-la-gi-co-che-hoat-dong/jvm.jpg
---

## 🎯 JVM là gì?
**JVM (Java Virtual Machine)** là một phần lõi của nền tảng Java, chịu trách nhiệm **chạy các chương trình Java** bằng cách chuyển đổi **bytecode thành mã máy tương ứng với hệ điều hành**.

👉 Nói cách khác, JVM chính là lý do tại sao Java có thể thực thi **"Write Once, Run Anywhere"** – viết một lần, chạy được ở mọi nơi có cài JVM.

---

## 🧠 Vai trò của JVM trong nền tảng Java
- **Thực thi mã bytecode**: Sau khi bạn compile mã Java (.java), nó sẽ thành bytecode (.class). JVM thực thi bytecode này.
- **Quản lý bộ nhớ**: Quản lý cấp phát và thu hồi bộ nhớ (Garbage Collection).
- **Đảm bảo tính bảo mật và di động**: Chạy trong sandbox, không phụ thuộc vào hệ điều hành.
- **Hỗ trợ đa ngôn ngữ**: Không chỉ Java, JVM còn hỗ trợ các ngôn ngữ khác như Kotlin, Scala, Groovy...

---

## ⚙️ Cơ chế hoạt động của JVM
Quá trình thực thi mã Java trên JVM bao gồm các bước:

### 1. **Compile mã nguồn thành Bytecode**
- File `.java` → Compile bằng `javac` → Thành file `.class` chứa bytecode.

### 2. **Class Loader (Trình nạp lớp)**
- JVM tải bytecode từ file `.class` vào bộ nhớ.
- Có 3 loại class loader:
  - **Bootstrap ClassLoader**: Nạp các lớp lõi từ thư viện Java (rt.jar).
  - **Extension ClassLoader**: Nạp các thư viện mở rộng.
  - **Application ClassLoader**: Nạp các lớp do người dùng định nghĩa.

### 3. **Bytecode Verifier (Trình kiểm tra bytecode)**
- Kiểm tra bytecode hợp lệ và an toàn (không vi phạm bộ nhớ).

### 4. **Execution Engine (Bộ máy thực thi)**
- Chịu trách nhiệm chạy chương trình thực tế.
- Gồm 2 thành phần chính:
  - **Interpreter**: Thực thi từng lệnh bytecode.
  - **JIT Compiler (Just-In-Time)**: Biên dịch bytecode thành mã máy khi chạy để tăng hiệu suất.

### 5. **Garbage Collector (Bộ gom rác)**
- Tự động thu hồi bộ nhớ không còn sử dụng.
- Có nhiều loại GC: Serial, Parallel, G1, ZGC...

---

## 🧪 Mô hình bộ nhớ trong JVM
JVM quản lý bộ nhớ theo 5 vùng chính:

| **Vùng nhớ**        | **Chức năng** |
|---------------------|----------------|
| **Method Area**     | Lưu thông tin class, method, field |
| **Heap**            | Lưu object, biến instance (dữ liệu lớn) |
| **Stack**           | Lưu thông tin gọi hàm, biến cục bộ |
| **PC Register**     | Lưu địa chỉ bytecode đang thực hiện |
| **Native Method Stack** | Dùng cho hàm native viết bằng C/C++ |

---

## 📌 JVM khác JDK và JRE như thế nào?
| Thành phần | Mô tả |
|------------|------|
| **JDK (Java Development Kit)** | Bao gồm: JRE + Compiler + Debugger (dành cho lập trình viên) |
| **JRE (Java Runtime Environment)** | Bao gồm: JVM + Thư viện chạy Java (dành cho chạy ứng dụng) |
| **JVM** | Thành phần lõi, thực thi bytecode |

---

## 🌍 JVM hỗ trợ đa nền tảng
- JVM tồn tại cho nhiều hệ điều hành: Windows, macOS, Linux.
- Bytecode là ngôn ngữ trung gian, có thể chạy được ở bất kỳ hệ điều hành nào cài đặt JVM tương ứng.

---

## 🧠 Tổng kết
- JVM là một thành phần quan trọng giúp Java có thể chạy đa nền tảng, an toàn và tối ưu hiệu suất.
- Hiểu về JVM giúp lập trình viên Java tối ưu hiệu năng, quản lý bộ nhớ tốt hơn, và hiểu sâu hơn về cách chương trình Java thực thi.

🚀 **Nếu bạn là lập trình viên Java, hãy làm bạn với JVM – nền tảng chạy mọi ứng dụng của bạn!** 😎