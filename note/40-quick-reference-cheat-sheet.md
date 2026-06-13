[← Previous: 39. Spring Boot Interview Questions](39-spring-boot-interview-questions.md) | [Main Index](../main.md) | [Next: 41. Official References →](41-official-references.md)

---

# 40. Quick Reference Cheat Sheet

## Main application

```java
@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

## REST controller

```java
@RestController
@RequestMapping("/api/items")
public class ItemController {
}
```

## Service

```java
@Service
public class ItemService {
}
```

## Repository

```java
public interface ItemRepository
        extends JpaRepository<Item, Long> {
}
```

## Entity

```java
@Entity
public class Item {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
}
```

## GET

```java
@GetMapping("/{id}")
public ItemResponse findById(@PathVariable Long id) {
    return service.findById(id);
}
```

## POST

```java
@PostMapping
@ResponseStatus(HttpStatus.CREATED)
public ItemResponse create(
        @Valid @RequestBody ItemRequest request) {
    return service.create(request);
}
```

## Configuration property

```java
@Value("${app.name}")
private String appName;
```

## Transaction

```java
@Transactional
public void process() {
}
```

## Scheduled task

```java
@Scheduled(fixedRate = 60_000)
public void run() {
}
```

## Cache

```java
@Cacheable("items")
public ItemResponse findById(Long id) {
}
```

## Test

```java
@SpringBootTest
class ApplicationTests {
}
```

## Build

```bash
./mvnw clean package
```

## Run

```bash
java -jar target/application.jar
```

---

---

[← Previous: 39. Spring Boot Interview Questions](39-spring-boot-interview-questions.md) | [Main Index](../main.md) | [Next: 41. Official References →](41-official-references.md)
