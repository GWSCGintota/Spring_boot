[← Previous: 24. Testing](24-testing.md) | [Main Index](../main.md) | [Next: 26. Spring Boot Actuator →](26-spring-boot-actuator.md)

---

# 25. Logging

Spring Boot uses a logging facade and provides default logging configuration.

Typical log levels:

```text
TRACE
DEBUG
INFO
WARN
ERROR
```

## 25.1 Logging in a class

```java
private static final Logger log =
        LoggerFactory.getLogger(ProductService.class);

public ProductResponse findById(Long id) {
    log.debug("Finding product with id {}", id);
    return ...
}
```

Use parameterized logging:

```java
log.info("Created product with id {}", productId);
```

Avoid:

```java
log.info("Created product with id " + productId);
```

## 25.2 Configure log levels

```properties
logging.level.root=INFO
logging.level.com.example.productapi=DEBUG
logging.level.org.hibernate.SQL=DEBUG
```

## 25.3 File logging

```properties
logging.file.name=logs/product-api.log
```

For production systems, consider structured JSON logging and centralized log collection.

Never log:

- Passwords
- Access tokens
- Private keys
- Full payment data
- Sensitive personal information

---

---

[← Previous: 24. Testing](24-testing.md) | [Main Index](../main.md) | [Next: 26. Spring Boot Actuator →](26-spring-boot-actuator.md)
