---
name: pending-issues
description: Track unresolved findings, attempt actionable resolutions, and review the pending ledger when resuming and after every commit without weakening acceptance gates.
---

# Pending issues

Read [PENDING.md](../../../codex-reports/PENDING.md) and
[CONTINUITY.md](../../../codex-reports/CONTINUITY.md) when resuming, whenever a
finding remains unresolved, and after every commit. The primary owns the ledger
and closure; workers provide evidence.

Use stable issue IDs. Record the affected task, observed problem, impact, owner,
first observation, latest review, attempted remedies and exact results, next
possible action, and evidence required to close. Distinguish untried work from a
failed attempt. Keep the implementation backlog in the plan; list concrete
findings here instead of duplicating every future task or hypothetical risk.

After each commit, review every open item. Attempt actionable remedies within
the current authorized scope, install missing required tools, and rerun checks.
Do not reopen application implementation after the user restricts work to a
different scope. For items outside scope, record that boundary and the next
eligible action; it does not waive a defect blocking the current candidate.

Close only after the primary verifies the resolution. Link the resolving task
and evidence; preserve useful history. Failed mandatory checks and known smells
keep affected tasks unaccepted even if documented here. An actual external
blocker needs a condition for retry and its impact in continuity.

Avoid endless unchanged bookkeeping commits. A substantive fix or new finding
gets a coherent report update with its task under
[orchestration](../project-workflow/references/orchestration.md). Then preserve
the handoff for native compaction and continue the requested scope.
