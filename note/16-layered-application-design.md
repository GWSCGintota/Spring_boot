[← Previous: 15. Building REST APIs](15-building-rest-apis.md) | [Main Index](../main.md) | [Next: 17. Complete CRUD Application Example →](17-complete-crud-application-example.md)

---

# 16. Layered Application Design

A recommended package layout is:

```text
com.example.productapi
├── ProductApiApplication.java
├── config
├── controller
├── dto
├── entity
├── exception
├── mapper
├── repository
└── service
```

## 16.1 Do not place all logic in controllers

Poor design:

```java
@PostMapping
public Product create(@RequestBody Product product) {
    // Validation
    // Business calculations
    // Database operations
    // External API call
    // Logging
    // Email sending
}
```

Better design:

```java
@PostMapping
public ProductResponse create(@Valid @RequestBody ProductRequest request) {
    return productService.create(request);
}
```

## 16.2 Keep layers focused

- Controllers should handle HTTP concerns.
- Services should implement business workflows.
- Repositories should handle persistence.
- DTOs should define API contracts.
- Entities should represent persistent domain data.

---

---

[← Previous: 15. Building REST APIs](15-building-rest-apis.md) | [Main Index](../main.md) | [Next: 17. Complete CRUD Application Example →](17-complete-crud-application-example.md)
