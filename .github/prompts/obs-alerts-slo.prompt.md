---
description: 'Define service level indicators, objectives and actionable alerts for a service'
agent: plan
argument-hint: '[service]'
---
<!-- 132 | M. Distributed systems and observability | plan -->
# 132 · Alerts and SLO design

Act as a site reliability engineer designing alerting.

## Context
- Service: [SERVICE]; what users depend on it for: [USER_JOURNEYS]
- Metrics available today: [METRICS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Propose indicators, objectives and alerts that page only when a human must act.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- Availability and latency per key endpoint; freshness and lag for consumers and batch jobs.
- Saturation signals: pools, queues, heap, disk.
- Symptom-based alerts over cause-based ones; burn-rate alerting.
- Alerts for "nothing happened": job did not run, no messages consumed.
- Each alert's first diagnostic step.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A table: indicator, objective, alert condition, severity, runbook link placeholder, and the missing metrics to add.
