[← Previous: 26. Spring Boot Actuator](26-spring-boot-actuator.md) | [Main Index](../main.md) | [Next: 28. Scheduling and Asynchronous Processing →](28-scheduling-and-asynchronous-processing.md)

---

# 27. Caching

Caching reduces repeated expensive operations.

Enable caching:

```java
@SpringBootApplication
@EnableCaching
public class ProductApiApplication {
}
```

Use:

```java
@Cacheable(cacheNames = "products", key = "#id")
public ProductResponse findById(Long id) {
    return ...
}
```

Update cache:

```java
@CachePut(cacheNames = "products", key = "#id")
public ProductResponse update(Long id, ProductRequest request) {
    return ...
}
```

Remove cache entry:

```java
@CacheEvict(cacheNames = "products", key = "#id")
public void delete(Long id) {
    ...
}
```

Possible cache providers:

- Simple in-memory cache
- Caffeine
- Redis
- Hazelcast

Do not cache data without considering:

- Staleness
- Eviction
- Memory use
- Distributed consistency
- Tenant separation
- Security

---

---

[← Previous: 26. Spring Boot Actuator](26-spring-boot-actuator.md) | [Main Index](../main.md) | [Next: 28. Scheduling and Asynchronous Processing →](28-scheduling-and-asynchronous-processing.md)
