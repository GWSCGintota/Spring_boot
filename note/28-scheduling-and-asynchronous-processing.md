[← Previous: 27. Caching](27-caching.md) | [Main Index](../main.md) | [Next: 29. Application Events →](29-application-events.md)

---

# 28. Scheduling and Asynchronous Processing

## 28.1 Scheduling

Enable scheduling:

```java
@EnableScheduling
@SpringBootApplication
public class ProductApiApplication {
}
```

Scheduled task:

```java
@Component
public class InventoryReportJob {

    @Scheduled(cron = "0 0 2 * * *")
    public void generateReport() {
        // Runs daily at 2:00 AM
    }
}
```

Fixed rate:

```java
@Scheduled(fixedRate = 60_000)
public void runEveryMinute() {
}
```

Fixed delay:

```java
@Scheduled(fixedDelay = 60_000)
public void runAfterPreviousCompletion() {
}
```

For multi-instance deployments, use distributed locking or a dedicated scheduler.

## 28.2 Asynchronous methods

Enable:

```java
@EnableAsync
@SpringBootApplication
public class ProductApiApplication {
}
```

Async service:

```java
@Service
public class EmailService {

    @Async
    public CompletableFuture<Void> sendEmail(String address) {
        // Send email
        return CompletableFuture.completedFuture(null);
    }
}
```

Similar to transactions, self-invocation can bypass the async proxy.

---

---

[← Previous: 27. Caching](27-caching.md) | [Main Index](../main.md) | [Next: 29. Application Events →](29-application-events.md)
