[← Previous: 17. Complete CRUD Application Example](17-complete-crud-application-example.md) | [Main Index](../main.md) | [Next: 19. Entity Relationships →](19-entity-relationships.md)

---

# 18. Spring Data JPA

Spring Data JPA simplifies database access using repository interfaces.

## 18.1 Repository hierarchy

Common interfaces:

```text
Repository
  |
  +-- CrudRepository
        |
        +-- ListCrudRepository
              |
              +-- JpaRepository
```

`JpaRepository` provides operations such as:

- `save`
- `saveAll`
- `findById`
- `findAll`
- `existsById`
- `count`
- `delete`
- `deleteById`
- Pagination and sorting

## 18.2 Derived query methods

```java
List<Product> findByName(String name);

List<Product> findByPriceGreaterThan(BigDecimal price);

List<Product> findByNameContainingIgnoreCase(String keyword);

List<Product> findByQuantityBetween(Integer minimum, Integer maximum);

boolean existsByNameIgnoreCase(String name);
```

Spring interprets the method name and generates a query.

## 18.3 JPQL query

```java
@Query("""
       select p
       from Product p
       where p.price between :minimum and :maximum
       order by p.price
       """)
List<Product> findWithinPriceRange(
        @Param("minimum") BigDecimal minimum,
        @Param("maximum") BigDecimal maximum
);
```

JPQL uses entity and field names, not database table and column names.

## 18.4 Native query

```java
@Query(
    value = "select * from products where quantity = 0",
    nativeQuery = true
)
List<Product> findOutOfStockProducts();
```

Native SQL is database-specific and should be used only where appropriate.

## 18.5 Pagination

```java
@GetMapping
public Page<ProductResponse> findAll(Pageable pageable) {
    return productService.findAll(pageable);
}
```

Service:

```java
@Transactional(readOnly = true)
public Page<ProductResponse> findAll(Pageable pageable) {
    return productRepository.findAll(pageable)
            .map(this::toResponse);
}
```

Request:

```http
GET /api/products?page=0&size=20&sort=name,asc
```

## 18.6 PostgreSQL configuration

Dependency:

```xml
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
```

Configuration:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/productdb
    username: product_user
    password: ${DB_PASSWORD}

  jpa:
    hibernate:
      ddl-auto: validate
    open-in-view: false
```

`ddl-auto: validate` is safer for production than automatically creating or changing schemas.

---

---

[← Previous: 17. Complete CRUD Application Example](17-complete-crud-application-example.md) | [Main Index](../main.md) | [Next: 19. Entity Relationships →](19-entity-relationships.md)
