---
applyTo: '**/src/main/java/**/*.java'
description: 'Rules for production Java code'
---
# Production Java code

- Follow the package and naming conventions of the neighbouring classes; name the class you copied the pattern from.
- Constructor injection with `final` fields. Singleton beans hold no mutable state.
- Public methods validate their arguments or document their null contract. Return empty collections, never `null`.
- `Optional` is a return type only, never a field or parameter.
- Prefer immutable types: records for data carriers, `List.copyOf` for defensive copies.
- Exceptions: specific types, always keep the cause, never log and rethrow the same exception.
- Restore the interrupt flag when catching `InterruptedException`.
- Every remote call has explicit connect and read timeouts.
- No `System.out`, no `printStackTrace`, no `Thread.sleep` in production code.
- Use an injected `Clock` rather than `now()` with the system default zone.
- Keep methods short enough to read without scrolling; extract a named method instead of adding a comment.
