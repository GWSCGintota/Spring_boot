[← Previous: 30. Calling External REST APIs](30-calling-external-rest-apis.md) | [Main Index](../main.md) | [Next: 32. File Uploads →](32-file-uploads.md)

---

# 31. Messaging

Spring Boot integrates with messaging systems such as:

- Apache Kafka
- RabbitMQ
- Apache Pulsar
- JMS brokers

## 31.1 Kafka producer example

```java
@Service
public class ProductEventProducer {

    private final KafkaTemplate<String, ProductCreatedEvent> kafkaTemplate;

    public ProductEventProducer(
            KafkaTemplate<String, ProductCreatedEvent> kafkaTemplate) {
        this.kafkaTemplate = kafkaTemplate;
    }

    public void publish(ProductCreatedEvent event) {
        kafkaTemplate.send(
                "product-created",
                event.productId().toString(),
                event
        );
    }
}
```

## 31.2 Kafka consumer example

```java
@Component
public class ProductEventConsumer {

    @KafkaListener(
        note = "product-created",
        groupId = "inventory-service"
    )
    public void consume(ProductCreatedEvent event) {
        // Process event
    }
}
```

Production messaging design should consider:

- Duplicate messages
- Ordering
- Retries
- Dead-letter note or queues
- Schema evolution
- Idempotent consumers
- Transactional outbox
- Monitoring and lag

---

---

[← Previous: 30. Calling External REST APIs](30-calling-external-rest-apis.md) | [Main Index](../main.md) | [Next: 32. File Uploads →](32-file-uploads.md)
