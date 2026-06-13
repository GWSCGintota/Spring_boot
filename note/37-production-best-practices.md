[← Previous: 36. Building and Running the Application](36-building-and-running-the-application.md) | [Main Index](../main.md) | [Next: 38. Common Errors and Solutions →](38-common-errors-and-solutions.md)

---

# 37. Production Best Practices

## 37.1 Application design

- Use constructor injection.
- Keep controllers thin.
- Put business logic in services.
- Use DTOs for API boundaries.
- Use repository interfaces for persistence.
- Keep packages organized.
- Prefer immutable request and response objects.
- Use clear exception types.
- Apply transactions at service boundaries.

## 37.2 Database

- Use migrations.
- Use connection pooling.
- Validate schemas in production.
- Add indexes based on query patterns.
- Monitor slow queries.
- Avoid N+1 queries.
- Use pagination for large datasets.
- Avoid exposing JPA entities directly.
- Keep transactions as short as practical.

## 37.3 Security

- Use HTTPS.
- Use strong password hashing.
- Store secrets outside source control.
- Validate all input.
- Apply least privilege.
- Restrict Actuator endpoints.
- Keep dependencies updated.
- Configure CORS intentionally.
- Do not disable CSRF without understanding the application type.
- Use established OAuth 2.0 or OpenID Connect libraries.
- Avoid custom cryptography.

## 37.4 Reliability

- Define timeouts for external calls.
- Add retry only for suitable failures.
- Use circuit breakers where appropriate.
- Make message consumers idempotent.
- Implement graceful shutdown.
- Add health and readiness checks.
- Use database constraints.
- Handle partial failures.

## 37.5 Observability

- Use structured logging.
- Add application metrics.
- Add distributed tracing where required.
- Include correlation IDs.
- Monitor error rates and latency.
- Create alerts based on service objectives.
- Avoid sensitive data in logs.

## 37.6 Configuration

- Use profiles carefully.
- Prefer environment variables or secret stores.
- Validate required configuration at startup.
- Use `@ConfigurationProperties`.
- Avoid environment-specific code branches.
- Never commit real passwords or private keys.

## 37.7 API design

- Use consistent resource naming.
- Use correct HTTP status codes.
- Version APIs when necessary.
- Define a consistent error format.
- Support pagination and filtering.
- Validate request bodies.
- Document backward-incompatible changes.
- Avoid exposing internal database structures.

---

---

[← Previous: 36. Building and Running the Application](36-building-and-running-the-application.md) | [Main Index](../main.md) | [Next: 38. Common Errors and Solutions →](38-common-errors-and-solutions.md)
