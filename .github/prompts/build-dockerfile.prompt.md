---
description: 'Write or review a Dockerfile with layering, a non-root user and container-aware JVM settings'
agent: agent
argument-hint: '[service]'
---
<!-- 140 | N. Build, CI and deployment | write -->
# 140 · Dockerfile for a Spring Boot service

Act as a senior engineer packaging JVM services for containers.

## Context
- Service: [SERVICE]; Java version: [JAVA_VERSION]; base image policy: [POLICY]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Write (or review) the Dockerfile so the image is small, cacheable, secure and correctly sized.

## Constraints
- Change only the files this task is about (tests, docs or build files). If production code looks wrong, report it instead of fixing it.
- Do not claim that anything passes or works unless you ran it.

## Cases to cover
- Multi-stage build; Spring Boot layered jar so dependency layers are cached.
- Non-root user; minimal runtime image; no build tools or secrets in the final image.
- Memory settings relative to the container limit (percentage-based heap), and exit on OutOfMemoryError.
- Signal handling so graceful shutdown works (exec form entrypoint).
- Time zone, locale and CA certificates.

## Code examples
Match the nearest existing test or document in this repository (naming, structure, libraries) and name the file you used as the model.

## Confirmation
- The Dockerfile with a comment per decision, plus the build and run commands to verify it.
