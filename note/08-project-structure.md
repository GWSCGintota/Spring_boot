[← Previous: 7. Creating a Spring Boot Project](07-creating-a-spring-boot-project.md) | [Main Index](../main.md) | [Next: 9. Build Configuration →](09-build-configuration.md)

---

# 8. Project Structure

A standard Maven project looks like this:

```text
product-api/
├── pom.xml
├── mvnw
├── mvnw.cmd
└── src/
    ├── main/
    │   ├── java/
    │   │   └── com/example/productapi/
    │   │       ├── ProductApiApplication.java
    │   │       ├── controller/
    │   │       ├── service/
    │   │       ├── repository/
    │   │       ├── entity/
    │   │       ├── dto/
    │   │       ├── exception/
    │   │       └── config/
    │   └── resources/
    │       ├── application.properties
    │       ├── application.yml
    │       ├── static/
    │       └── templates/
    └── test/
        └── java/
            └── com/example/productapi/
```

## 8.1 Important directories

| Directory | Purpose |
|---|---|
| `src/main/java` | Application source code |
| `src/main/resources` | Configuration and resources |
| `src/test/java` | Test source code |
| `static` | Static HTML, CSS, JavaScript, images |
| `templates` | Thymeleaf or other templates |

---

---

[← Previous: 7. Creating a Spring Boot Project](07-creating-a-spring-boot-project.md) | [Main Index](../main.md) | [Next: 9. Build Configuration →](09-build-configuration.md)
