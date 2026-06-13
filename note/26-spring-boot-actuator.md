[← Previous: 25. Logging](25-logging.md) | [Main Index](../main.md) | [Next: 27. Caching →](27-caching.md)

---

# 26. Spring Boot Actuator

Add:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Common endpoints include:

| Endpoint | Purpose |
|---|---|
| `/actuator/health` | Application health |
| `/actuator/info` | Application information |
| `/actuator/metrics` | Metrics |
| `/actuator/loggers` | Logging configuration |
| `/actuator/mappings` | Request mappings |
| `/actuator/env` | Environment information |
| `/actuator/prometheus` | Prometheus metrics |

Expose selected endpoints:

```properties
management.endpoints.web.exposure.include=health,info,metrics,prometheus
management.endpoint.health.show-details=when_authorized
```

Do not expose every endpoint publicly.

## 26.1 Application information

```properties
info.app.name=Product API
info.app.version=1.0.0
info.app.description=Product management service
```

## 26.2 Custom health indicator

```java
@Component
public class PaymentGatewayHealthIndicator
        implements HealthIndicator {

    @Override
    public Health health() {
        boolean available = checkGateway();

        if (available) {
            return Health.up().build();
        }

        return Health.down()
                .withDetail("reason", "Gateway unavailable")
                .build();
    }

    private boolean checkGateway() {
        return true;
    }
}
```

---

---

[← Previous: 25. Logging](25-logging.md) | [Main Index](../main.md) | [Next: 27. Caching →](27-caching.md)
