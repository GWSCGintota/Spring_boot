[← Previous: 23. Spring Security](23-spring-security.md) | [Main Index](../main.md) | [Next: 25. Logging →](25-logging.md)

---

# 24. Testing

Spring Boot supports:

- Unit tests
- Slice tests
- Integration tests
- Web tests
- Repository tests
- Security tests
- Testcontainers

## 24.1 Unit test with Mockito

```java
@ExtendWith(MockitoExtension.class)
class ProductServiceTest {

    @Mock
    private ProductRepository productRepository;

    @InjectMocks
    private ProductService productService;

    @Test
    void shouldReturnProductById() {
        Product product = new Product(
                "Keyboard",
                new BigDecimal("99.99"),
                5
        );

        when(productRepository.findById(1L))
                .thenReturn(Optional.of(product));

        ProductResponse response = productService.findById(1L);

        assertThat(response.name()).isEqualTo("Keyboard");
    }
}
```

A pure unit test does not start the Spring context.

## 24.2 Application context test

```java
@SpringBootTest
class ProductApiApplicationTests {

    @Test
    void contextLoads() {
    }
}
```

## 24.3 Controller slice test

```java
@WebMvcTest(ProductController.class)
class ProductControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockitoBean
    private ProductService productService;

    @Test
    void shouldReturnProduct() throws Exception {
        ProductResponse response = new ProductResponse(
                1L,
                "Monitor",
                new BigDecimal("299.99"),
                3
        );

        when(productService.findById(1L))
                .thenReturn(response);

        mockMvc.perform(get("/api/products/1"))
                .andExpect(status().isOk())
                .andExpect(jsonPath("$.name").value("Monitor"));
    }
}
```

Depending on the Spring Boot minor version and test setup, projects may use the current Spring test bean override annotation supported by that version.

## 24.4 Repository slice test

```java
@DataJpaTest
class ProductRepositoryTest {

    @Autowired
    private ProductRepository productRepository;

    @Test
    void shouldFindByNameIgnoringCase() {
        productRepository.save(
                new Product(
                        "Mouse",
                        new BigDecimal("29.99"),
                        20
                )
        );

        boolean exists =
                productRepository.existsByNameIgnoreCase("mouse");

        assertThat(exists).isTrue();
    }
}
```

## 24.5 Full integration test

```java
@SpringBootTest(webEnvironment =
        SpringBootTest.WebEnvironment.RANDOM_PORT)
class ProductApiIntegrationTest {

    @Autowired
    private TestRestTemplate restTemplate;

    @Test
    void shouldCreateProduct() {
        ProductRequest request = new ProductRequest(
                "Desk",
                new BigDecimal("249.99"),
                2
        );

        ResponseEntity<ProductResponse> response =
                restTemplate.postForEntity(
                        "/api/products",
                        request,
                        ProductResponse.class
                );

        assertThat(response.getStatusCode())
                .isEqualTo(HttpStatus.CREATED);
    }
}
```

## 24.6 Testcontainers

Testcontainers starts real services in containers during tests.

Example uses:

- PostgreSQL
- MySQL
- MongoDB
- Kafka
- Redis
- RabbitMQ

Benefits:

- More realistic integration tests
- Fewer differences from production
- Reproducible environments
- No permanently installed local test database

---

---

[← Previous: 23. Spring Security](23-spring-security.md) | [Main Index](../main.md) | [Next: 25. Logging →](25-logging.md)
