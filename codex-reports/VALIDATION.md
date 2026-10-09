# Validation evidence

Status: uninitialized. No checks, measurements, reviews, or live runs performed.

## Per-task record

For each task, record the candidate revision or exact changed-file state,
working directory, versions, environment, inputs, and required gates. Keep
commands, results, selected test counts, skipped cases, output evidence, and
unrun checks explicit. Link durable evidence stored under this report directory;
exclude secrets and irrelevant raw output.

Record the primary's final diff review, code-smell findings and resolutions,
comment/documentation review, test readability and independent-oracle review,
and any faithful source-to-destination test mapping.

For executable behavior, record the representative workload, success and failure
paths, correctness oracle, optimized configuration, measurement boundaries,
warmup, repetitions, units, distributions, and resource use. Explain genuine
inapplicability or demonstrated literal impossibility with attempted remedies.
Never score unmeasured performance or call a planned experiment completed.

## Operational qualification

No deliverable has been qualified. Record actual startup, interaction, outputs,
real integration versus fixtures, relevant failure and cleanup behavior, and
sanitized evidence for each usable partial and final requested flow. Include
limitations and whether the primary accepted the result.

## Review history

No reviews yet. Link task IDs from [PLAN.md](PLAN.md), decisions from
[DECISIONS.md](DECISIONS.md), and unresolved findings from [PENDING.md](PENDING.md).
