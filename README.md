# 🔐 JWT Authentication & Authorization
A production-style JWT-based authentication and authorization service built with Spring Boot 3.x and Spring Security 6.x, designed to implement stateless security, modern configuration patterns, and role-based access control.
This project served as my final project of 2025 and a deep dive into how modern Spring Security actually works, especially when adapting older tutorials to newer, opinionated APIs.

---
## Technologies
  - Java
  - Spring Boot 3.x
  - Spring Security 6.x
  - JWT (JSON Web Tokens)
  - REST APIs
  - Maven
  - PostgreSQL
  - Postman (testing & validation)
#
## Features
  - Stateless JWT-based authentication (no server-side sessions)
  - Secure login and registration flow
  - Custom JWT filter using OncePerRequestFilter
  - Role-based authorization for protected endpoints
  - Modern Spring Security configuration using Lambda DSL
  - Secure password handling with explicit encoder wiring
  - End-to-end request lifecycle validation
#
## 🧠 The Process
This project started by following tutorials written for older versions of Spring Security, which immediately exposed breaking changes in Spring Security 6.
Instead of fighting the framework, I slowed down and focused on why things had changed:
  - Why .and() chaining was removed
  - Why antMatchers() was deprecated
  - Why authentication providers require explicit configuration
    
By embracing the Lambda DSL, explicitly wiring security components, and tracing requests through the filter chain, I gained a much clearer mental model of how Spring Security enforces authentication and authorization.

This wasn’t just about “making JWT work”—it was about understanding the framework’s design philosophy.
#
## Testing & Validation (Postman)
All critical authentication and authorization flows were validated manually using Postman:
  - ✅ Unauthorized request → 403 Forbidden
  - ✅ Invalid credentials → 403 Forbidden
  - ✅ Valid login → JWT issued and decoded
  - ✅ Protected endpoint with valid token → 200 OK
  - ✅ Full request lifecycle verified

(JWT filter → SecurityContext → controller)

These tests confirmed correct enforcement of access controls at every stage.
#
## 🔑 Key Technical Takeaways
  - Lambda DSL replaces .and() chaining for clearer, safer security configuration
  - DaoAuthenticationProvider requires explicit password encoder wiring
  - API changes such as:
    - antMatchers() → requestMatchers()
    - authorizeRequests() → authorizeHttpRequests()
  - JWT-based stateless auth enables horizontal scalability
  - Security filters are central to request lifecycle control

This project significantly improved my ability to debug and reason about security configurations, not just copy them.
#
## Architecture Overview
  - Authentication
    - User login & registration endpoints
    - Credentials validated via DaoAuthenticationProvider
    - JWT issued upon successful authentication
  - Authorization
    - Role-based access control on protected routes
    - JWT validated per request via OncePerRequestFilter
  - Security Context
    - Token parsed and authenticated before controller execution
    - Stateless request handling (no session persistence)
#
## ▶️ Running the Project
1. Clone the repository
     - git clone https://github.com/cecilkbm/Spring-Security6-Jwt-Auth.git
3. Configure application properties (DB, JWT secret)
4. Build and run
     - mvn spring-boot:run
6. Test endpoints using Postman
#
## 🙌 Acknowledgements
Thanks to Amigoscode and Bouali Ali for high-quality educational content that helped clarify Spring Security 6’s architecture and intent.
#
## 📷 Preview
<img width="1265" height="799" alt="image" src="https://github.com/user-attachments/assets/aa740f65-e789-4d3e-b167-55bec54f127a" />

#

