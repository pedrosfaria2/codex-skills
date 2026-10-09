---
name: code-smell-review
description: Inspect code, tests, and scripts for concrete code smells before acceptance; resolve every identified smell in the candidate and verify the simpler result.
---

# Code-smell review

Run before every acceptance involving code, including tests, scripts, and
integration changes. Linting helps find problems; a clean linter is not a
substitute for reading the code. For prose-only work, record that no executable
code changed and review the instructions with the documentation skill.

## Inspect the actual candidate

Read the final diff, affected callers, surrounding state, and tests. Trace the
normal path and relevant failures. Check for:

- Duplicated logic or state, unclear ownership, hidden mutation, and temporal
  coupling that forces callers to remember an undocumented sequence.
- Unnecessary abstraction, speculative generality, forwarding layers, mode flags,
  long argument lists, deep nesting, and branches obscuring the domain operation.
- Misleading names, mixed responsibilities, oversized operations, dead code,
  magic values, commented-out code, and stale or redundant explanations.
- Swallowed errors, implicit fallbacks, unbounded retries or resource growth,
  unsafe cleanup, and validation placed where it cannot enforce the contract.
- Avoidable allocations, copies, repeated scans, I/O, locks, and task or queue
  hops. Preserve correctness and measure executable changes before acceptance.
- Tests that mirror implementation, conceal their oracle, duplicate algorithms,
  or require substantial mental execution to understand the expected outcome.

A smell is a concrete maintenance, clarity, correctness, or cost problem in
context. Do not treat a line-count threshold, a pattern name, or personal taste
as proof. Necessary branching and validation remain explicit. Use actual
examples to explain why a finding harms this implementation.

## Acceptance gate

Record reviewed files and paths, findings, corrections, and verification evidence
in the task handoff. Rewrite confusing code rather than explaining a maze with
comments. Prefer a small direct correction; avoid speculative refactoring or
introducing another framework to satisfy the review.

**Never accept a candidate with an identified unresolved code smell.** Fix it,
rerun affected checks and measurements, and review the final diff again.
Do not rename a finding as technical debt, suppress a linter, or put it in a
pending report to waive acceptance. If a finding is not a smell after analysis,
record the concrete contract or evidence that resolves it.

Respect the authorized scope and read-only boundaries. An unrelated existing
finding belongs in the pending ledger; a finding that blocks the candidate's
correctness or integration must be resolved before acceptance. If resolution
needs unavailable authority, report the exact blocker and keep the affected
task unaccepted. A worker's review remains evidence for the primary to assess.
