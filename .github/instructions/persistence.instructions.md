---
applyTo: '**/*Repository.java,**/*Entity.java,**/repository/**/*.java,**/entity/**/*.java,**/persistence/**/*.java,**/domain/**/*.java'
description: 'Rules for JPA entities, repositories and transactional code'
---
# JPA and Hibernate code

- All associations are `LAZY`. Fetch what a use case needs with a join fetch, `@EntityGraph` or a DTO projection.
- Whenever you write or change a query, show the SQL it generates and say which index it uses.
- No Lombok `@Data`, `@EqualsAndHashCode` or `@ToString` on entities. `equals`/`hashCode` are based on a business key or the id, and are proxy-safe.
- Enums are stored as `STRING`. Money columns state precision and scale.
- Keep both sides of a bidirectional association in sync through helper methods on the owning aggregate.
- `@Transactional` belongs on the service layer; `readOnly = true` for queries. No remote calls (HTTP, Kafka) inside a transaction.
- Do not call a `@Transactional` method from the same class and expect it to apply.
- Parameters are always bound; never build JPQL or SQL by concatenation.
- Read-only list queries return projections with pagination, never unbounded entity lists.
- Bulk updates bypass the persistence context and `@Version`: flush and clear around them and say so.
- Schema changes go through a migration script; never rely on `ddl-auto`.
