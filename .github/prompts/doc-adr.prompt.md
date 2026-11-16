---
description: 'Draft an ADR with context from the code, real alternatives and consequences'
agent: agent
argument-hint: '[decision to make]'
---
<!-- 155 | P. Pull requests, documentation and workflow | write -->
# 155 · Architecture decision record

Act as a software architect documenting a decision for future maintainers.

## Context
- Decision: [DECISION_TO_MAKE]
- Constraints and drivers I already know: [DRIVERS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Draft the Architecture Decision Record.

## Constraints
- The decision is mine. Present the options fairly; do not argue only for your favourite.
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Context and forces: business, technical and operational.
- At least three options, including "do nothing".
- For each: benefits, costs, operational burden and failure modes.
- The recommended option and why.
- Consequences, and what would make us revisit the decision.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- An ADR in this project's template, with the context grounded in files from this repository.
