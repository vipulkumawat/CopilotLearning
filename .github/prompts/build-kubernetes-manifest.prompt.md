---
description: 'Write or review probes, resources, rollout and shutdown settings for a JVM service'
agent: agent
argument-hint: '[service and manifest]'
---
<!-- 141 | N. Build, CI and deployment | write -->
# 141 · Kubernetes deployment review

Act as a senior engineer who runs JVM services on Kubernetes.

## Context
- Service: [SERVICE]; manifest: [PASTE_OR_FILE]; startup time: [SECONDS]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Check that the deployment starts, scales, rolls out and stops without dropping requests.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Startup, readiness and liveness probes mapped to the right actuator endpoints, with thresholds that fit startup time.
- CPU and memory requests and limits versus JVM heap and thread counts; CPU throttling.
- Rolling update settings, pod disruption budget and replicas.
- terminationGracePeriodSeconds, preStop delay and graceful shutdown timeout.
- Configuration and secrets sources; database connections times replicas.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The corrected manifest fragments with the reason for each value.
