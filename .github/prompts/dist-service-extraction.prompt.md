---
description: 'Assess and plan extracting a module from a monolith, starting from its data and call coupling'
agent: plan
argument-hint: '[module]'
---
<!-- 137 | M. Distributed systems and observability | plan -->
# 137 · Extract a module into a service

Act as a software architect planning an incremental extraction.

## Context
- Module: [MODULE]; reason for extracting: [REASON]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Assess how coupled the module is and propose an incremental extraction path.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Inbound and outbound calls, and shared tables, joins and transactions.
- Operations that are atomic today and will become distributed.
- Data ownership, migration and the period when both write.
- Chatty call patterns that become network calls.
- Whether a well-bounded module inside the monolith achieves the goal more cheaply.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A coupling report, an ordered strangler-style plan with a rollback point per step, and the decision criteria for stopping.
