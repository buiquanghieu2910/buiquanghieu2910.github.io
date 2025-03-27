---
layout: post
title: 🚀 Elasticsearch – Công cụ tìm kiếm và phân tích dữ liệu mạnh mẽ
date: 2025-03-28 02:44 +0700
categories: [Big Data, Elasticsearch]
tags: [
    Elasticsearch là gì,
    Tìm kiếm full-text,
    Elasticsearch và Spring Boot,
    Phân tích dữ liệu lớn,
    Elastic Stack
]
image:
  path: /assets/img/elasticsearch/elasticsearch.jpg
---

## 🎯 **Giới thiệu về Elasticsearch**
**Elasticsearch** là một công cụ tìm kiếm và phân tích dữ liệu mã nguồn mở, nổi bật với khả năng tìm kiếm nhanh chóng và hiệu quả, đặc biệt là trong các hệ thống dữ liệu lớn (Big Data). Được xây dựng trên nền tảng **Apache Lucene**, Elasticsearch là một phần trong bộ công cụ **Elastic Stack** (cùng với **Logstash** và **Kibana**) và được sử dụng rộng rãi trong các ứng dụng cần tìm kiếm, phân tích và giám sát dữ liệu.

Elasticsearch cung cấp khả năng tìm kiếm full-text, tìm kiếm theo các trường cụ thể, và phân tích dữ liệu với tốc độ cao. Nó hỗ trợ lưu trữ và xử lý các loại dữ liệu phi cấu trúc và có thể mở rộng linh hoạt với các cluster phân tán.

## 🛠️ **Cách thức hoạt động của Elasticsearch**

### ✅ **Công cụ tìm kiếm phân tán**
Elasticsearch sử dụng kiến trúc **phân tán**, với các **node** và **cluster**. Một **cluster** có thể chứa nhiều **node** (máy chủ), mỗi node chịu trách nhiệm lưu trữ một phần dữ liệu và thực hiện các thao tác tìm kiếm, phân tích.

1️⃣ **Chỉ mục (Index)**: Dữ liệu trong Elasticsearch được lưu trữ trong các chỉ mục. Một chỉ mục có thể chứa nhiều tài liệu và dữ liệu được phân loại theo các trường (fields) để dễ dàng tìm kiếm.

2️⃣ **Tài liệu (Document)**: Một tài liệu trong Elasticsearch tương đương với một hàng trong cơ sở dữ liệu quan hệ. Mỗi tài liệu là một đơn vị dữ liệu có cấu trúc dưới dạng JSON.

3️⃣ **Trường (Field)**: Mỗi tài liệu có thể chứa nhiều trường, trong đó mỗi trường chứa một giá trị hoặc một mảng các giá trị.

4️⃣ **Shard và Replica**: Elasticsearch phân chia các chỉ mục thành các **shard** (mảnh nhỏ) và mỗi shard có thể có một hoặc nhiều bản sao (replica) để đảm bảo độ tin cậy và tăng hiệu suất tìm kiếm.

### ✅ **Phân tích và tìm kiếm full-text**
Elasticsearch cung cấp khả năng phân tích và tìm kiếm **full-text** (toàn văn), điều này có nghĩa là bạn có thể tìm kiếm văn bản, nội dung tài liệu hoặc các chuỗi văn bản không theo cấu trúc mà không gặp khó khăn.

- Elasticsearch sử dụng **analyzers** để phân tích văn bản đầu vào, chuyển đổi văn bản thành các **token** (đơn vị tìm kiếm), sau đó sử dụng các **inverted index** để tìm kiếm nhanh chóng.
  
- **Inverted index** là cấu trúc dữ liệu giúp Elasticsearch tìm kiếm nhanh chóng các từ hoặc cụm từ trong văn bản.

### ✅ **Tìm kiếm theo trường**
Elasticsearch không chỉ hỗ trợ tìm kiếm văn bản mà còn cho phép bạn tìm kiếm dữ liệu theo các trường cụ thể. Bạn có thể tìm kiếm theo **mảng** (array), **số** (numeric), **ngày tháng** (date), hoặc **địa lý** (geo-location).

## 🛠️ **Lợi ích của Elasticsearch**

### ✅ **Tìm kiếm nhanh chóng**
- Elasticsearch được thiết kế để cung cấp khả năng tìm kiếm nhanh chóng trong các bộ dữ liệu lớn. Điều này rất quan trọng đối với các ứng dụng yêu cầu phản hồi thời gian thực, chẳng hạn như công cụ tìm kiếm web, phân tích log, hoặc các hệ thống giám sát.

