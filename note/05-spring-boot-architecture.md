[← Previous: 4. Core Spring Concepts](04-core-spring-concepts.md) | [Main Index](../main.md) | [Next: 6. System Requirements and Tools →](06-system-requirements-and-tools.md)

---

# 5. Spring Boot Architecture

A common layered Spring Boot architecture is:

```text
Client
  |
  v
Controller Layer
  |
  v
Service Layer
  |
  v
Repository Layer
  |
  v
Database
```

## 5.1 Controller layer

Responsibilities:

- Receive HTTP requests
- Validate request data
- Convert request data into application objects
- Call service methods
- Return HTTP responses
- Select appropriate status codes

## 5.2 Service layer

Responsibilities:

- Implement business rules
- Coordinate repositories
- Manage transactions
- Call external services
- Apply application workflows

## 5.3 Repository layer

Responsibilities:

- Read and write data
- Execute queries
- Abstract persistence operations

## 5.4 Domain or entity layer

Responsibilities:

- Represent business data
- Define entity relationships
- Contain domain behaviour where appropriate

## 5.5 DTO layer

Data Transfer Objects are used to:

- Represent API requests
- Represent API responses
- Hide internal entity details
- Prevent unwanted field updates
- Reduce entity serialization problems
- Stabilize the public API

---

---

[← Previous: 4. Core Spring Concepts](04-core-spring-concepts.md) | [Main Index](../main.md) | [Next: 6. System Requirements and Tools →](06-system-requirements-and-tools.md)
