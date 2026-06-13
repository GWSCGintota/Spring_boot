[← Previous: 38. Common Errors and Solutions](38-common-errors-and-solutions.md) | [Main Index](../main.md) | [Next: 40. Quick Reference Cheat Sheet →](40-quick-reference-cheat-sheet.md)

---

# 39. Spring Boot Interview Questions

## 39.1 What is Spring Boot?

Spring Boot is a framework that simplifies creating stand-alone, production-ready Spring applications through auto-configuration, starter dependencies, embedded servers, and operational features.

## 39.2 What is auto-configuration?

Auto-configuration conditionally creates beans according to available dependencies, configuration properties, and existing application beans.

## 39.3 What is a starter?

A starter is a dependency descriptor that brings together a supported group of related dependencies.

## 39.4 What does `@SpringBootApplication` do?

It combines configuration, auto-configuration, and component scanning.

## 39.5 What is dependency injection?

Dependency injection supplies an object's required collaborators from outside that object, normally through the Spring container.

## 39.6 Why is constructor injection preferred?

It makes dependencies explicit, allows immutable fields, improves testability, and prevents partially initialized objects.

## 39.7 What is the difference between `@Controller` and `@RestController`?

`@Controller` is commonly used for MVC views. `@RestController` returns response bodies directly and combines `@Controller` with `@ResponseBody`.

## 39.8 What is Spring Data JPA?

Spring Data JPA simplifies JPA persistence by generating repository implementations and queries from interfaces and method names.

## 39.9 What is the difference between `CrudRepository` and `JpaRepository`?

`CrudRepository` provides basic CRUD operations. `JpaRepository` provides additional JPA-specific operations and list, paging, and sorting capabilities through its hierarchy.

## 39.10 What does `@Transactional` do?

It defines a transaction boundary so that database operations can be committed or rolled back together.

## 39.11 What is Spring Boot Actuator?

Actuator provides management and monitoring endpoints, metrics, health checks, environment information, and other production features.

## 39.12 What is the difference between `@Component`, `@Service`, and `@Repository`?

All register Spring-managed components. `@Service` communicates service-layer intent. `@Repository` communicates persistence-layer intent and supports exception translation. `@Component` is generic.

## 39.13 What are profiles?

Profiles allow different beans and properties to be activated for different environments.

## 39.14 How do you handle exceptions globally?

Use `@RestControllerAdvice` or `@ControllerAdvice` with `@ExceptionHandler`.

## 39.15 How do you secure a Spring Boot API?

Use Spring Security with a `SecurityFilterChain`, secure password storage, appropriate authorization rules, HTTPS, input validation, and established OAuth 2.0 or OpenID Connect components where required.

## 39.16 What is the difference between Spring MVC and WebFlux?

Spring MVC uses the Servlet model and is normally request-per-thread. WebFlux is designed for reactive, non-blocking processing. WebFlux is valuable for suitable high-concurrency I/O workloads, but it should not be chosen automatically.

## 39.17 What is the N+1 query problem?

It occurs when one query loads a collection of parent records and additional queries are executed for each parent's related data. It can be addressed using fetch joins, entity graphs, projections, or improved query design.

## 39.18 Why should entities not be returned directly from REST APIs?

Direct entity exposure can cause recursive serialization, lazy loading problems, excessive data exposure, coupling between the API and database model, and unsafe updates.

---

---

[← Previous: 38. Common Errors and Solutions](38-common-errors-and-solutions.md) | [Main Index](../main.md) | [Next: 40. Quick Reference Cheat Sheet →](40-quick-reference-cheat-sheet.md)
