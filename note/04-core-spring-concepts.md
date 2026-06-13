[← Previous: 3. Why Use Spring Boot?](03-why-use-spring-boot.md) | [Main Index](../main.md) | [Next: 5. Spring Boot Architecture →](05-spring-boot-architecture.md)

---

# 4. Core Spring Concepts

Understanding Spring Boot requires understanding several Spring concepts.

## 4.1 Inversion of Control

Inversion of Control, or IoC, means that the framework controls the creation and management of application objects.

Without IoC:

```java
OrderService service = new OrderService(new OrderRepository());
```

With Spring:

```java
@Service
public class OrderService {

    private final OrderRepository repository;

    public OrderService(OrderRepository repository) {
        this.repository = repository;
    }
}
```

Spring creates the required objects and injects them.

## 4.2 Dependency Injection

Dependency Injection is the process of supplying an object's dependencies from outside the object.

Recommended approach:

```java
@Service
public class PaymentService {

    private final PaymentRepository paymentRepository;

    public PaymentService(PaymentRepository paymentRepository) {
        this.paymentRepository = paymentRepository;
    }
}
```

Constructor injection is preferred because it:

- Makes dependencies explicit
- Supports immutability
- Simplifies unit testing
- Prevents partially initialized objects
- Avoids hidden dependencies

## 4.3 Spring Bean

A Spring bean is an object created, configured, and managed by the Spring container.

Common ways to create beans:

```java
@Component
public class EmailSender {
}
```

```java
@Configuration
public class AppConfiguration {

    @Bean
    public Clock clock() {
        return Clock.systemUTC();
    }
}
```

## 4.4 ApplicationContext

The `ApplicationContext` is the Spring container.

It is responsible for:

- Creating beans
- Resolving dependencies
- Applying configuration
- Managing bean life cycles
- Publishing application events
- Providing resources
- Applying aspects and proxies

## 4.5 Component scanning

Spring scans application packages and detects classes annotated with stereotypes such as:

- `@Component`
- `@Service`
- `@Repository`
- `@Controller`
- `@RestController`
- `@Configuration`

The package containing the main application class is normally the root package for component scanning.

## 4.6 Aspect-Oriented Programming

Aspect-Oriented Programming, or AOP, separates cross-cutting concerns from business logic.

Typical cross-cutting concerns include:

- Logging
- Security
- Transactions
- Performance measurement
- Auditing
- Retry logic

For example, `@Transactional` is commonly implemented using a Spring proxy.

---

---

[← Previous: 3. Why Use Spring Boot?](03-why-use-spring-boot.md) | [Main Index](../main.md) | [Next: 5. Spring Boot Architecture →](05-spring-boot-architecture.md)
