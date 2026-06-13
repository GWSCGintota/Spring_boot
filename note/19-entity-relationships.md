[← Previous: 18. Spring Data JPA](18-spring-data-jpa.md) | [Main Index](../main.md) | [Next: 20. Transactions →](20-transactions.md)

---

# 19. Entity Relationships

## 19.1 Many-to-one

Many products may belong to one category.

```java
@Entity
public class Product {

    @ManyToOne(fetch = FetchType.LAZY, optional = false)
    @JoinColumn(name = "category_id")
    private Category category;
}
```

## 19.2 One-to-many

```java
@Entity
public class Category {

    @OneToMany(
        mappedBy = "category",
        cascade = CascadeType.ALL,
        orphanRemoval = true
    )
    private List<Product> products = new ArrayList<>();
}
```

## 19.3 One-to-one

```java
@OneToOne(fetch = FetchType.LAZY, cascade = CascadeType.ALL)
@JoinColumn(name = "profile_id")
private CustomerProfile profile;
```

## 19.4 Many-to-many

```java
@ManyToMany
@JoinTable(
    name = "product_tags",
    joinColumns = @JoinColumn(name = "product_id"),
    inverseJoinColumns = @JoinColumn(name = "tag_id")
)
private Set<Tag> tags = new HashSet<>();
```

Many-to-many relationships often become easier to manage when the join table is represented as a separate entity.

## 19.5 Relationship best practices

- Prefer lazy loading for collections.
- Avoid returning entities directly from APIs.
- Control cascading carefully.
- Maintain both sides of bidirectional relationships.
- Avoid recursive JSON serialization.
- Use DTOs.
- Watch for the N+1 query problem.
- Use fetch joins or entity graphs when necessary.

---

---

[← Previous: 18. Spring Data JPA](18-spring-data-jpa.md) | [Main Index](../main.md) | [Next: 20. Transactions →](20-transactions.md)
