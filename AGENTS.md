# Codex project workflow

## Working contract

Follow the user's current scope and the actual repository. Read the relevant
implementation, callers, contracts, configuration, and tests before planning,
changing, debugging, or reviewing behavior. Record what was consulted. When
porting from a designated reference, preserve its required behavior and tests.
Treat reference repositories as read-only, including generated output and Git
metadata; run experiments in a separate copy.

**Deadly simple. Deadly fast.** Prefer clear ownership, direct composition,
small cohesive modules, existing tools, and explicit control flow. Rework code
that is hard to follow. Measure every executable behavior change, including
relevant failure paths, before acceptance. Prose has no runtime performance.

Use the skills below and read their SKILL.md before the matching work. Load only
needed supporting references. These rules also apply to scripts and test code.

| Work | Required skill |
| --- | --- |
| Plan, implement, delegate, review, accept, commit, or resume | [project-workflow](.agents/skills/project-workflow/SKILL.md) |
| Write or review tests | [authoring-tests](.agents/skills/authoring-tests/SKILL.md) |
| Investigate a failure or regression | [systematic-debugging](.agents/skills/systematic-debugging/SKILL.md) |
| Choose between alternatives | [decision-matrix](.agents/skills/decision-matrix/SKILL.md) |
| Before every commit or dependency/tool install/update | [security-dependency-review](.agents/skills/security-dependency-review/SKILL.md) |
| Review code before acceptance | [code-smell-review](.agents/skills/code-smell-review/SKILL.md) |
| Write or review prose, docstrings, or comments | [documentation](.agents/skills/documentation/SKILL.md) |
| Exercise a runnable partial or final deliverable | [operational-validation](.agents/skills/operational-validation/SKILL.md) |
| Resume, find an unresolved issue, or finish a commit | [pending-issues](.agents/skills/pending-issues/SKILL.md) |
| Resolve an unsuitable skill rule | [skill-issue](.agents/skills/skill-issue/SKILL.md) |

## Evidence and ownership

Keep all workflow reports in [codex-reports](codex-reports/PLAN.md).
Read [the plan](codex-reports/PLAN.md), [continuity](codex-reports/CONTINUITY.md),
and [pending issues](codex-reports/PENDING.md) when resuming. Maintain an accurate
current snapshot; label older results as history.

The primary Codex agent is the orchestrator and sole acceptance authority.
Only the primary edits project skills, supporting resources, metadata, and
routing instructions. Workers return evidence; they never accept, commit, push,
or compact the primary session. Use small, bounded tasks with disjoint ownership
and a low-cost available worker model. Escalate only for a demonstrated gap.

Use a researched, equal-weight decision matrix for each project choice. Search
the internet for alternatives before scoring, prefer primary documentation,
measure runtime performance, and select the highest sum. Only ties allow a
reasoned primary choice. Record evidence in
[DECISIONS.md](codex-reports/DECISIONS.md).

## Acceptance and continuation

Before accepting, inspect the final diff and affected integration yourself.
Resolve every identified code smell in the candidate. Review every changed or
affected comment and test for clarity; hard-to-follow code or tests need rework.
Run the actual formatter, linter, type checks, tests, and other applicable gates.
For compiled projects, build the exact candidate successfully before every
commit, including prose-only commits. For projects without a compilation step,
run their real applicable checks and record why a build is inapplicable.
Never create unrelated scaffolding to manufacture a passing build.

Before every installation or update, pass the provenance gate in
[security-dependency-review](.agents/skills/security-dependency-review/SKILL.md).
This prerequisite applies to every installation instruction in these skills,
including tools and temporary experiments. Unverified origin or unresolved
applicable security findings block installation.

Install required missing tools and dependencies through the appropriate existing
package manager within the user's authorization; respect pins and permissions.
Rerun the blocked check immediately. Record actual installation failures, not
an unattempted installation as a blocker. Permission limits require a concrete
request only when existing authorization and tools cannot resolve them.

Every commit requires a PASS from the secrets/private-infrastructure and
dependency gate on the exact staged candidate, including documentation and
reports. A failed, unresolved, or unrun required check blocks commit and affected
publication. Build/test success cannot substitute for this review.

Accept one coherent task at a time. When Git applies, include its checked plan
entry and handoff in an immediate atomic commit with a plain descriptive title.
For an explicitly established delivery outside Git, record validated files and
local-only status under orchestration instead. Push each accepted
commit to the configured destination when authorized, verify publication, review
pending issues, and invoke native session compaction when exposed. Do not invent
a remote, claim an unverified push, or equate a report with context compaction.
The detailed sequence and capability handling are in
[orchestration](.agents/skills/project-workflow/references/orchestration.md).

Continue until the requested scope is complete, the user stops or changes it,
or an investigated critical blocker prevents all meaningful authorized progress.
Do not end merely because a task, commit, push, or compaction finished. Keep
working on independent eligible tasks and preserve the next action. A checklist
or successful build alone does not establish a working final deliverable.
