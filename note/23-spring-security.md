[← Previous: 22. Exception Handling](22-exception-handling.md) | [Main Index](../main.md) | [Next: 24. Testing →](24-testing.md)

---

# 23. Spring Security

Spring Security provides:

- Authentication
- Authorization
- Password encoding
- CSRF protection
- Session management
- OAuth 2.0
- OpenID Connect
- Resource server support
- Method security
- Security headers

Add the dependency:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

## 23.1 Basic security configuration

```java
package com.example.productapi.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.Customizer;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
public class SecurityConfiguration {

    @Bean
    SecurityFilterChain securityFilterChain(
            HttpSecurity http) throws Exception {

        return http
                .csrf(csrf -> csrf.disable())
                .authorizeHttpRequests(auth -> auth
                        .requestMatchers(
                                "/actuator/health",
                                "/api/public/**"
                        ).permitAll()
                        .anyRequest().authenticated()
                )
                .httpBasic(Customizer.withDefaults())
                .build();
    }
}
```

Disabling CSRF may be reasonable for a stateless token-based API, but should not be done automatically for browser session applications.

## 23.2 Password encoder

```java
@Bean
PasswordEncoder passwordEncoder() {
    return new BCryptPasswordEncoder();
}
```

Never store plain-text passwords.

## 23.3 In-memory users

```java
@Bean
UserDetailsService userDetailsService(
        PasswordEncoder passwordEncoder) {

    UserDetails user = User
            .withUsername("admin")
            .password(passwordEncoder.encode("change-me"))
            .roles("ADMIN")
            .build();

    return new InMemoryUserDetailsManager(user);
}
```

Suitable for demonstrations, not normal production user management.

## 23.4 Method security

Enable:

```java
@Configuration
@EnableMethodSecurity
public class MethodSecurityConfiguration {
}
```

Use:

```java
@PreAuthorize("hasRole('ADMIN')")
public void deleteUser(Long id) {
}
```

## 23.5 JWT resource server

A production API may validate JWT access tokens using OAuth 2.0 resource server support.

Typical configuration:

```java
http
    .authorizeHttpRequests(auth -> auth
        .requestMatchers("/actuator/health").permitAll()
        .anyRequest().authenticated()
    )
    .oauth2ResourceServer(oauth2 -> oauth2.jwt(Customizer.withDefaults()));
```

Configuration:

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://identity.example.com/realms/application
```

Do not manually implement JWT parsing when standard resource server support is available.

---

---

[← Previous: 22. Exception Handling](22-exception-handling.md) | [Main Index](../main.md) | [Next: 24. Testing →](24-testing.md)
