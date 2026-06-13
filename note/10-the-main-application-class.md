[← Previous: 9. Build Configuration](09-build-configuration.md) | [Main Index](../main.md) | [Next: 11. Important Spring Boot Annotations →](11-important-spring-boot-annotations.md)

---

# 10. The Main Application Class

```java
package com.example.productapi;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ProductApiApplication {

    public static void main(String[] args) {
        SpringApplication.run(ProductApiApplication.class, args);
    }
}
```

`@SpringBootApplication` combines three main annotations:

```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```

## 10.1 `@SpringBootConfiguration`

Marks the class as the primary configuration class.

## 10.2 `@EnableAutoConfiguration`

Enables Spring Boot auto-configuration.

## 10.3 `@ComponentScan`

Scans the current package and subpackages for Spring components.

---

---

[← Previous: 9. Build Configuration](09-build-configuration.md) | [Main Index](../main.md) | [Next: 11. Important Spring Boot Annotations →](11-important-spring-boot-annotations.md)
