[← Previous: 11. Important Spring Boot Annotations](11-important-spring-boot-annotations.md) | [Main Index](../main.md) | [Next: 13. Configuration and Properties →](13-configuration-and-properties.md)

---

# 12. Dependency Injection

## 12.1 Constructor injection

```java
@Service
public class CustomerService {

    private final CustomerRepository customerRepository;

    public CustomerService(CustomerRepository customerRepository) {
        this.customerRepository = customerRepository;
    }
}
```

A single constructor does not require `@Autowired`.

## 12.2 Field injection

```java
@Service
public class CustomerService {

    @Autowired
    private CustomerRepository customerRepository;
}
```

Field injection works, but is generally discouraged because it makes testing and immutability harder.

## 12.3 Setter injection

```java
@Service
public class CustomerService {

    private CustomerRepository customerRepository;

    @Autowired
    public void setCustomerRepository(CustomerRepository customerRepository) {
        this.customerRepository = customerRepository;
    }
}
```

Setter injection may be useful for optional dependencies, but constructor injection is normally preferable.

## 12.4 Multiple implementations

```java
public interface NotificationSender {
    void send(String message);
}
```

```java
@Component("emailSender")
public class EmailNotificationSender implements NotificationSender {

    @Override
    public void send(String message) {
        System.out.println("Email: " + message);
    }
}
```

```java
@Component("smsSender")
public class SmsNotificationSender implements NotificationSender {

    @Override
    public void send(String message) {
        System.out.println("SMS: " + message);
    }
}
```

Select one implementation:

```java
@Service
public class AlertService {

    private final NotificationSender notificationSender;

    public AlertService(
            @Qualifier("emailSender") NotificationSender notificationSender) {
        this.notificationSender = notificationSender;
    }
}
```

---

---

[← Previous: 11. Important Spring Boot Annotations](11-important-spring-boot-annotations.md) | [Main Index](../main.md) | [Next: 13. Configuration and Properties →](13-configuration-and-properties.md)
