---
applyTo: '**/*Controller.java,**/controller/**/*.java,**/api/**/*.java,**/web/**/*.java'
description: 'Rules for REST controllers and API DTOs'
---
# REST API code

- Controllers translate HTTP to a service call and back. No business logic, no repositories, no transactions.
- Request and response DTOs are records with Bean Validation; `@Valid` on every request body. Never accept or return JPA entities.
- Every string has a maximum length and every collection a maximum size.
- Clients never supply `id`, `version`, owner, tenant, role or audit fields for a create.
- Errors go through the global handler in the project's standard error format; no stack traces or internal names in responses.
- Status codes: 201 with `Location` for create, 204 for no content, 400 validation, 404 missing, 409 conflict.
- List endpoints are paginated with a server-enforced maximum page size and a whitelist of sortable fields.
- Every operation states who may call it; check object-level access, not only the role.
- Changes to an existing contract must be additive unless I approve a breaking change.
