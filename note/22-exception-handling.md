[← Previous: 21. Validation](21-validation.md) | [Main Index](../main.md) | [Next: 23. Spring Security →](23-spring-security.md)

---

# 22. Exception Handling

Avoid handling every exception directly inside each controller method.

Use:

- Domain-specific exceptions
- `@RestControllerAdvice`
- `@ExceptionHandler`
- Standardized error responses
- `ProblemDetail`

Example exception:

```java
public class DuplicateEmailException extends RuntimeException {

    public DuplicateEmailException(String email) {
        super("Email is already registered: " + email);
    }
}
```

Handler:

```java
@ExceptionHandler(DuplicateEmailException.class)
public ProblemDetail handleDuplicateEmail(
        DuplicateEmailException exception) {

    return ProblemDetail.forStatusAndDetail(
            HttpStatus.CONFLICT,
            exception.getMessage()
    );
}
```

Do not expose:

- Stack traces
- SQL queries
- Passwords
- Internal tokens
- Sensitive infrastructure details

---

---

[← Previous: 21. Validation](21-validation.md) | [Main Index](../main.md) | [Next: 23. Spring Security →](23-spring-security.md)
