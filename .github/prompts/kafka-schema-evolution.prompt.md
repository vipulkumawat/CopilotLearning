---
description: 'Assess compatibility of an event change and define a safe evolution process'
agent: plan
argument-hint: '[event] on [topic] : [planned change]'
---
<!-- 068 | F. Kafka | plan -->
# 068 · Event schema evolution

Act as an engineer who owns event contracts across teams.

## Context
- Event: [EVENT_NAME]; topic: [TOPIC]; planned change: [CHANGE]
- Known consumers: [CONSUMERS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Assess what the change breaks and define how to evolve this event safely.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Serialisation format and whether a schema registry enforces compatibility.
- Effect on each consumer of adding, removing, renaming or retyping a field; unknown enum values.
- Old events still in the topic and replayed after the change.
- Whether events carry a type and version discriminator.
- Order of deployment for producers and consumers.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A compatibility policy (backward, forward or full), the rollout sequence and the procedure for a genuinely breaking change.
