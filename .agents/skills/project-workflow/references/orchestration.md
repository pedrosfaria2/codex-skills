# Atomic orchestration

## Roles and work orders

The primary alone accepts or rejects work and edits shared workflow instructions.
Workers investigate, implement assigned files, and return evidence. Their success
report is not acceptance. A read-only independent review is useful for difficult
changes; the primary still inspects the final diff and runs required checks.

Use the lowest-cost available worker suited to a small task, with low reasoning
and a fresh context where supported. Record the chosen model in the work order;
do not assume a particular model name or tool exists. Give only necessary
context. Split difficult work before escalating; record evidence for any model
or reasoning escalation and return to the cheaper default afterward.

Each work order contains:

- Task ID, intended outcome, and accepted dependencies.
- Exact allowed files, exclusions, and read-only reference paths.
- Contracts, ownership, ordering, invariants, and relevant source/test paths.
- Required checks and measurement workload, with acceptance criteria.
- Handoff: changed files, reason, commands/results, findings, review evidence,
  and proposed plain commit title.

Keep concurrent edits disjoint. The primary integrates shared manifests,
lockfiles, registration, reports, and instructions serially. Never overwrite
another contributor's work. Do not create a branch or framework per task.
Use isolation only when overlap actually requires it. If delegation is unavailable,
record that fact and let the primary complete the same bounded work.

## Acceptance sequence

1. Read the final diff and affected callers against the assigned contract and
   consulted reference. Trace success, failure, cleanup, and integration.
2. Apply [code-smell review](../../code-smell-review/SKILL.md),
   [test review](../../authoring-tests/SKILL.md), and
   [documentation review](../../documentation/SKILL.md). Reject concrete defects,
   known smells, confusing tests, redundant comments, and unnecessary complexity.
3. Run [verification](verification.md) against the exact candidate, including a
   successful build before every commit when the project has a compilation step.
   Measure executable changes and exercise runnable deliverables. Inspect the
   outputs; a zero-test run or unrelated entry point proves nothing about the fix.
4. Return failed work with the specific correction and required evidence.
   A mandatory unrun or failed check prevents acceptance. Do not soften a check
   to clear a task or accumulate dependent work on an unaccepted foundation.
5. After gates pass, update the task entry, continuity, and validation evidence.
   Stage only that coherent task and its reports. Inspect the staged diff and
   whitespace. Confirm it is the candidate that passed; rerun affected checks
   after changes. Mark the task checked in the same atomic commit.
   Before committing, apply the blocking
   [security/dependency gate](../../security-dependency-review/SKILL.md) to the
   final staged content, including reports and commit text. Record redacted
   evidence; recheck after any content change. A missing or failed gate prevents
   commit. Before any dependency/tool install or update, its provenance gate
   must pass first; this applies throughout the task.
6. Commit immediately with a short descriptive title and task ID in the body.
   Do not use Conventional Commit prefixes. If the commit fails, leave the task
   unchecked, record the failure, and resolve it before dependent implementation.
7. Verify the local commit and remaining tree. Push to the configured current
   destination when authorized; verify the remote head. Do not force-push,
   rewrite history, alter identity, or include unrelated commits by surprise.
8. After every commit, apply [pending-issues](../../pending-issues/SKILL.md).
   Attempt actionable resolutions within scope. Preserve unresolved evidence
   and the next action in continuity. Fixes get their own coherent acceptance.
9. Preserve a concise handoff, then invoke the current session's native context
   compaction when available. Only the primary compacts its session. Resume
   from AGENTS, the plan, continuity, and relevant skills; continue the scope.

A checked task means reviewed, verified, and committed when Git is applicable.
For a user-requested deliverable outside version control, explicitly agree or
establish that boundary in the plan and record delivery evidence instead. Never
label an unsuccessful Git operation as an intentional non-Git workflow.

## Git and capability boundaries

Inspect Git before acting. Keep the current branch and preserve user changes.
Initialize Git when requested or already authorized. If Git is required but
unavailable, investigate and report the actual cause; do not bypass restricted
metadata with another repository. If the user requested files without version
control, deliver validated files and report that no commit exists.

A copied workflow is not blanket authorization to publish or deploy. Reuse
existing user authorization for commits and pushes; do not repeatedly request it.
If a remote is absent or publication is not authorized, record local-only status
and the actual boundary. Do not invent a remote. If an authorized required push
fails, resolve it before accumulating implementation commits; continue useful
independent investigation. Never claim an unpushed commit is published.

Native compaction is a session operation. Use only a mechanism actually exposed
for the current session. A summary, shell command, new session, or edited history
file is not compaction. If unavailable, record the limitation, retain the handoff,
and continue. Unavailable compaction alone is not a critical implementation block.

Record push and compaction outcomes in the next substantive handoff; do not
create an endless chain of bookkeeping commits to record their own hashes.

## Handoff and continuation

Include what changed, why, source paths read, decisions, actual checks and
measurements, open issues, Git/publication state, and the next eligible task.
Keep current status at the top of continuity and distinguish history from current
readiness. Essential evidence must live in durable files, not only chat or a
worker's report. Never record credentials or private tokens.

Continue through the user's requested scope. A reduced scope or stop instruction
overrides the old backlog. Stop only on completion, user direction, or a critical
blocker remaining after investigation that prevents all meaningful authorized
progress. Preserve an honest handoff before any interruption.
