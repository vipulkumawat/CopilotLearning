---
applyTo: '**/db/migration/**/*.sql,**/db/changelog/**/*'
description: 'Rules for database migration scripts'
---
# Database migrations

- Never edit a migration that has already been applied; add a new one.
- Every migration must work while the previous application version is still running (rolling deployment): expand first, contract in a later release.
- No column drop, rename or type change in the same release as the code that stops using it.
- New `NOT NULL` columns need a default or a backfill step first.
- Backfills on large tables run in batches and are restartable; no single statement that locks or rewrites a large table.
- Create indexes with the engine's online or concurrent option where available, and say which queries each index serves.
- Flag any statement that takes a long lock, with its expected duration at production volume.
- Write the scripts; do not run them.
