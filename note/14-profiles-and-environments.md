[← Previous: 13. Configuration and Properties](13-configuration-and-properties.md) | [Main Index](../main.md) | [Next: 15. Building REST APIs →](15-building-rest-apis.md)

---

# 14. Profiles and Environments

Profiles allow different configuration for different environments.

Common profiles:

- `dev`
- `test`
- `staging`
- `prod`

Files:

```text
application.yml
application-dev.yml
application-test.yml
application-prod.yml
```

## 14.1 Activate a profile

```properties
spring.profiles.active=dev
```

Environment variable:

```bash
export SPRING_PROFILES_ACTIVE=prod
```

Command line:

```bash
java -jar app.jar --spring.profiles.active=prod
```

## 14.2 Profile-specific bean

```java
@Configuration
@Profile("dev")
public class DevelopmentConfiguration {

    @Bean
    public Clock developmentClock() {
        return Clock.systemUTC();
    }
}
```

Avoid permanently hard-coding a production profile in the packaged application.

---

---

[← Previous: 13. Configuration and Properties](13-configuration-and-properties.md) | [Main Index](../main.md) | [Next: 15. Building REST APIs →](15-building-rest-apis.md)
