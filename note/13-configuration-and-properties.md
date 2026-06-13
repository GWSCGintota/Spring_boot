[← Previous: 12. Dependency Injection](12-dependency-injection.md) | [Main Index](../main.md) | [Next: 14. Profiles and Environments →](14-profiles-and-environments.md)

---

# 13. Configuration and Properties

Spring Boot supports externalized configuration.

Common sources include:

- `application.properties`
- `application.yml`
- Environment variables
- Command-line arguments
- System properties
- Configuration files outside the JAR
- Secret management systems

## 13.1 `application.properties`

```properties
spring.application.name=product-api
server.port=8081

app.title=Product Management API
app.page-size=20
```

## 13.2 `application.yml`

```yaml
spring:
  application:
    name: product-api

server:
  port: 8081

app:
  title: Product Management API
  page-size: 20
```

Do not normally use both formats for the same configuration unless there is a clear reason.

## 13.3 Reading a single property

```java
@Component
public class AppInfo {

    private final String title;

    public AppInfo(@Value("${app.title}") String title) {
        this.title = title;
    }

    public String getTitle() {
        return title;
    }
}
```

## 13.4 Type-safe configuration properties

```java
package com.example.productapi.config;

import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties(prefix = "app")
public record AppProperties(
        String title,
        int pageSize
) {
}
```

Enable scanning:

```java
@SpringBootApplication
@ConfigurationPropertiesScan
public class ProductApiApplication {
}
```

Type-safe configuration is preferable for groups of related properties.

## 13.5 Environment variables

Spring Boot maps environment variables to properties.

Example:

```bash
export SERVER_PORT=9090
export SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/productdb
```

On Windows PowerShell:

```powershell
$env:SERVER_PORT="9090"
```

## 13.6 Configuration precedence

Higher-priority configuration sources override lower-priority sources.

A common practical order is:

1. Command-line arguments
2. Environment variables
3. External configuration files
4. Packaged application configuration
5. Default values

Do not hard-code passwords, tokens, or API keys in source control.

---

---

[← Previous: 12. Dependency Injection](12-dependency-injection.md) | [Main Index](../main.md) | [Next: 14. Profiles and Environments →](14-profiles-and-environments.md)
