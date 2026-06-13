# Comprehensive Guide to Spring Boot

> **Current baseline:** Spring Boot 4.1.x, Spring Framework 7.x, and Java 17 or later.  
> **Recommended for new projects:** Java 21 LTS or a newer supported Java release.  
> **Last updated:** June 2026

This modular version stores every major topic in a separate Markdown file.

---

## Table of Contents

1. [Introduction](note/01-introduction.md)
2. [Spring Framework vs Spring Boot](note/02-spring-framework-vs-spring-boot.md)
3. [Why Use Spring Boot?](note/03-why-use-spring-boot.md)
4. [Core Spring Concepts](note/04-core-spring-concepts.md)
5. [Spring Boot Architecture](note/05-spring-boot-architecture.md)
6. [System Requirements and Tools](note/06-system-requirements-and-tools.md)
7. [Creating a Spring Boot Project](note/07-creating-a-spring-boot-project.md)
8. [Project Structure](note/08-project-structure.md)
9. [Build Configuration](note/09-build-configuration.md)
10. [The Main Application Class](note/10-the-main-application-class.md)
11. [Important Spring Boot Annotations](note/11-important-spring-boot-annotations.md)
12. [Dependency Injection](note/12-dependency-injection.md)
13. [Configuration and Properties](note/13-configuration-and-properties.md)
14. [Profiles and Environments](note/14-profiles-and-environments.md)
15. [Building REST APIs](note/15-building-rest-apis.md)
16. [Layered Application Design](note/16-layered-application-design.md)
17. [Complete CRUD Application Example](note/17-complete-crud-application-example.md)
18. [Spring Data JPA](note/18-spring-data-jpa.md)
19. [Entity Relationships](note/19-entity-relationships.md)
20. [Transactions](note/20-transactions.md)
21. [Validation](note/21-validation.md)
22. [Exception Handling](note/22-exception-handling.md)
23. [Spring Security](note/23-spring-security.md)
24. [Testing](note/24-testing.md)
25. [Logging](note/25-logging.md)
26. [Spring Boot Actuator](note/26-spring-boot-actuator.md)
27. [Caching](note/27-caching.md)
28. [Scheduling and Asynchronous Processing](note/28-scheduling-and-asynchronous-processing.md)
29. [Application Events](note/29-application-events.md)
30. [Calling External REST APIs](note/30-calling-external-rest-apis.md)
31. [Messaging](note/31-messaging.md)
32. [File Uploads](note/32-file-uploads.md)
33. [API Documentation](note/33-api-documentation.md)
34. [Database Migration](note/34-database-migration.md)
35. [Docker and Container Deployment](note/35-docker-and-container-deployment.md)
36. [Building and Running the Application](note/36-building-and-running-the-application.md)
37. [Production Best Practices](note/37-production-best-practices.md)
38. [Common Errors and Solutions](note/38-common-errors-and-solutions.md)
39. [Spring Boot Interview Questions](note/39-spring-boot-interview-questions.md)
40. [Quick Reference Cheat Sheet](note/40-quick-reference-cheat-sheet.md)
41. [Official References](note/41-official-references.md)

---

## Final Summary

Spring Boot accelerates Java backend development by combining Spring Framework features with:

- Auto-configuration
- Starter dependencies
- Embedded servers
- Externalized configuration
- Database integration
- Security support
- Testing support
- Monitoring and management
- Executable packaging
- Container and cloud support

A strong Spring Boot application normally uses:

```text
Controller -> Service -> Repository -> Database
```

along with DTOs, validation, centralized exception handling, secure configuration, automated testing, database migrations, and production observability.
``