---
name: java-springboot-application-guide
description: Enterprise-grade Java Spring Boot implementation standards for production-ready backend architectures, layered application structures, REST APIs, security models, database standards, observability systems, testing strategies, and scalable application and practises.
---

## Primary Responsibility

This skill acts as the authoritative enterprise reference for generating:
- backend architecture requirement documents
- implementation plans
- scalable application structures
- production-ready backend standards
- Spring Boot implementation blueprints
- technical requirement markdown files
- developer handoff specifications

This skill MUST be used whenever:
- planning Java backend systems
- generating Spring Boot project structures
- designing REST APIs
- generating production architecture
- designing microservices
- creating implementation requirement documents
- generating backend engineering standards

# Project Structure

The implementation planner MUST generate the following enterprise structure.

```text
src/main/java/com/company/project/
├── config/       # (Mandatory) Security, embedded server, and Bean configurations
├── controller/   # (Mandatory) REST API endpoints (Web Layer)
├── service/      # (Mandatory) Business logic & transaction boundaries
├── repository/   # (Mandatory) Spring Data JPA interfaces
├── model/        # (Mandatory) JPA Entities (Database representation)
├── dto/          # (Mandatory) Data Transfer Objects (Request/Response contracts)
├── mapper/       # (Optional) Model-to-DTO conversion logic (e.g., MapStruct)
├── validation/   # (Optional) Custom @Constraint validators
├── exception/    # (Mandatory) GlobalExceptionHandler (@RestControllerAdvice)
├── util/         # (Optional) Static helper classes (use sparingly)
└── common/       # (Optional) Global Enums, Constants, or shared POJOs
```

---

# Enterprise Naming Standards

| Element | Convention | Example |
|---|---|---|
| Classes | PascalCase | `PaymentService` |
| Methods | camelCase | `calculateTotal()` |
| Variables | camelCase | `isUserActive` |
| Constants | SCREAMING_SNAKE_CASE | `MAX_RETRY_COUNT` |
| Packages | lowercase | `com.company.orderservice` |
| Endpoints | kebab-case plural | `/api/v1/user-profiles` |
| DTOs | Suffix DTO | `UserResponseDTO` |
| Requests | Suffix Request | `CreateUserRequest` |
| Responses | Suffix Response | `UserDetailsResponse` |
| Exceptions | Suffix Exception | `ResourceNotFoundException` |
| Config Classes | Suffix Config | `SecurityConfig` |

---

# Mandatory Architectural Style

## Required Layer Flow

- Controller Layer
- Service Layer
- Repository Layer
- Database

## Layer Responsibilities

### Controller Layer
Responsible only for:
- request validation
- request mapping
- response mapping
- HTTP status handling

Controllers MUST NOT:
- contain business logic
- directly access repositories
- contain transaction logic

### Service Layer
Responsible for:
- business logic
- orchestration
- transaction boundaries
- domain workflows
- external integrations

### Repository Layer
Responsible only for:
- persistence operations
- query definitions
- database interaction

Repositories MUST NOT:
- contain business workflows
- contain validation logic
- contain orchestration logic

---


# API Design Standards
Required Standards

- API versioning required
- URI format: /api/v1/...
- JSON responses only
- Stateless architecture required
- Pagination required for collections
- OpenAPI documentation required
- Standard HTTP status codes required

API Requirements

- use request validation
- return meaningful error responses
- never expose internal exceptions
- include trace identifiers
- support idempotency where applicable

---

# DTO & Mapping Standards
Mandatory Rules

- entities MUST NEVER be exposed directly
- all external communication MUST use DTOs
- mapping layers required
- prefer MapStruct for large applications
- immutable DTOs preferred
- request and response DTOs separated

---

# Security Standards
Mandatory Security Requirements

- Spring Security required
- JWT or OAuth2 authentication required
- stateless authentication only
- RBAC authorization required
- method-level security required
- HTTPS assumed mandatory
- secure password hashing required
- secrets externalization required

Required Practices

- use @PreAuthorize
- implement token expiration
- implement refresh tokens
- secure actuator endpoints
- validate all inputs
- sanitize external payloads

