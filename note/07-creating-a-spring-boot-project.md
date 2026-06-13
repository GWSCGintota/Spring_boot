[← Previous: 6. System Requirements and Tools](06-system-requirements-and-tools.md) | [Main Index](../main.md) | [Next: 8. Project Structure →](08-project-structure.md)

---

# 7. Creating a Spring Boot Project

## 7.1 Using Spring Initializr

The easiest method is Spring Initializr:

```text
https://start.spring.io
```

Typical selections:

| Setting | Example |
|---|---|
| Project | Maven |
| Language | Java |
| Spring Boot | Latest stable |
| Group | `com.example` |
| Artifact | `product-api` |
| Packaging | JAR |
| Java | 21 |

Useful dependencies:

- Spring Web MVC
- Spring Data JPA
- Validation
- H2 Database
- PostgreSQL Driver
- Spring Boot Actuator
- Spring Security
- DevTools

## 7.2 Using an IDE

Most modern Java IDEs provide a Spring Initializr project wizard.

## 7.3 Using the command line

After downloading and extracting the project:

```bash
cd product-api
```

Run with Maven:

```bash
./mvnw spring-boot:run
```

Windows:

```powershell
mvnw.cmd spring-boot:run
```

Run with Gradle:

```bash
./gradlew bootRun
```

Windows:

```powershell
gradlew.bat bootRun
```

---

---

[← Previous: 6. System Requirements and Tools](06-system-requirements-and-tools.md) | [Main Index](../main.md) | [Next: 8. Project Structure →](08-project-structure.md)
