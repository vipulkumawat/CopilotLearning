---
applyTo: '**/batch/**/*.java,**/*Job*.java,**/*Step*.java,**/*ItemReader*.java,**/*ItemProcessor*.java,**/*ItemWriter*.java,**/*Tasklet*.java'
description: 'Rules for Spring Batch jobs'
---
# Spring Batch code

- Every job must be restartable: reader state lives in the `ExecutionContext`, and writers are idempotent so a replayed chunk does not double-apply.
- Job parameters identify the run (for example the business date). Do not add a random or timestamp parameter just to force a new instance.
- Components that use job parameters are `@StepScope`. No state in fields that survives between runs.
- State the chunk size and why. Readers set a fetch size; writers use JDBC batching.
- No row-by-row lookups in a processor when the data can be joined in the reader or preloaded.
- Skips are deliberate: name the skippable exceptions, set a limit, and record every skipped item with its reason.
- No non-transactional side effects (HTTP, Kafka, files) inside a chunk unless they are idempotent.
- Report read, written, filtered and skipped counts at the end of every run; they must reconcile.
- Prevent concurrent runs of the same job across instances.
- Test with `spring-batch-test`, including a failure followed by a restart.
