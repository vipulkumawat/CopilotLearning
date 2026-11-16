# Copilot for Java teams: training guide and prompt library

A working kit for Java / Spring Boot / JPA / Kafka / Spring Batch developers who want Copilot to do the
legwork (reading, tracing, drafting, checking) so their own attention goes to architecture and business rules.

| What | Where | Purpose |
|---|---|---|
| This guide | `README.md` | How to work with Copilot day to day |
| Always-on instructions | [.github/copilot-instructions.md](.github/copilot-instructions.md) | Project context and working rules, sent with every chat request |
| Path-scoped rules | [.github/instructions/](.github/instructions/) | Extra rules applied automatically to tests, JPA, Kafka, Batch, API and migration files |
| 160 prompts | [.github/prompts/](.github/prompts/) | Slash commands, one per task |
| Index | [PROMPTS.md](PROMPTS.md) | Every prompt by category, with its command and input |
| Copy-paste catalogue | [docs/all-prompts.md](docs/all-prompts.md) | All prompts in one file, for chat windows without slash commands |

## 1. Setup (30 minutes, once per repository)

1. Copy the `.github` folder into your service repository (merge with an existing one).
2. Fill in every `[BRACKET]` in `copilot-instructions.md`: what the system does, the stack, the package
   structure, three or four classes that are good examples, and the build commands. This is the highest-value
   step in the whole kit: it is the context you would otherwise retype in every prompt.
3. Adjust the `applyTo` globs in `.github/instructions/*.instructions.md` to your package names.
4. In Copilot Chat type `/` and start typing a category prefix (`jpa-`, `kafka-`, `test-`) to see the prompts.
   If your chat window does not list them, use `docs/all-prompts.md` and copy the text.
5. Delete the prompts you will never use. A short list you know beats a long list you scroll.

## 2. The division of labour

You keep the decisions. Copilot gets everything that is mostly reading and typing.

| Delegate to Copilot | Keep for yourself |
|---|---|
| Tracing a flow, finding callers, mapping configuration | Deciding what the system should do |
| Listing edge cases and failure modes | Deciding which of them matter to the business |
| Drafting code that follows an existing pattern | Choosing the pattern and the boundaries |
| Writing tests, builders, mappers, migrations, Javadoc, PR text | Reviewing them and owning the result |
| Proposing options with trade-offs | Choosing the option |
| Producing hypotheses for a production problem | Confirming them with evidence |

The time you save is real only if you do not spend it re-prompting. That depends on the next three sections.

## 3. The 6C framework

Every prompt in this library has the same six parts. Use them for your own prompts too.

| C | Question it answers | In this kit it comes from |
|---|---|---|
| **Context** | Where does this live, and what exists already? | `copilot-instructions.md` plus the placeholders you fill in |
| **Capability** | What exactly should be produced? | One or two sentences in the prompt |
| **Constraints** | What must be used, followed and left alone? | Instruction files plus the prompt's own rules |
| **Cases** | Normal, edge and failure scenarios? | The checklist in each prompt; add your business cases |
| **Code examples** | What does good look like here? | An existing class you point at, or sample input and output |
| **Confirmation** | How do we know it is right? | Tests and outputs the prompt demands |

### Before and after

Weak prompt:

> add an endpoint to cancel an order

Copilot must guess the path, the rules, the error format, the test style and the definition of "cancel".
You then spend four rounds correcting the guesses.

The same request with 6C:

```text
Context: OrderController and OrderService in com.acme.orders. Orders have status NEW, PAID, SHIPPED, CANCELLED.
Capability: add POST /orders/{id}/cancel that cancels an order and returns the updated order.
Constraints: follow OrderController.confirm() as the pattern; no new dependencies; do not change existing
  signatures; the status change belongs in the Order aggregate, not the controller.
Cases: NEW or PAID -> CANCELLED. SHIPPED -> 409. Already CANCELLED -> 200, no change (idempotent).
  Unknown id -> 404. Not the owner -> 403. Two cancels at the same time -> one wins, the other gets 200.
Code example: error body as produced by GlobalExceptionHandler; tests in the style of OrderControllerTest.
Confirmation: @WebMvcTest for every case above, a unit test for Order.cancel(), and a list of the files you
  will change before you change anything.
```

You wrote six lines, all of them business decisions. Everything else was already in the instruction files.
In this library that request is `/feature-state-transition` with the placeholders filled in.

**The part only you can supply is Cases.** Copilot knows what an N+1 query is. It does not know that a shipped
order cannot be cancelled. Spend your prompt-writing effort there.

## 4. Choosing the mode

