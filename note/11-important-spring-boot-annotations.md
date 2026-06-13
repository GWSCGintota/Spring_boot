[← Previous: 10. The Main Application Class](10-the-main-application-class.md) | [Main Index](../main.md) | [Next: 12. Dependency Injection →](12-dependency-injection.md)

---

# 11. Important Spring Boot Annotations

## 11.1 Core annotations

| Annotation | Purpose |
|---|---|
| `@SpringBootApplication` | Main application configuration |
| `@Configuration` | Declares a configuration class |
| `@Bean` | Declares a bean from a method |
| `@Component` | Generic managed component |
| `@Service` | Service-layer component |
| `@Repository` | Persistence-layer component |
| `@Controller` | MVC controller |
| `@RestController` | REST controller |
| `@Autowired` | Requests dependency injection |
| `@Qualifier` | Selects a specific bean |
| `@Primary` | Marks a preferred bean |

## 11.2 Web annotations

| Annotation | Purpose |
|---|---|
| `@RequestMapping` | Defines a base request mapping |
| `@GetMapping` | Handles HTTP GET |
| `@PostMapping` | Handles HTTP POST |
| `@PutMapping` | Handles HTTP PUT |
| `@PatchMapping` | Handles HTTP PATCH |
| `@DeleteMapping` | Handles HTTP DELETE |
| `@PathVariable` | Reads a path parameter |
| `@RequestParam` | Reads a query parameter |
| `@RequestBody` | Reads a request body |
| `@ResponseStatus` | Defines a response status |
| `@ControllerAdvice` | Global controller logic |
| `@ExceptionHandler` | Handles exceptions |

## 11.3 Data annotations

| Annotation | Purpose |
|---|---|
| `@Entity` | Declares a JPA entity |
| `@Table` | Configures the table |
| `@Id` | Declares a primary key |
| `@GeneratedValue` | Configures key generation |
| `@Column` | Configures a column |
| `@OneToOne` | One-to-one relationship |
| `@OneToMany` | One-to-many relationship |
| `@ManyToOne` | Many-to-one relationship |
| `@ManyToMany` | Many-to-many relationship |
| `@Transactional` | Defines a transaction boundary |

## 11.4 Validation annotations

| Annotation | Purpose |
|---|---|
| `@Valid` | Triggers nested validation |
| `@Validated` | Enables method-level validation |
| `@NotNull` | Value must not be null |
| `@NotBlank` | Text must contain non-whitespace content |
| `@Size` | Restricts size |
| `@Min` / `@Max` | Restricts numeric values |
| `@Positive` | Value must be positive |
| `@Email` | Validates an email format |
| `@Pattern` | Validates using a regular expression |

---

---

[← Previous: 10. The Main Application Class](10-the-main-application-class.md) | [Main Index](../main.md) | [Next: 12. Dependency Injection →](12-dependency-injection.md)