### ✅ **Khả năng mở rộng cao**
- Elasticsearch hỗ trợ khả năng mở rộng theo chiều ngang, tức là bạn có thể thêm các node vào cluster để mở rộng dung lượng lưu trữ và khả năng xử lý. Việc này rất dễ dàng và tự động, giúp Elasticsearch trở thành một giải pháp lý tưởng cho các hệ thống có khối lượng dữ liệu lớn.

### ✅ **Tìm kiếm phân tán**
- Elasticsearch phân phối dữ liệu trên các node khác nhau, giúp tăng khả năng tìm kiếm và phân tích với quy mô lớn mà không làm giảm hiệu suất. Điều này giúp duy trì hiệu suất ngay cả khi dữ liệu tăng lên rất nhanh.

### ✅ **Khả năng phân tích dữ liệu mạnh mẽ**
- Elasticsearch không chỉ giúp tìm kiếm mà còn hỗ trợ các phân tích dữ liệu mạnh mẽ, bao gồm phân tích thời gian thực, tổng hợp (aggregation), và phân tích các trường dữ liệu.

### ✅ **Tính linh hoạt và dễ dàng tích hợp**
- Elasticsearch dễ dàng tích hợp với nhiều hệ thống khác nhau, bao gồm các công cụ phân tích dữ liệu, các dịch vụ cloud, và các ứng dụng tìm kiếm. Nó cũng hỗ trợ nhiều API, bao gồm RESTful API, giúp bạn dễ dàng làm việc với dữ liệu.

## 🛠️ **Ví dụ tích hợp Elasticsearch với Spring Boot**

Để tích hợp **Elasticsearch** vào ứng dụng **Spring Boot**, bạn có thể sử dụng **Spring Data Elasticsearch**. Dưới đây là một ví dụ cơ bản về cách tích hợp Elasticsearch để tìm kiếm dữ liệu trong ứng dụng Spring Boot.

### ✅ **Bước 1: Thêm Dependencies vào `pom.xml`**
```xml
<dependencies>
    <!-- Spring Data Elasticsearch -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-elasticsearch</artifactId>
    </dependency>

    <!-- Spring Boot Web Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

### ✅ **Bước 2: Cấu hình kết nối với Elasticsearch**
Trong file `application.properties`, bạn cần cấu hình thông tin kết nối đến Elasticsearch.
```properties
spring.elasticsearch.rest.uris=http://localhost:9200
spring.data.elasticsearch.repositories.enabled=true
```

### ✅ **Bước 3: Tạo Entity và Repository**
Tạo một Document để đại diện cho một tài liệu trong Elasticsearch, và một Repository để truy vấn dữ liệu.
```java
import org.springframework.data.annotation.Id;
import org.springframework.data.elasticsearch.annotations.Document;

@Document(indexName = "products")
public class Product {
    @Id
    private String id;
    private String name;
    private double price;

    // Getters and Setters
}
```

Tạo một Repository để tương tác với Elasticsearch:
```java
import org.springframework.data.elasticsearch.repository.ElasticsearchRepository;

public interface ProductRepository extends ElasticsearchRepository<Product, String> {
    // Các phương thức tìm kiếm tùy chỉnh có thể được định nghĩa ở đây
}
```

### ✅ **Bước 4: Tạo Service để sử dụng Elasticsearch**
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class ProductService {

    @Autowired
    private ProductRepository productRepository;

    public Iterable<Product> getAllProducts() {
        return productRepository.findAll();
    }

    public Product saveProduct(Product product) {
        return productRepository.save(product);
    }

    public Iterable<Product> searchByName(String name) {
        return productRepository.findByName(name);
    }
}
```

### ✅ **Bước 5: Tạo Controller để xử lý yêu cầu**
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/products")
public class ProductController {

    @Autowired
    private ProductService productService;

    @GetMapping("/")
    public Iterable<Product> getAllProducts() {
        return productService.getAllProducts();
    }

    @PostMapping("/")
    public Product addProduct(@RequestBody Product product) {
        return productService.saveProduct(product);
    }

    @GetMapping("/search/{name}")
    public Iterable<Product> searchByName(@PathVariable String name) {
        return productService.searchByName(name);
    }
}
```

## 🚀 **Tổng kết**
Elasticsearch là một công cụ tìm kiếm và phân tích dữ liệu mạnh mẽ, giúp bạn xử lý và tìm kiếm dữ liệu nhanh chóng, hiệu quả, đặc biệt là trong các hệ thống dữ liệu lớn. Với khả năng mở rộng linh hoạt và hỗ trợ phân tán dữ liệu, Elasticsearch trở thành giải pháp lý tưởng cho các ứng dụng web, phân tích log, giám sát hệ thống và các dự án Big Data. Việc tích hợp với Spring Boot giúp bạn triển khai Elasticsearch một cách dễ dàng trong các ứng dụng Java.