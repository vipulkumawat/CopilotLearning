---
description: 'Find validation gaps in request DTOs and unvalidated data flowing to queries, paths and URLs'
agent: ask
argument-hint: '[DTO package]'
---
<!-- 036 | D. Spring Boot and APIs | ask -->
# 036 · Input validation audit

Act as a senior Java engineer auditing input validation.

## Context
- Target: request DTOs under [PACKAGE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check every inbound field for missing constraints and for unvalidated flow into sensitive sinks.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Missing @NotNull, size, range or pattern constraints; strings with no maximum length.
- Collections without @Size; nested objects without @Valid; @Valid or @Validated missing on the controller parameter.
- Path variables and request parameters with no constraints.
- Strings that flow into queries, file paths, URLs, logs or HTML.
- Cross-field rules enforced nowhere.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: DTO, field, issue, suggested constraint.
- The top five gaps by exploitability.
