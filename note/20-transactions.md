[← Previous: 19. Entity Relationships](19-entity-relationships.md) | [Main Index](../main.md) | [Next: 21. Validation →](21-validation.md)

---

# 20. Transactions

Transactions ensure that a group of database operations succeeds or fails as one unit.

```java
@Service
@Transactional
public class OrderService {

    public void placeOrder(OrderRequest request) {
        // Save order
        // Reduce inventory
        // Store payment information
    }
}
```

## 20.1 Read-only transaction

```java
@Transactional(readOnly = true)
public ProductResponse findById(Long id) {
    return ...
}
```

## 20.2 Rollback behaviour

By default, Spring transactions generally roll back for unchecked exceptions.

```java
@Transactional
public void process() {
    repository.save(entity);
    throw new IllegalStateException("Processing failed");
}
```

## 20.3 Common proxy limitation

This may not activate a separate transactional proxy call:

```java
public void outerMethod() {
    innerTransactionalMethod();
}

@Transactional
public void innerTransactionalMethod() {
}
```

Self-invocation within the same object bypasses the proxy. Place the transactional operation in another Spring bean or redesign the transaction boundary.

---

---

[← Previous: 19. Entity Relationships](19-entity-relationships.md) | [Main Index](../main.md) | [Next: 21. Validation →](21-validation.md)
