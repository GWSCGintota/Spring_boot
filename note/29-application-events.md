[← Previous: 28. Scheduling and Asynchronous Processing](28-scheduling-and-asynchronous-processing.md) | [Main Index](../main.md) | [Next: 30. Calling External REST APIs →](30-calling-external-rest-apis.md)

---

# 29. Application Events

Events reduce direct coupling between components.

## 29.1 Define an event

```java
public record ProductCreatedEvent(
        Long productId,
        String productName
) {
}
```

## 29.2 Publish an event

```java
@Service
public class ProductService {

    private final ApplicationEventPublisher eventPublisher;

    public ProductService(
            ProductRepository repository,
            ApplicationEventPublisher eventPublisher) {
        this.eventPublisher = eventPublisher;
    }

    public ProductResponse create(ProductRequest request) {
        // Save product

        eventPublisher.publishEvent(
                new ProductCreatedEvent(id, name)
        );

        return response;
    }
}
```

## 29.3 Listen for an event

```java
@Component
public class ProductEventListener {

    @EventListener
    public void handle(ProductCreatedEvent event) {
        System.out.println(
                "Product created: " + event.productName()
        );
    }
}
```

For reliable integration across services, use a message broker and an outbox pattern rather than depending only on in-memory application events.

---

---

[← Previous: 28. Scheduling and Asynchronous Processing](28-scheduling-and-asynchronous-processing.md) | [Main Index](../main.md) | [Next: 30. Calling External REST APIs →](30-calling-external-rest-apis.md)
