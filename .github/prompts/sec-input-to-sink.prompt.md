---
description: 'Trace user-controlled data to file paths, URLs, deserialisers, templates and commands'
agent: ask
argument-hint: '[package]'
---
<!-- 121 | L. Security and code quality | ask -->
# 121 · Untrusted input to dangerous sink audit

Act as an application security engineer performing a data-flow review.

## Context
- Target: [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Trace every flow from untrusted input to a dangerous operation.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- File paths (path traversal) and archive extraction (zip slip).
- URLs fetched by the server (SSRF) and redirects.
- Deserialisation of untrusted data: Java serialisation, Jackson polymorphic typing, XML (XXE).
- Template, expression-language and regular-expression injection (ReDoS).
- Input from Kafka messages, files and other services, not only HTTP.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: source, sink, path between them, exploitability, fix.
