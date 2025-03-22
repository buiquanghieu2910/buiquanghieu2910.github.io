---
layout: post
title: 🔐 Transaction trong cơ sở dữ liệu – Hiểu và ứng dụng trong backend
date: 2025-03-22 13:21 +0700
categories: [Database & Data Engineering]
tags:
  [
    Transaction là gì,
    Transaction trong cơ sở dữ liệu,
    Database transaction,
    Tính chất ACID,
    Cách dùng transaction trong backend,
  ]
image:
  path: /assets/img/transaction-database-la-gi-ung-dung-trong-backend/transaction.jpg
---

## 🎯 Transaction là gì?
**Transaction** (giao dịch) trong cơ sở dữ liệu là một đơn vị xử lý **bao gồm một hoặc nhiều thao tác** (insert, update, delete...) mà được thực hiện như **một khối thống nhất**.

Một transaction sẽ chỉ thành công nếu **tất cả các thao tác bên trong nó đều thành công**. Nếu có bất kỳ lỗi nào xảy ra, toàn bộ transaction sẽ bị **rollback** (quay về trạng thái trước khi thực hiện).

---

## 🔄 Ví dụ đơn giản
Chuyển tiền từ tài khoản A sang B:
1. Trừ tiền từ A
2. Cộng tiền vào B

➡ Nếu thao tác 1 thành công nhưng thao tác 2 thất bại, tiền sẽ "mất" nếu không có transaction.

---

## 📦 Tính chất ACID trong Transaction

| Thành phần | Ý nghĩa |
|------------|---------|
| **Atomicity** | Tính nguyên tử – tất cả hoặc không gì cả |
| **Consistency** | Tính nhất quán – dữ liệu luôn ở trạng thái hợp lệ |
| **Isolation** | Tính cô lập – các transaction không ảnh hưởng nhau |
| **Durability** | Tính bền vững – sau khi commit, dữ liệu được lưu vĩnh viễn |

---

## 📌 Khi nào nên sử dụng Transaction?
✔ Khi thao tác liên quan đến **nhiều bảng hoặc nhiều bước cập nhật** dữ liệu liên quan đến nhau.
✔ Khi yêu cầu **tính toàn vẹn dữ liệu** cực cao (banking, e-commerce, logistics...)
✔ Khi cần đảm bảo không có dữ liệu "trung gian" gây lỗi logic.
✔ Khi thao tác ghi phức tạp và cần rollback nếu có lỗi.

---

## 🛠 Ứng dụng Transaction trong các công nghệ Backend

### ✅ Spring Boot (Java)
Sử dụng `@Transactional` để đánh dấu method cần transaction:
```java
@Service
public class PaymentService {
  @Transactional
  public void transferMoney(Long fromId, Long toId, BigDecimal amount) {
    accountRepo.debit(fromId, amount);
    accountRepo.credit(toId, amount);
  }
}
```

### ✅ Django ORM (Python)
```python
from django.db import transaction

@transaction.atomic
def transfer_money(from_acc, to_acc, amount):
    from_acc.balance -= amount
    from_acc.save()
    to_acc.balance += amount
    to_acc.save()
```

### ✅ Node.js (Sequelize)
```javascript
const t = await sequelize.transaction();
try {
  await Account.decrement('balance', { by: 100, where: { id: 1 }, transaction: t });
  await Account.increment('balance', { by: 100, where: { id: 2 }, transaction: t });
  await t.commit();
} catch (error) {
  await t.rollback();
}
```

### ✅ Laravel (PHP)
```php
DB::transaction(function () {
    DB::table('accounts')->decrement('balance', 100);
    DB::table('accounts')->increment('balance', 100);
});
```

---

## 🧪 Transaction Isolation Levels
Mỗi hệ quản trị DB hỗ trợ mức độ cô lập khác nhau để tránh lỗi như dirty read, non-repeatable read:

| Mức độ Isolation        | Tránh được lỗi |
|-------------------------|----------------|
| **Read Uncommitted**    | ❌ Dirty Read  |
| **Read Committed**      | ✅ Dirty Read  |
| **Repeatable Read**     | ✅ Non-repeatable Read |
| **Serializable**        | ✅ Phantom Read (mạnh nhất) |

---

## ❌ Cảnh báo khi dùng Transaction
- Nếu transaction quá dài sẽ **khóa bảng**, gây chậm hệ thống.
- Cần rollback khi có exception – không rollback có thể gây sai lệch dữ liệu.
- Không nên kết hợp transaction với external API nếu không kiểm soát được lỗi.

---

## 🧠 Tổng kết
- Transaction là thành phần **thiết yếu** để đảm bảo an toàn dữ liệu.
- Hầu hết các framework backend hiện đại như **Spring, Django, Laravel, Sequelize...** đều hỗ trợ Transaction dễ dàng.

🚀 **Sử dụng transaction đúng cách sẽ giúp hệ thống của bạn ổn định, tin cậy và dễ mở rộng!**
