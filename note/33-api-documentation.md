[← Previous: 32. File Uploads](32-file-uploads.md) | [Main Index](../main.md) | [Next: 34. Database Migration →](34-database-migration.md)

---

# 33. API Documentation

OpenAPI documentation can be generated using a compatible third-party Spring integration.

Typical outputs include:

- OpenAPI JSON
- OpenAPI YAML
- Swagger UI
- Schema definitions
- Endpoint descriptions

Example annotations may include:

```java
@Operation(summary = "Find a product by ID")
@ApiResponses({
    @ApiResponse(responseCode = "200", description = "Product found"),
    @ApiResponse(responseCode = "404", description = "Product not found")
})
@GetMapping("/{id}")
public ProductResponse findById(@PathVariable Long id) {
    return productService.findById(id);
}
```

Use a library version that explicitly supports your Spring Boot release.

API documentation should describe:

- Authentication
- Request fields
- Response fields
- Status codes
- Validation rules
- Pagination
- Error format
- Example requests and responses

---

---

[← Previous: 32. File Uploads](32-file-uploads.md) | [Main Index](../main.md) | [Next: 34. Database Migration →](34-database-migration.md)
