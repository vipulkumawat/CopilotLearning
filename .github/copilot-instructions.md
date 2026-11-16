# Copilot instructions for this repository

<!-- Fill in every [BRACKET] once. This file is sent with every Copilot Chat request,
     so anything written here never has to be typed into a prompt again. Keep it under two pages. -->

## What this system is
- Purpose: [ONE OR TWO SENTENCES: what the service does for the business]
- Domain terms: [TERM = meaning; TERM = meaning]
- Main flows: [e.g. REST API -> service -> PostgreSQL; consumes `orders.created`, publishes `payments.settled`; nightly settlement batch]

## Stack
- Java [21], Spring Boot [3.x], build with [Maven | Gradle]
- Persistence: Spring Data JPA / Hibernate [6.x] on [PostgreSQL | Oracle | MySQL]; migrations with [Flyway | Liquibase]
- Messaging: Spring Kafka, [JSON | Avro] payloads, [schema registry: yes | no]
- Batch: Spring Batch [5.x]
- Tests: JUnit 5, Mockito, AssertJ, Testcontainers, [WireMock], [Awaitility]
- Other: [MapStruct | Lombok | Resilience4j | Micrometer | ShedLock | Redis ...]

## Structure
- Packages: [e.g. com.acme.orders.{api, application, domain, infrastructure}]
- Layering rule: [controller -> service -> repository; domain has no Spring or JPA imports]
- Good examples to copy: [OrderController], [OrderService], [OrderRepository], [OrderCreatedListener], [OrderServiceTest]

## How to work with me
- For any change beyond one method: investigate, then list the files you will touch and why, then wait for my approval before editing.
- Make the smallest change that satisfies the request. Do not refactor, rename or reformat unrelated code.
- Copy the nearest existing pattern in this repository rather than introducing a new style or library.
- Cite file, class and method for every claim about this codebase. Say "I could not verify" instead of guessing.
- Separate what the code proves from what you infer.
- Never claim that tests pass, a build works or a bug is fixed unless you ran it; say exactly what you ran.
- If the request is ambiguous or a business rule is missing, ask before coding.
- Architecture and business decisions are mine: give options with trade-offs, then let me choose.

## Java standards
- Constructor injection only. No field injection, no static mutable state.
- DTOs are records. JPA entities are never exposed through the API or published as events.
- Validate at the boundary with Bean Validation. Throw specific exceptions; never swallow them; never catch `Exception` to continue silently.
- `java.time` only, with an injected `Clock`. `BigDecimal` for money, with explicit scale and `RoundingMode`.
- No new dependency without asking first.
- Logging through SLF4J with parameters, never string concatenation. Never log secrets, tokens or personal data.

## Always consider
- Transactions: where the boundary is, and no remote calls inside it.
- Concurrency: this service runs on [N] instances; assume concurrent requests and duplicate messages.
- Failure: timeouts on every remote call; what happens on retry; what is left behind on a crash.
- Compatibility: API, event and database changes must work during a rolling deployment.

## Build and verify
- Build: `[./mvnw -q verify]`   Unit tests: `[./mvnw test]`   One test: `[./mvnw test -Dtest=ClassName]`
- Run locally: `[./mvnw spring-boot:run -Dspring-boot.run.profiles=local]`
- Required local infrastructure: [docker compose up -d]
