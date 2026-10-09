# Pending issues

Reviewed for TASK-001. No unresolved secret/provenance finding blocks this task.

| ID | Status | Finding and impact | Next action |
| --- | --- | --- | --- |
| ISSUE-001 | Session capability unavailable | No exposed native control can compact the current session; durable handoff preserved | Recheck capabilities after each commit; use native compaction when exposed |

## ISSUE-001

The primary inspected the session's tool catalog. No current-session compaction
mechanism is exposed. Writing this report is not compaction. This does not block
instruction work or publication; no compaction is claimed.

## Future findings

Use stable issue IDs with task/owner, first observation, latest review, impact,
actual attempted remedies/results, next action, and closure evidence. Never
copy secrets or private endpoints into this ledger. A pending entry cannot waive
a failed security gate. Review every open item after each commit and mirror
continuity impact in [CONTINUITY.md](CONTINUITY.md).
