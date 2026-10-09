# Implementation plan

Status: TASK-001 accepted for the atomic commit after final checks. This repository delivers Codex instructions and
report structures. No application compilation or runtime workload applies.

## Project contract

Add the requested security skill for secrets, private infrastructure, environment
files, and dependency provenance. Integrate blocking checks before every commit
and before any installation/update. Keep the existing directory layout and
primary-only skill ownership. Exclude general security and migration workflows.
The user authorized this task, atomic commits, and pushes to the existing origin.

## Verification setup

| Gate | Command or applicability reason | Status |
| --- | --- | --- |
| Document diff/whitespace | `git diff --check` and primary final read | Passed |
| Skill schema/metadata | Codex skill-creator validator; names and UI fields | Passed |
| Local links | Resolve Markdown paths and anchors in the actual candidate | Passed |
| Ignore behavior | `git check-ignore --no-index` on synthetic filenames | Passed |
| Secret/infrastructure gate | Read exact staged changes; Git content searches and contextual review | Passed |
| Dependency provenance | No installation or dependency update in this task | Explicitly inapplicable |
| Build/runtime measurement | Markdown/YAML instructions; no application or executable helper changed | Inapplicable |
| Workflow scenarios | Independent review of blocking and permitted cases | Passed |
| Git destination | Existing origin/current branch; verify remote after push | Pending publication |
| Native compaction | No exposed current-session mechanism; handoff preserved | ISSUE-001 |

## Atomic task ledger

- [x] **TASK-001 — Block secret exposure and unverified dependency installs.**
  - Outcome: one focused security skill and mandatory routing throughout acceptance.
  - Allowed files: AGENTS, README, project-workflow skill/references, new security
    skill/metadata, .gitignore, and these reports.
  - Contract: no commit without a reviewed staged-candidate PASS; no install
    before trusted provenance, integrity, and applicable advisory review.
  - Checks: the verification setup above; primary accepts the actual final diff.
  - Delegation: low-cost worker, low reasoning, read-only integration/scenario
    review with bounded fresh context. Skill edits remain with the primary.

## Future tasks

Add stable task IDs with outcome, dependencies, allowed files, contracts,
checks, decision links, and evidence. Mark checked only under the acceptance
workflow. When reusing this kit, establish the destination's actual scope and
commands; these maintenance checks do not validate another project.
