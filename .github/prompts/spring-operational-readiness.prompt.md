---
description: 'Review actuator health, probes, graceful shutdown and startup behaviour'
agent: ask
argument-hint: '[service]'
---
<!-- 047 | D. Spring Boot and APIs | ask -->
# 047 · Health, readiness and graceful shutdown review

Act as a senior engineer preparing a service for production operation.

## Context
- Service: [SERVICE]; runs on: [PLATFORM, e.g. Kubernetes]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that the service reports its health truthfully and stops without losing work.

## Constraints
- Read-only: do not modify any files.
- Cite file, class and method for every claim, and label anything you could not verify as an assumption.

## Cases to cover
- Liveness versus readiness: a downstream outage must not restart every pod.
- Health indicators that are slow, missing or expose details publicly.
- Graceful shutdown: in-flight HTTP requests, Kafka listeners, scheduled tasks, executors and batch steps.
- Shutdown timeout versus the platform's termination grace period.
- Actuator endpoints exposed and who can reach them.

## Code examples
Quote the exact code behind every finding (file, class, method). For each recommended change show a short before/after snippet written in this project's style.

## Confirmation
- A table: concern, current behaviour, risk, change.
- The exact properties and probe settings recommended.
