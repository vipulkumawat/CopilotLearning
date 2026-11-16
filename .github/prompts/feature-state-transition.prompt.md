---
description: 'Implement a status change with allowed-transition rules, audit and concurrency safety'
agent: agent
argument-hint: '[entity] : [from] -> [to]'
---
<!-- 031 | C. Feature development | build -->
# 031 · Workflow state transition

Act as a senior Java engineer modelling domain workflows.

## Context
- Entity: [ENTITY]; transition: [FROM_STATE] to [TO_STATE]
- Preconditions and side effects: [RULES]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Implement the transition in the domain model so that illegal transitions are impossible.

## Constraints
- Allowed transitions are defined in one place (enum or state machine), not as scattered if-statements.
- Plan first: list every file you will create or modify and why, then stop and wait for my approval.
- After approval implement exactly that plan, follow existing conventions, and do not touch unrelated code or change public signatures.

## Cases to cover
- Each illegal source state; repeating the transition (idempotent or error?).
- Two users transitioning the same entity concurrently.
- Side effect fails after the status is saved.
- Who did it and when must be recorded.

## Code examples
Before writing code, name the closest existing implementation in this repository and mirror its naming, packaging, error handling and test style. If I pasted an example, treat it as the pattern to follow.

## Confirmation
- A parameterised test over the full matrix of from/to states.
- A test that concurrent transitions produce one winner and one clean conflict.
