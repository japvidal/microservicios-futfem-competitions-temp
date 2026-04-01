# microservicios-futfem-competitions-temp

`microservicios-futfem-competitions-temp` is the temporary or staging companion service for competition data in the Tikitakas backend. It follows the same architectural style as the main `competitions` service, but it is intended for transitional, imported, staged, or intermediate competition records depending on the workflow being used by the platform.

The project is built with Java 21, Spring Boot, Spring Data JPA, MySQL, Springdoc OpenAPI, and Maven Wrapper. It also uses the shared abstractions from `microservicios-common`, which allows the repository to keep a very compact codebase while still exposing standard CRUD behavior. The service registers in Eureka and is routed externally through the API gateway.

Typical local execution:

```bash
./mvnw spring-boot:run
```

Gateway route:

- `/api/futfem/competitionstemp/**`

In `v0.1.0`, this service includes Docker-friendly packaging, Jenkins pipeline support, and OpenAPI server configuration that makes Swagger work correctly behind the gateway. That means the generated API docs now point to the gateway path instead of internal container addresses.

Use this repository when the application needs a temporary competition dataset separated from the canonical competition service while still preserving the same deployment and observability model as the rest of the Tikitakas backend.
