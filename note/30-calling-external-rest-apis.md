[← Previous: 29. Application Events](29-application-events.md) | [Main Index](../main.md) | [Next: 31. Messaging →](31-messaging.md)

---

# 30. Calling External REST APIs

Modern Spring applications can use:

- `RestClient` for synchronous calls
- `WebClient` for reactive or non-blocking calls
- HTTP service interfaces where suitable

## 30.1 RestClient bean

```java
@Configuration
public class HttpClientConfiguration {

    @Bean
    RestClient customerRestClient(RestClient.Builder builder) {
        return builder
                .baseUrl("https://api.example.com")
                .build();
    }
}
```

## 30.2 Calling an API

```java
@Service
public class CustomerClient {

    private final RestClient restClient;

    public CustomerClient(RestClient restClient) {
        this.restClient = restClient;
    }

    public CustomerResponse findCustomer(Long id) {
        return restClient
                .get()
                .uri("/customers/{id}", id)
                .retrieve()
                .body(CustomerResponse.class);
    }
}
```

Consider:

- Connection timeouts
- Read timeouts
- Retries
- Circuit breakers
- Authentication
- Rate limits
- Error mapping
- Observability
- Idempotency

Do not retry every failed request without checking whether the operation is safe to repeat.

---

---

[← Previous: 29. Application Events](29-application-events.md) | [Main Index](../main.md) | [Next: 31. Messaging →](31-messaging.md)
