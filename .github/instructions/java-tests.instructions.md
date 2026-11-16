---
applyTo: '**/src/test/java/**/*.java'
description: 'Rules for Java tests'
---
# Tests

- JUnit 5, AssertJ assertions, Mockito only for collaborators that cross a boundary. Use real value objects.
- One behaviour per test. Name: `methodOrScenario_condition_expectedResult` or a `@DisplayName` in business language.
- Arrange / act / assert, separated by blank lines. No logic (loops, conditionals) in tests.
- Use `@ParameterizedTest` for boundary values and input/outcome tables.
- Assert on outcomes and state. Verify interactions only when the interaction is the behaviour.
- Never `Thread.sleep`: use Awaitility for asynchronous assertions and a fixed `Clock` for time.
- Database tests run against Testcontainers with the real migrations, not H2 or Hibernate auto-DDL.
- Use the narrowest Spring slice that works (`@WebMvcTest`, `@DataJpaTest`); `@SpringBootTest` only for true end-to-end flows.
- Tests must not depend on execution order or shared mutable state, and must clean up what they create.
- If a test reveals behaviour that looks like a bug, report it; do not write a test that blesses it.
