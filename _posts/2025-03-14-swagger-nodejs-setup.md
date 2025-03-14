---
layout: post
title: 🚀 Hướng Dẫn Cấu Hình Swagger Cho Node.js
date: 2025-03-14 23:39 +0700
categories: [Node.js]
tags:
  [
    Swagger Node.js,
    Cấu hình Swagger cho Node.js,
    Swagger UI Express,
    Tích hợp Swagger vào Node.js,
  ]
image:
  path: /assets/img/swagger-nodejs-setup/nodejs_swagger.jpg
  width: 800
---

## 📌 Giới Thiệu
[Swagger](https://swagger.io/) là một công cụ mạnh mẽ giúp tạo tài liệu API tự động cho các ứng dụng web. Bài viết này sẽ hướng dẫn bạn cách tích hợp Swagger vào một ứng dụng **Node.js** sử dụng **Express**.

## 🛠️ Bước 1: Cài Đặt Các Gói Cần Thiết
Trước tiên, hãy cài đặt các gói cần thiết bằng lệnh sau:

```sh
npm install swagger-jsdoc swagger-ui-express
```

Để hỗ trợ tự động restart server khi có thay đổi, cài đặt `nodemon`:

```sh
npm install --save-dev nodemon
```

Sau đó, chỉnh sửa file `package.json` để thêm script chạy ứng dụng:

```json
"scripts": {
  "start": "node app.js",
  "dev": "nodemon app.js"
}
```

## ⚙️ Bước 2: Cấu Hình Swagger
Tạo một thư mục `setups` và thêm file `swaggerSetup.js`:

```javascript
const swaggerJsDoc = require('swagger-jsdoc');
const swaggerUi = require('swagger-ui-express');

const swaggerOptions = {
  swaggerDefinition: {
    openapi: '3.0.0',
    info: {
      title: '📘 API Documentation',
      version: '1.0.0',
      description: '📄 Tài liệu API cho ứng dụng Node.js với Express',
    },
    servers: [
      {
        url: 'http://localhost:3000',
        description: '🌐 Local server',
      },
    ],
  },
  apis: ['./routes/*.js'], // Định nghĩa nơi Swagger tìm kiếm các comment
};

const swaggerDocs = swaggerJsDoc(swaggerOptions);

const setupSwagger = (app) => {
  app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerDocs));
};

module.exports = setupSwagger;
```

## 🔗 Bước 3: Tích Hợp Swagger vào Express
Mở file `app.js` và chỉnh sửa như sau:

```javascript
const express = require('express');
const setupSwagger = require('./setups/swaggerSetup');

const app = express();
const PORT = 3000;

// Middleware
app.use(express.json());

// Cấu hình Swagger
setupSwagger(app);

app.listen(PORT, () => {
  console.log(`🚀 Server is running on http://localhost:${PORT}`);
});
```

## ✏️ Bước 4: Viết Tài Liệu API
Mở file `routes/users.js` và thêm comment Swagger:

```javascript
const express = require('express');
const router = express.Router();

/**
 * @swagger
 * /users:
 *   get:
 *     summary: 📌 Lấy danh sách người dùng
 *     description: 🧑‍💻 API này trả về danh sách người dùng
 *     responses:
 *       200:
 *         description: ✅ Thành công
 *         content:
 *           application/json:
 *             schema:
 *               type: array
 *               items:
 *                 type: object
 *                 properties:
 *                   id:
 *                     type: integer
 *                     example: 1
 *                   name:
 *                     type: string
 *                     example: "Nguyễn Văn A"
 */
router.get('/users', (req, res) => {
  res.json([{ id: 1, name: 'Nguyễn Văn A' }]);
});

module.exports = router;
```

## ▶️ Bước 5: Chạy Ứng Dụng
Chạy ứng dụng bằng lệnh:

```sh
npm run dev
```

Sau đó, mở trình duyệt và truy cập **🔗 http://localhost:3000/api-docs** để xem tài liệu API do Swagger tạo ra.

---
### 🎯 Tổng Kết
Bạn đã hoàn thành việc tích hợp Swagger vào ứng dụng Node.js sử dụng Express. Bây giờ bạn có thể dễ dàng viết tài liệu API và chia sẻ với nhóm phát triển một cách trực quan và chuyên nghiệp! 🚀
