[← Previous: 34. Database Migration](34-database-migration.md) | [Main Index](../main.md) | [Next: 36. Building and Running the Application →](36-building-and-running-the-application.md)

---

# 35. Docker and Container Deployment

## 35.1 Multi-stage Dockerfile

```dockerfile
FROM eclipse-temurin:21-jdk AS build

WORKDIR /workspace
COPY . .

RUN ./mvnw clean package -DskipTests

FROM eclipse-temurin:21-jre

WORKDIR /app
COPY --from=build \
    /workspace/target/*.jar \
    application.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "application.jar"]
```

Build:

```bash
docker build -t product-api:1.0 .
```

Run:

```bash
docker run --rm -p 8080:8080 product-api:1.0
```

## 35.2 Buildpacks

Spring Boot can build an OCI image without a manually written Dockerfile.

Maven:

```bash
./mvnw spring-boot:build-image \
  -Dspring-boot.build-image.imageName=product-api:1.0
```

Gradle:

```bash
./gradlew bootBuildImage \
  --imageName=product-api:1.0
```

## 35.3 Docker Compose example

```yaml
services:
  database:
    image: postgres:17
    environment:
      POSTGRES_DB: productdb
      POSTGRES_USER: product_user
      POSTGRES_PASSWORD: change-me
    ports:
      - "5432:5432"
    volumes:
      - postgres-data:/var/lib/postgresql/data

  application:
    build: .
    depends_on:
      - database
    environment:
      SPRING_DATASOURCE_URL: jdbc:postgresql://database:5432/productdb
      SPRING_DATASOURCE_USERNAME: product_user
      SPRING_DATASOURCE_PASSWORD: change-me
    ports:
      - "8080:8080"

volumes:
  postgres-data:
```

Use a secret management solution instead of storing real production passwords in Compose files.

---

---

[← Previous: 34. Database Migration](34-database-migration.md) | [Main Index](../main.md) | [Next: 36. Building and Running the Application →](36-building-and-running-the-application.md)
