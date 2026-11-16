---
description: 'Review what is cached, where, for how long, and how it is invalidated'
agent: plan
argument-hint: '[service or cache config]'
---
<!-- 096 | I. Performance and JVM | plan -->
# 096 · Caching strategy review

Act as a senior engineer who treats caches as a consistency trade-off.

## Context
- Target: [SERVICE_OR_CACHE_CONFIG]; cache technology: [CAFFEINE_REDIS_OTHER]
- If a [PLACEHOLDER] above is still unfilled, take its value from the text I typed after this command, the current selection or the open file. If it is still unknown, ask me before proceeding.

## Capability
Review existing caches and identify both risky caching and missing caching.

## Constraints
- Design only: no implementation code until I choose an option.
- Cite the files you read, label assumptions, and give trade-offs rather than only a recommendation.

## Cases to cover
- TTL and size limits; entries that never expire.
- Invalidation on every write path, across instances and services.
- Keys missing tenant, user, locale or permission dimensions.
- Entities or mutable objects cached; serialisation compatibility across deployments.
- Stampede on expiry; behaviour when the cache is down.
- Read paths where caching would help, with the staleness the business accepts.

## Code examples
Ground the design in this repository: name the existing classes, configuration and conventions it builds on, and sketch key signatures or configuration snippets rather than full implementations.

## Confirmation
- A table: cache, purpose, TTL, invalidation, risk, recommendation.
