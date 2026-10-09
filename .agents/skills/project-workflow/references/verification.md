# Verify the actual deliverable

## Establish commands

Inspect manifests, lockfiles, scripts, CI, and neighboring practice. Record
actual commands and applicable versions in [PLAN.md](../../../../codex-reports/PLAN.md).
Include formatting, linting, types, compilation, tests, supported configurations,
and artifact checks as applicable. An omitted category needs a reason, not a
fabricated pass. Use existing pinned tools and ordinary package managers.
Install missing required dependencies within authorization and rerun immediately.

For compiled projects, build the exact candidate before every commit, even when
only prose changes. For interpreted code, validate syntax/types and behavior.
For documents, inspect content, links, examples, and rendering when relevant.
Never add an unrelated application or run a bootstrap binary as evidence that
changed modules work.

## Run and inspect

Start with focused checks, then run the affected project's required gates.
Verify test discovery and selected counts, skipped cases, feature combinations,
and actual output. Exercise supported configurations without enabling mutually
exclusive features blindly. Run commands from the intended working directory.
A successful exit alone does not prove the intended behavior was exercised.

For regressions, reproduce the failure and confirm the corrected behavior.
Replicate required reference tests under [authoring-tests](../../authoring-tests/SKILL.md).
Preserve useful raw evidence and concise results in
[VALIDATION.md](../../../../codex-reports/VALIDATION.md).
Run [operational validation](../../operational-validation/SKILL.md) whenever a
partial is usable and before claiming final readiness.

## Measure performance

Measure every executable behavior change with representative inputs, including
relevant failures, before acceptance. Use optimized production-equivalent builds
where applicable. Record correctness, versions, environment, inputs, measurement
boundary, units, warmup, repetitions, distribution, and relevant resource use.
Compare the previous behavior or alternatives fairly when making comparative
claims. Separate startup, I/O, deliberate waits, and local processing costs.
Do not hide allocation, memory, throughput, or tail-latency regressions behind
an average. Pick metrics that match the actual deliverable and workload.

Install tools, repair the environment, and run the workload. Difficulty, cost
of effort, a missing dependency, or an unmeasured result is not an exception.
Only demonstrated literal impossibility after attempted remedies can justify
an explicit unavailable measurement; record evidence and keep any unsupported
claim out of acceptance. Decision scores follow the stricter rules in
[decision-matrix](../../decision-matrix/SKILL.md).
Prose-only changes have no runtime performance to measure.

## Review evidence

The primary inspects the final diff, outputs, and affected artifacts. Confirm
that evidence belongs to this candidate and exercises changed behavior. Resolve
known smells and review comments/tests before accepting. Repeat checks when a
new change, failure, or unresolved concern makes previous evidence insufficient;
do not rerun unrelated suites ceremonially after sufficient gates pass.