---

# Database & Persistence Standards
Mandatory Rules

- Flyway or Liquibase required
- migrations required
- UUID preferred for distributed systems
- indexing strategy required
- pagination mandatory
- soft deletes required for critical data
- auditing required for sensitive entities

Prohibited

- automatic schema updates in production
- eager loading by default
- N+1 query patterns
- direct native queries unless justified

---

# Configuration Standards
Applications May include Confi based on profiles:

- application-dev.yml
- application-test.yml
- application-prod.yml

Configuration Rules

- use @ConfigurationProperties
- avoid excessive @Value
- environment variable externalization required
- secrets MUST NOT be hardcoded

---

# Logging, Monitoring & Observability
Logging Standards

- SLF4J required
- Logback required
- structured logging preferred
- correlation IDs required
- request tracing required

Monitoring Standards

- Spring Boot Actuator required
- Micrometer required
- distributed tracing required
- metrics endpoints required

# Resilience & Reliability Standards
Mandatory Patterns

- retry mechanisms
- timeout management
- graceful shutdown
- circuit breakers
- fallback handling

---

# Testing Standards
Required Testing Layers

- Unit Testing
- Slice Testing
- Integration Testing

Coverage Requirements

- minimum 80% business logic coverage
- critical paths require integration testing
- API validation testing required


# Planning Directives

MUST:
- prioritize maintainability and enterprise production readiness
- enforce layered architecture and DTO-based API contracts
- design for security-first and scalable operation
- favor modular, extensible structure with explicit configuration
- avoid deprecated Spring practices

MUST NOT:

- expose entities directly through APIs
- place business logic in controllers or repositories
- use field injection (`@Autowired` on fields)
- use `spring.jpa.hibernate.ddl-auto=update`
- generate tightly coupled modules or unstructured package hierarchies
- use generic exception handling patterns
- generate flat service architectures for complex domains

---
# Prefereed technology stack

| Category | Preferred Technology |
| --- | --- |
| Language | Java 21+ |
| Framework | Spring Boot 3+ |
| Security | Spring Security |
| ORM | Spring Data JPA |
| Migration | Flyway |
| Mapping | MapStruct |
| Validation | Jakarta Validation |
| Testing | JUnit 5 + Mockito |
| Integration Testing | Testcontainers |
| Observability | Micrometer |
| Resilience | Resilience4j |
| Documentation | OpenAPI/Swagger |
| Build Tool | Maven |
| Containerization | Docker |

# Enterprise Best Practices & Quality Attributes

These are the target standards, performance optimizations, and core pillars of a production-ready system.

System Attributes & Standards:

- Enterprise engineering standards
- Production readiness
- Maintainability
- Scalability
- Security
- Observability
- Modularity

Performance & Data Optimization:

- Caching strategy
- Async processing
- Database indexing
- Connection pooling
- API pagination
- Query optimization

Infrastructure & Operations:

- Secure secrets management
- Centralized logging
- Environment isolation

Architectural Anti-Patterns (What to Avoid)
These are structural flaws, poor coding practices, and technical debt indicators that violate enterprise standards.

Structural & Coupling Issues:

- Fat controllers
- God services
- Circular dependencies
- Tightly coupled modules
- Monolithic package dumping

Data & State Mishandling:

- Entity exposure (not using DTOs)
- Shared mutable utility state
- Missing transaction boundaries
- Business logic in repositories

Configuration & Error Handling Flaws:

- Hardcoded configuration
- Generic exception swallowing

---

# Official Technology Standards

All generated implementation guidance must align with official standards and current stable enterprise practices.

## Primary References

- Spring Boot Reference:
  https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/

- Spring Security:
  https://docs.spring.io/spring-security/reference/

- Spring Data JPA:
  https://docs.spring.io/spring-data/jpa/reference/

- Spring Modulith:
  https://docs.spring.io/spring-modulith/reference/

- Flyway:
  https://documentation.red-gate.com/fd

- Resilience4j:
  https://resilience4j.readme.io/