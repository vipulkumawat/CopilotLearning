---
description: 'Find configuration, data, version or infrastructure differences behind an environment-only failure'
agent: ask
argument-hint: '[symptom and environment]'
---
<!-- 118 | K. Production debugging | ask -->
# 118 · Works locally, fails in an environment

Act as a senior engineer debugging an environment-specific failure.

## Context
- Symptom: [SYMPTOM]; fails in: [ENVIRONMENT]; works in: [OTHER_ENVIRONMENT]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
List the differences between the environments that could explain the behaviour, most likely first.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Active profiles and property overrides; missing environment variables or secrets.
- Data volume and shape; time zone, locale and encoding.
- Several instances versus one (caches, sessions, scheduled tasks, locks).
- Network: proxies, TLS, DNS, timeouts, firewalls.
- JVM, container limits and dependency versions.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A checklist of differences with the command or endpoint to verify each.
