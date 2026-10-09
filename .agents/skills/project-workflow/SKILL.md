---
name: project-workflow
description: Plan, implement, delegate, review, and accept project work with atomic commits, measured verification, and durable continuity; use when starting or resuming a task.
---

# Project workflow

Read [AGENTS.md](../../../AGENTS.md), [the plan](../../../codex-reports/PLAN.md),
[continuity](../../../codex-reports/CONTINUITY.md), and
[pending issues](../../../codex-reports/PENDING.md).
Use [orchestration](references/orchestration.md) for task ownership and acceptance,
and [verification](references/verification.md) to establish actual checks.

Before every commit and before installing or updating dependencies/tools, apply
[security-dependency-review](../security-dependency-review/SKILL.md). Verify
provenance before execution; inspect the exact staged candidate before commit.

## Understand and plan

1. Inspect the tree, manifests, scripts, CI, configuration, and current Git state.
   Read the affected implementation, callers, and tests. Do not assume a tool,
   module, service, language, or command exists because a skill mentions it.
2. Establish the requested outcome and observable acceptance criteria. Preserve
   requirements; implementation order must not silently reduce scope.
3. Break work into atomic task IDs with accepted dependencies, allowed files,
   contracts, checks, and measurable completion. Keep a coherent fix together.
   Resolve choices through [decision-matrix](../decision-matrix/SKILL.md).
4. Reuse existing project conventions and maintained libraries when they fit.
   Prefer the smallest direct design that meets the actual contract. Do not
   build speculative extension points, parallel frameworks, or infrastructure.
5. Implement and validate one task at a time. Delegate bounded work under
   orchestration. Update the handoff while working, including rejected evidence
   only when it prevents repeating a mistake.

## Design and review

Use domain names, explicit ownership, and narrow interfaces. Put validation at
responsible boundaries. Keep state transitions and side effects visible; handle
failure and resource cleanup deliberately. Avoid duplicated state, unnecessary
branches, forwarding layers, copies, allocations, locks, and task or queue hops.
Select relevant resource limits from requirements or measurements rather than
arbitrary constants. Do not remove necessary correctness checks for speed.

Before acceptance, apply [code-smell-review](../code-smell-review/SKILL.md),
[documentation](../documentation/SKILL.md), and
[authoring-tests](../authoring-tests/SKILL.md) where relevant. Run and interact
with available deliverables under
[operational-validation](../operational-validation/SKILL.md).
The primary reviews its own work by the same standard as a worker's delivery.
