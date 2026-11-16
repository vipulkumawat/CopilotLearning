---
description: 'Generate a Mermaid diagram of a flow or lifecycle from the actual code'
agent: agent
argument-hint: '[flow or entity lifecycle]'
---
<!-- 159 | P. Pull requests, documentation and workflow | write -->
# 159 · Sequence or state diagram from code

Act as an engineer documenting how the system really behaves.

## Context
- Subject: [FLOW_OR_ENTITY_LIFECYCLE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Produce a Mermaid sequence diagram (for a flow) or state diagram (for a lifecycle) derived from the code.

## Constraints
- Draw only what the code does; mark anything inferred.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Synchronous versus asynchronous interactions.
- Transaction boundaries.
- Error and retry paths, not only the happy path.
- Every state and transition, including ones reachable only by jobs or consumers.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The diagram plus a legend mapping each participant or transition to a class and method.