| You want | Use | Typical prompts |
|---|---|---|
| To understand or audit, with no risk | **Ask** mode (read-only) | `understand-*`, `debug-*`, every review prompt |
| A design or a decision to make | **Plan** mode | `feature-story-to-plan`, `db-schema-migration`, `kafka-retry-dlt-design` |
| Changes across several files | **Agent** mode, with the plan-then-approve gate | `feature-*`, `jpa-n-plus-one`, `conc-race-check-then-act` |
| The next few lines while you type | Inline completion, steered by a comment | Section 5 |
| A small edit to code in front of you | Inline chat on a selection | "extract this into a method", "add null handling" |

Each prompt file sets its mode in the `agent:` line of its front matter, so the slash command switches for you.

## 5. Comment-driven completion

Inline completion reads the file you are in and the tabs you have open. A good comment is a 6C prompt in
miniature: say what goes in, what comes out, and the cases.

Weak:

```java
// calculate discount
```

Strong:

```java
/**
 * Returns the discount for an order as a percentage between 0 and 30.
 * - Gold customers: 10%. Platinum: 15%. Others: 0%.
 * - Add 5% when the order total exceeds 1000.00 (strictly greater).
 * - Add 10% during a campaign (campaign.isActive(today)).
 * - The sum is capped at 30%.
 * - A null customer tier is treated as "other". Total must not be negative: IllegalArgumentException.
 * Pure function: no I/O, no clock access; "today" is passed in.
 */
BigDecimal discountPercent(CustomerTier tier, BigDecimal orderTotal, Campaign campaign, LocalDate today) {
```

Habits that make completions better:

- Write the **signature and Javadoc first**, then let Copilot write the body.
- Write the **test first**. With `OrderServiceTest` open, the completion of `OrderService` follows the test.
- **Open the files you want imitated** (the similar service, the DTO, the entity) in other tabs.
- Use **precise names**. `findActiveOrdersByCustomerIdOrderByCreatedAtDesc` almost writes itself; `getData` does not.
- For a sequence of steps, write the steps as comments first, then complete under each:
  `// 1. load order or throw NotFound` / `// 2. check ownership` / `// 3. apply transition` / `// 4. publish event after commit`.
- Reject a wrong suggestion quickly and improve the comment. Do not edit a bad suggestion into shape.

## 6. The working loop

Use the same loop for every non-trivial task. Each step is cheap, and each catches a different kind of mistake.

| Step | What you do | Prompts |
|---|---|---|
| 1. Understand | Have Copilot read before anyone writes | `understand-request-flow`, `understand-change-impact` |
| 2. Plan | Ask for options or a file-by-file plan | `feature-story-to-plan`, `feature-plan-first` |
| 3. Decide | **You** choose, correct the plan, add missing cases | (your judgement) |
| 4. Implement | Approve; Copilot implements exactly the plan | the matching `feature-*`, `jpa-*`, `kafka-*`, `batch-*` |
| 5. Verify | Run the tests yourself; ask for the missing ones | `test-*`, `conc-write-concurrency-test` |
| 6. Review | A fresh chat reviews the diff | `pr-self-review`, `pr-review-diff` |
| 7. Describe | Commit message and pull request text | `pr-commit-message`, `pr-description` |

Step 3 is where your saved mental energy goes. A plan takes a minute to read and is far cheaper to correct than code.

## 7. Giving Copilot the right context

- **Point, do not describe.** Attach the file (`#file:` or drag it in), or select the code. "Like `OrderService.confirm`" beats a paragraph of description.
- **Paste the evidence.** Stack trace, failing test output, SQL, `EXPLAIN` plan, log lines, the sample message. Never paraphrase an error.
- **Give numbers.** Row counts, message rates, instance counts, latency targets. "Large table" produces generic advice; "40 million rows" produces a batched migration.
- **One task per chat.** Start a new chat for a new task; old context degrades answers.
- **Review in a fresh chat.** The chat that wrote the code will defend it.
- **Say what you already ruled out.** It stops Copilot proposing it again.

## 8. Playbooks

Chains of prompts for the situations you meet most.

**A new story**
`feature-story-to-plan` -> answer the questions -> `understand-change-impact` -> `feature-plan-first` (or the specific `feature-*`) -> `test-service-unit` -> `pr-self-review` -> `pr-description`

**A new or changed JPA query**
`jpa-write-query` -> check the SQL it shows -> `test-repository-testcontainers` -> `jpa-n-plus-one` on the calling endpoint

