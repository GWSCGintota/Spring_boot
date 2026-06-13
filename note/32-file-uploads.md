[← Previous: 31. Messaging](31-messaging.md) | [Main Index](../main.md) | [Next: 33. API Documentation →](33-api-documentation.md)

---

# 32. File Uploads

Controller example:

```java
@RestController
@RequestMapping("/api/files")
public class FileController {

    @PostMapping(consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
    public ResponseEntity<String> upload(
            @RequestPart("file") MultipartFile file)
            throws IOException {

        if (file.isEmpty()) {
            return ResponseEntity.badRequest()
                    .body("File is empty");
        }

        String originalName = file.getOriginalFilename();

        return ResponseEntity.ok(
                "Uploaded: " + originalName
        );
    }
}
```

Configure limits:

```properties
spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB
```

Security considerations:

- Validate file type
- Validate file size
- Generate safe storage names
- Prevent path traversal
- Scan untrusted files
- Store outside the application source tree
- Restrict public access
- Do not trust the original filename

---

---

[← Previous: 31. Messaging](31-messaging.md) | [Main Index](../main.md) | [Next: 33. API Documentation →](33-api-documentation.md)
