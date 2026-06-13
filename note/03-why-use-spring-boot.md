[← Previous: 2. Spring Framework vs Spring Boot](02-spring-framework-vs-spring-boot.md) | [Main Index](../main.md) | [Next: 4. Core Spring Concepts →](04-core-spring-concepts.md)

---

# 3. Why Use Spring Boot?

## 3.1 Auto-configuration

Spring Boot automatically configures application components according to:

- Dependencies on the classpath
- Existing beans
- Configuration properties
- Application type
- Available infrastructure

For example, when Spring Data JPA and a supported database driver are present, Spring Boot can configure:

- A `DataSource`
- An `EntityManagerFactory`
- Hibernate
- Transaction management
- Repository support

## 3.2 Starter dependencies

Starters group related dependencies.

Examples:

| Starter | Purpose |
|---|---|
| `spring-boot-starter-webmvc` | Servlet-based web and REST applications |
| `spring-boot-starter-webflux` | Reactive web applications |
| `spring-boot-starter-data-jpa` | JPA and Hibernate |
| `spring-boot-starter-security` | Spring Security |
| `spring-boot-starter-validation` | Jakarta Bean Validation |
| `spring-boot-starter-actuator` | Monitoring and management |
| `spring-boot-starter-test` | Testing libraries |
| `spring-boot-starter-thymeleaf` | Server-side HTML templates |

> Older Spring Boot tutorials commonly use `spring-boot-starter-web`. In Spring Boot 4, the more specific Servlet starter is `spring-boot-starter-webmvc`.

## 3.3 Embedded servers

Spring Boot can run with an embedded web server, such as:

- Apache Tomcat
- Jetty
- Reactor Netty for WebFlux

A separate application server installation is normally unnecessary.

## 3.4 Opinionated defaults

Spring Boot chooses sensible defaults, while still allowing customization.

Examples include:

- Port `8080`
- Automatic JSON conversion
- Default logging setup
- Standard resource directories
- Automatic component scanning

## 3.5 Production-ready features

Spring Boot Actuator provides features such as:

- Health checks
- Metrics
- Environment information
- Request mappings
- Log level management
- Application information
- Prometheus integration
- Thread dumps
- Heap dumps

---

---

[← Previous: 2. Spring Framework vs Spring Boot](02-spring-framework-vs-spring-boot.md) | [Main Index](../main.md) | [Next: 4. Core Spring Concepts →](04-core-spring-concepts.md)