**A new Kafka consumer**
`kafka-retry-dlt-design` (decide retry and dead-letter policy) -> `kafka-implement-consumer` -> `kafka-consumer-idempotency` -> `test-kafka-integration` -> `kafka-consumer-lag-review`

**Publishing an event from a transaction**
`dist-dual-write-audit` -> `feature-domain-event` or `kafka-outbox-pattern` -> `kafka-schema-evolution` for later changes

**A new batch job**
`batch-job-design` -> `batch-restartability-skip` -> `test-batch-job` -> `batch-performance-tuning` once it runs on real volume

**"It sometimes produces wrong totals"** (suspected race)
`conc-race-check-then-act` -> `conc-write-concurrency-test` -> `jpa-optimistic-locking` or `conc-locking-strategy`

**A production error**
`debug-stack-trace` or `debug-log-analysis` -> confirm with the evidence it asks for -> `debug-bug-reproduction-first` -> `debug-postmortem`

**A slow endpoint**
`debug-slow-endpoint` -> `jpa-n-plus-one` / `db-sql-tuning` / `api-http-client-hardening`, depending on the evidence

**Inheriting unfamiliar code**
`understand-codebase-tour` -> `understand-request-flow` -> `understand-domain-rules` -> `test-characterization` before the first change

**Before a release**
`db-schema-migration` -> `api-backward-compat` -> `spring-operational-readiness` -> `doc-release-notes`

## 9. Habits that waste the saving

| Habit | Cost | Do this instead |
|---|---|---|
| One-line prompts for multi-file work | Several correction rounds | Use the 6C prompt; state the cases |
| Letting the agent code before you saw a plan | Large diff in the wrong direction | Plan, approve, then implement |
| Accepting a claim about your code unchecked | A confident, wrong statement reaches production | Open the cited method and read it |
| Asking for a fix before reproducing the bug | The symptom is patched, the cause stays | `debug-bug-reproduction-first` |
| Asking the same chat to review its own code | It agrees with itself | New chat, `pr-self-review` |
| Retyping the stack and conventions | Minutes per prompt, inconsistent results | Put them in `copilot-instructions.md` once |
| Asking "is this OK?" | "Yes, looks good" | Ask "how does this fail?" and name the failure types |
| Treating generated tests as proof | Tests that mirror the implementation's bugs | Check that each test would fail if the rule were broken |

## 10. What Copilot cannot do for you

- It does not know your business rules unless you state them. Missing rules become plausible inventions.
- It does not know production: volumes, traffic shape, which consumer is fragile. Give it the numbers.
- It cannot see other repositories. Consumers of your API or events have to be named by you.
- Version-specific facts (a property renamed in a Spring Boot release, a Hibernate default) can be out of date. Check the release notes for anything an upgrade depends on.
- It has not run anything unless it shows you the command and the output.

Treat every answer as a draft from a fast colleague who has not been on your project for long: usually right, cheap to check, and your responsibility once merged.

## 11. A two-week practice plan

| Days | Practise | Goal |
|---|---|---|
| 1 | Fill in `copilot-instructions.md`. Run `understand-codebase-tour` on your own module and correct what it gets wrong by improving the instructions. | Copilot describes your system accurately |
| 2-3 | Use only read-only prompts on real work: `understand-change-impact`, `jpa-transaction-boundaries`, `test-gap-analysis`. Verify every finding. | You learn how far to trust it, at no risk |
| 4-5 | Comment-driven completion: signature and Javadoc first, tests first, for every new method. | Fewer rejected suggestions |
| 6-8 | One full story through the working loop in section 6, plan approval included. | The loop becomes a habit |
| 9-10 | A playbook from section 8 that matches your current work (Kafka consumer, batch job, slow endpoint). | You chain prompts instead of improvising |
| 11-12 | Review every pull request of your own with `pr-self-review` before asking a colleague. | Fewer review rounds |
| 13-14 | Edit the library: delete unused prompts, add your team's cases to the ones you use, write one new prompt in 6C form. | The library fits your team |

## 12. Maintaining the library

- A prompt is a file in `.github/prompts/` named `<category>-<task>.prompt.md`. Copy an existing one to add your own.
- Keep the comment line under the front matter (`<!-- number | category | kind -->`); the index is built from it.
- After adding or editing prompts, rebuild the index and the catalogue:

```bash
python tools/build_catalog.py
```

- When Copilot repeatedly gets something wrong, fix it at the right level: a project fact goes in
  `copilot-instructions.md`, a rule for one kind of file goes in `.github/instructions/`, and a missing case
  goes in the prompt.
- Review the instruction files when the stack changes. Stale instructions are worse than none.
