[← Previous: 14. Profiles and Environments](14-profiles-and-environments.md) | [Main Index](../main.md) | [Next: 16. Layered Application Design →](16-layered-application-design.md)

---

# 15. Building REST APIs

REST APIs commonly use HTTP methods as follows:

| HTTP Method | Purpose |
|---|---|
| GET | Retrieve data |
| POST | Create data |
| PUT | Fully replace or update data |
| PATCH | Partially update data |
| DELETE | Delete data |

## 15.1 Basic controller

```java
@RestController
@RequestMapping("/api/greetings")
public class GreetingController {

    @GetMapping
    public String greeting() {
        return "Hello, Spring Boot!";
    }
}
```

## 15.2 Path variables

```java
@GetMapping("/{name}")
public String greetByName(@PathVariable String name) {
    return "Hello, " + name;
}
```

Request:

```http
GET /api/greetings/Ovindi
```

## 15.3 Query parameters

```java
@GetMapping("/search")
public String search(
        @RequestParam String keyword,
        @RequestParam(defaultValue = "10") int limit) {

    return "Keyword: " + keyword + ", limit: " + limit;
}
```

Request:

```http
GET /api/greetings/search?keyword=spring&limit=20
```

## 15.4 Request body

```java
public record GreetingRequest(String name) {
}
```

```java
@PostMapping
public ResponseEntity<String> createGreeting(
        @RequestBody GreetingRequest request) {

    return ResponseEntity
            .status(HttpStatus.CREATED)
            .body("Hello, " + request.name());
}
```

## 15.5 ResponseEntity

`ResponseEntity` allows control over:

- HTTP status
- Headers
- Response body

```java
return ResponseEntity.ok(product);
```

```java
return ResponseEntity.noContent().build();
```

```java
return ResponseEntity
        .status(HttpStatus.CREATED)
        .body(createdProduct);
```

## 15.6 Common status codes

| Code | Meaning |
|---:|---|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthenticated |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 422 | Unprocessable Content |
| 500 | Internal Server Error |

---

---

[← Previous: 14. Profiles and Environments](14-profiles-and-environments.md) | [Main Index](../main.md) | [Next: 16. Layered Application Design →](16-layered-application-design.md)
