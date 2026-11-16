---
description: 'Assess an upgrade of Java and Spring Boot versions and produce a phased plan'
agent: plan
argument-hint: 'Java [old] -> [new], Spring Boot [old] -> [new]'
---
<!-- 144 | O. Upgrades and migrations | plan -->
# 144 · Java and Spring Boot upgrade assessment

Act as a senior engineer planning a platform upgrade.

## Context
- Java [OLD_JAVA] to [NEW_JAVA]; Spring Boot [OLD_BOOT] to [NEW_BOOT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find what breaks and produce a phased upgrade plan.

## Constraints
- Verify claims about version changes against the official migration guides and release notes; say when you are relying on memory.
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Removed or deprecated APIs in use; javax to jakarta namespace changes.
- Libraries needing minimum version bumps; ones with no compatible release.
- Reflection, bytecode tooling and serialisation affected by module encapsulation.
- Renamed configuration properties and changed defaults.
- Build plugin changes; language features worth adopting, ranked by value.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A phased plan with a rollback point after each phase and the test evidence required to pass each gate.
