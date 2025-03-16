---
layout: post
title: 🔧Cấu Hình Spring Boot Kết Nối Hai Database PostgreSQL
date: 2025-03-07 02:29 +0700
categories: [Java, Spring Boot]
tags:
  [
    Spring Boot multiple databases,
    Spring Boot connect two databases,
    Spring Boot JPA multiple databases,
  ]
image:
  path: /assets/img/spring-boot-multiple-postgresql-databases/spring-postgres.png
  width: 800
---
## 📌 1. Cấu hình `application.yml`

Thêm thông tin kết nối cho **2 database** vào `application.yml`:

```yaml
spring:
  datasource:
    primary:
      url: jdbc:postgresql://localhost:5432/db_primary
      username: user_primary
      password: pass_primary
      driver-class-name: org.postgresql.Driver
    secondary:
      url: jdbc:postgresql://localhost:5432/db_secondary
      username: user_secondary
      password: pass_secondary
      driver-class-name: org.postgresql.Driver
  jpa:
    properties:
      hibernate:
        dialect: org.hibernate.dialect.PostgreSQLDialect
    hibernate:
      ddl-auto: update
```

---

## 🏗 2. Cấu hình Primary Database

📌 **Tạo file `PrimaryDatabaseConfig.java`**:

```java
@Configuration
@EnableTransactionManagement
@EnableJpaRepositories(
    basePackages = "com.example.repository.primary",
    entityManagerFactoryRef = "primaryEntityManagerFactory",
    transactionManagerRef = "primaryTransactionManager"
)
public class PrimaryDatabaseConfig {

    @Primary
    @Bean(name = "primaryDataSource")
    @ConfigurationProperties(prefix = "spring.datasource.primary")
    public DataSource dataSource() {
        return DataSourceBuilder.create().build();
    }

    @Primary
    @Bean(name = "primaryEntityManagerFactory")
    public LocalContainerEntityManagerFactoryBean entityManagerFactory(
            EntityManagerFactoryBuilder builder, @Qualifier("primaryDataSource") DataSource dataSource) {
        return builder
                .dataSource(dataSource)
                .packages("com.example.model.primary")
                .persistenceUnit("primary")
                .build();
    }

    @Primary
    @Bean(name = "primaryTransactionManager")
    public PlatformTransactionManager transactionManager(
            @Qualifier("primaryEntityManagerFactory") EntityManagerFactory entityManagerFactory) {
        return new JpaTransactionManager(entityManagerFactory);
    }
}
```

---

## 🏗 3. Cấu hình Secondary Database

📌 **Tạo file `SecondaryDatabaseConfig.java`**:

```java
@Configuration
@EnableTransactionManagement
@EnableJpaRepositories(
    basePackages = "com.example.repository.secondary",
    entityManagerFactoryRef = "secondaryEntityManagerFactory",
    transactionManagerRef = "secondaryTransactionManager"
)
public class SecondaryDatabaseConfig {

    @Bean(name = "secondaryDataSource")
    @ConfigurationProperties(prefix = "spring.datasource.secondary")
    public DataSource dataSource() {
        return DataSourceBuilder.create().build();
    }

    @Bean(name = "secondaryEntityManagerFactory")
    public LocalContainerEntityManagerFactoryBean entityManagerFactory(
            EntityManagerFactoryBuilder builder, @Qualifier("secondaryDataSource") DataSource dataSource) {
        return builder
                .dataSource(dataSource)
                .packages("com.example.model.secondary")
                .persistenceUnit("secondary")
                .build();
    }

    @Bean(name = "secondaryTransactionManager")
    public PlatformTransactionManager transactionManager(
            @Qualifier("secondaryEntityManagerFactory") EntityManagerFactory entityManagerFactory) {
        return new JpaTransactionManager(entityManagerFactory);
    }
}
```

---

## 📂 4. Tạo Entity & Repository cho từng database

### 🏛 **Primary Database**

#### **Entity:**
```java
@Entity
@Table(name = "users")
public class PrimaryUser {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
}
```

#### **Repository:**
```java
@Repository
public interface PrimaryUserRepository extends JpaRepository<PrimaryUser, Long> {
}
```

### 🏛 **Secondary Database**

#### **Entity:**
```java
@Entity
@Table(name = "customers")
public class SecondaryUser {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String email;
}
```

#### **Repository:**
```java
@Repository
public interface SecondaryUserRepository extends JpaRepository<SecondaryUser, Long> {
}
```

---

## ⚙️ 5. Sử dụng Service để thao tác với 2 database

```java
@Service
public class UserService {
    private final PrimaryUserRepository primaryUserRepository;
    private final SecondaryUserRepository secondaryUserRepository;

    @Autowired
    public UserService(PrimaryUserRepository primaryUserRepository, SecondaryUserRepository secondaryUserRepository) {
        this.primaryUserRepository = primaryUserRepository;
        this.secondaryUserRepository = secondaryUserRepository;
    }

    @Transactional("primaryTransactionManager")
    public void saveToPrimaryDB(PrimaryUser user) {
        primaryUserRepository.save(user);
    }

    @Transactional("secondaryTransactionManager")
    public void saveToSecondaryDB(SecondaryUser user) {
        secondaryUserRepository.save(user);
    }
}
```

---

## 📌 6. Kết luận

| ✅ **Bước** | 🎯 **Hành động** |
|------------|-----------------|
| **1** | Cấu hình **2 DataSource** trong `application.yml` |
| **2** | Tạo `PrimaryDatabaseConfig` để cấu hình database chính |
| **3** | Tạo `SecondaryDatabaseConfig` để cấu hình database phụ |
| **4** | Tạo **Entity & Repository** riêng cho mỗi database |
| **5** | Sử dụng `@Transactional` để thao tác đúng database |

🚀 **Sau khi hoàn thành, Spring Boot sẽ kết nối & thao tác được với cả 2 database PostgreSQL!**