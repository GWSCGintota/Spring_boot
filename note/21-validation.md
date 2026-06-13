[← Previous: 20. Transactions](20-transactions.md) | [Main Index](../main.md) | [Next: 22. Exception Handling →](22-exception-handling.md)

---

# 21. Validation

Add validation to request DTOs.

```java
public record UserRequest(

        @NotBlank
        @Size(max = 100)
        String name,

        @Email
        @NotBlank
        String email,

        @Min(18)
        int age
) {
}
```

Controller:

```java
@PostMapping
public UserResponse create(
        @Valid @RequestBody UserRequest request) {
    return userService.create(request);
}
```

## 21.1 Method parameter validation

```java
@Service
@Validated
public class DiscountService {

    public BigDecimal calculate(
            @Positive BigDecimal amount) {
        return amount.multiply(new BigDecimal("0.90"));
    }
}
```

## 21.2 Validation groups

Validation groups can apply different rules for create and update operations, but separate request DTOs are often easier to understand.

---

---

[← Previous: 20. Transactions](20-transactions.md) | [Main Index](../main.md) | [Next: 22. Exception Handling →](22-exception-handling.md)
