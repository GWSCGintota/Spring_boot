[← Previous: 37. Production Best Practices](37-production-best-practices.md) | [Main Index](../main.md) | [Next: 39. Spring Boot Interview Questions →](39-spring-boot-interview-questions.md)

---

# 38. Common Errors and Solutions

## 38.1 Port already in use

Error:

```text
Web server failed to start. Port 8080 was already in use.
```

Solution:

```properties
server.port=8081
```

Or stop the process using port 8080.

## 38.2 Bean not found

Error:

```text
No qualifying bean of type ... available
```

Check:

- Is the class annotated with `@Component`, `@Service`, or another stereotype?
- Is it under the component-scan root package?
- Is an implementation available?
- Are profile conditions preventing creation?
- Is a required starter missing?

## 38.3 Multiple beans found

Error:

```text
NoUniqueBeanDefinitionException
```

Use:

- `@Qualifier`
- `@Primary`
- A more specific dependency type

## 38.4 Database connection failure

Check:

- JDBC URL
- Database host
- Port
- Username
- Password
- Driver dependency
- Database availability
- Network rules
- SSL configuration

## 38.5 Table not found

Possible causes:

- Migration did not run
- Wrong schema
- Wrong database
- Entity scanning issue
- Incorrect table name
- `ddl-auto` setting

## 38.6 LazyInitializationException

Common causes:

- Accessing a lazy relationship outside a transaction
- Serializing entities directly
- Incorrect fetch design

Better solutions:

- Map entities to DTOs inside the transaction
- Fetch required data explicitly
- Use fetch joins or entity graphs
- Avoid changing everything to eager loading

## 38.7 Circular dependency

Example:

```text
ServiceA -> ServiceB -> ServiceA
```

Redesign responsibilities rather than depending on circular references.

## 38.8 Unsupported media type

Error:

```text
415 Unsupported Media Type
```

Make sure the request contains:

```http
Content-Type: application/json
```

## 38.9 Validation not triggered

Check:

- Validation starter is included
- `@Valid` is used
- Jakarta validation annotations are imported
- The request is being bound to the expected object

Correct imports use:

```java
jakarta.validation.*
```

not legacy `javax.validation.*`.

## 38.10 Jakarta migration errors

Spring Boot 3 and later use Jakarta namespaces.

Use:

```java
import jakarta.persistence.Entity;
import jakarta.validation.Valid;
import jakarta.servlet.http.HttpServletRequest;
```

Do not use older `javax.*` imports for these APIs.

---

---

[← Previous: 37. Production Best Practices](37-production-best-practices.md) | [Main Index](../main.md) | [Next: 39. Spring Boot Interview Questions →](39-spring-boot-interview-questions.md)
