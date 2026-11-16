---
description: 'Find hard-coded secrets, unsafe defaults and sensitive values exposed by configuration'
agent: ask
argument-hint: '[repository or module]'
---
<!-- 122 | L. Security and code quality | ask -->
# 122 · Secrets and sensitive configuration review

Act as a security engineer reviewing configuration hygiene.

## Context
- Scope: [MODULE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Find secrets and unsafe settings in code, configuration, tests and build files.

## Constraints
- Never print a secret's value; give the file, the key name and the kind of secret.
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Passwords, tokens and keys in source, YAML, test resources, Dockerfiles and CI files.
- Secrets with default values, or logged at startup.
- Actuator env, configprops or heapdump endpoints exposed.
- Debug settings, permissive TLS or disabled certificate checks.
- Secrets that must be rotated because they are already in version history.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A findings table with severity and the remediation, including rotation.
