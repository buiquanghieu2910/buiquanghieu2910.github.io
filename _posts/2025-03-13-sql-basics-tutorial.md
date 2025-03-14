---
layout: post
title: 📌 Hướng Dẫn Cơ Bản về SQL
date: 2025-03-13 20:53 +0700
categories: [SQL]
tags:
  [
    SQL Basic,
    Database
  ]
image:
  path: /assets/img/sql-basics-tutorial/sql.png
  width: 800
---
## 🔥 Giới Thiệu
SQL (Structured Query Language) là ngôn ngữ dùng để quản lý và thao tác cơ sở dữ liệu quan hệ (RDBMS). Dưới đây là các khái niệm và lệnh cơ bản trong SQL.

---

## 1️⃣ Các Loại Lệnh SQL Cơ Bản

### 🔹 1.1 Data Definition Language (DDL)
DDL dùng để định nghĩa cấu trúc của cơ sở dữ liệu, bao gồm:
- `CREATE`: Tạo database hoặc bảng mới.
- `ALTER`: Thay đổi cấu trúc của bảng.
- `DROP`: Xóa database hoặc bảng.
- `TRUNCATE`: Xóa toàn bộ dữ liệu trong bảng nhưng giữ nguyên cấu trúc.

Ví dụ:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 🔹 1.2 Data Manipulation Language (DML)
DML dùng để thao tác với dữ liệu trong bảng:
- `INSERT`: Thêm dữ liệu mới.
- `UPDATE`: Cập nhật dữ liệu.
- `DELETE`: Xóa dữ liệu.

Ví dụ:
```sql
INSERT INTO users (name, email) VALUES ('Nguyen Van A', 'a@example.com');
UPDATE users SET name = 'Nguyen Van B' WHERE id = 1;
DELETE FROM users WHERE id = 1;
```

### 🔹 1.3 Data Query Language (DQL)
DQL chủ yếu sử dụng lệnh `SELECT` để truy vấn dữ liệu:
```sql
SELECT * FROM users;
SELECT name, email FROM users WHERE id = 1;
```

### 🔹 1.4 Data Control Language (DCL)
DCL dùng để kiểm soát quyền truy cập:
- `GRANT`: Cấp quyền.
- `REVOKE`: Thu hồi quyền.

### 🔹 1.5 Transaction Control Language (TCL)
TCL dùng để quản lý giao dịch:
- `COMMIT`: Lưu thay đổi.
- `ROLLBACK`: Hoàn tác giao dịch.
- `SAVEPOINT`: Tạo điểm khôi phục trong giao dịch.

Ví dụ:
```sql
START TRANSACTION;
UPDATE users SET email = 'test@example.com' WHERE id = 1;
ROLLBACK;
```

---

## 2️⃣ Các Lệnh SQL Quan Trọng

### ✅ 2.1 Lệnh `SELECT`
```sql
SELECT name, email FROM users WHERE name LIKE 'Nguyen%';
```

### ✅ 2.2 Sử dụng `JOIN`
```sql
SELECT users.name, orders.total_price FROM users
JOIN orders ON users.id = orders.user_id;
```

### ✅ 2.3 Nhóm Dữ Liệu với `GROUP BY`
```sql
SELECT user_id, SUM(total_price) AS total FROM orders GROUP BY user_id;
```

### ✅ 2.4 Lọc Dữ Liệu với `HAVING`
```sql
SELECT user_id, SUM(total_price) AS total FROM orders
GROUP BY user_id HAVING total > 10000000;
```

### ✅ 2.5 Sắp xếp dữ liệu với `ORDER BY`
```sql
SELECT * FROM users ORDER BY created_at DESC;
```

---

## 📌 Tổng Kết
SQL là một ngôn ngữ mạnh mẽ giúp bạn quản lý dữ liệu hiệu quả. Hãy thực hành thường xuyên để nắm vững các lệnh cơ bản này! 🚀

