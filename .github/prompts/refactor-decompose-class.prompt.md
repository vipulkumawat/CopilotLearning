---
description: 'Plan how to split a god class into cohesive units without a big-bang rewrite'
agent: plan
argument-hint: '[class]'
---
<!-- 126 | L. Security and code quality | plan -->
# 126 · Decompose a large class

Act as a senior engineer restructuring a large class incrementally.

## Context
- Target: [CLASS]; lines and dependency count: [SIZE]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Identify the separate responsibilities in the class and plan an incremental extraction.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Clusters of methods and fields that change together.
- Dependencies used by only one cluster.
- Shared mutable state that makes extraction hard.
- Transaction boundaries and proxy behaviour that will change when methods move to another bean.
- The extraction with the best value-to-risk ratio to do first.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A responsibility map, a target structure and an ordered list of steps that each leave the code working.
