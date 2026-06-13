[← Previous: 35. Docker and Container Deployment](35-docker-and-container-deployment.md) | [Main Index](../main.md) | [Next: 37. Production Best Practices →](37-production-best-practices.md)

---

# 36. Building and Running the Application

## 36.1 Maven

Run:

```bash
./mvnw spring-boot:run
```

Test:

```bash
./mvnw test
```

Package:

```bash
./mvnw clean package
```

Start packaged JAR:

```bash
java -jar target/product-api-0.0.1-SNAPSHOT.jar
```

## 36.2 Gradle

Run:

```bash
./gradlew bootRun
```

Test:

```bash
./gradlew test
```

Package:

```bash
./gradlew clean build
```

Start:

```bash
java -jar build/libs/product-api-0.0.1-SNAPSHOT.jar
```

## 36.3 Command-line properties

```bash
java -jar app.jar \
  --server.port=9090 \
  --spring.profiles.active=prod
```

## 36.4 JVM options

```bash
java -Xms256m -Xmx1g -jar app.jar
```

Container memory settings should be based on measured workload and platform limits.

---

---

[← Previous: 35. Docker and Container Deployment](35-docker-and-container-deployment.md) | [Main Index](../main.md) | [Next: 37. Production Best Practices →](37-production-best-practices.md)
