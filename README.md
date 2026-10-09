# Reusable Codex workflow

Copy `AGENTS.md`, `.agents/skills/`, and `codex-reports/` into a project root.
Merge existing instructions and reports; preserve existing work. Include the
hidden `.agents` directory when copying. This README describes the kit itself.

The kit covers planning, delegation, implementation, tests, debugging, decisions,
review, documentation, operational validation, pending issues, and handoff.
It selects no application stack. All reports start uninitialized, ready for the
first task; they contain no invented checks or completed work.

Before implementation, Codex inspects the destination and records actual
commands, tool versions, scope, and Git capabilities in
[the plan](codex-reports/PLAN.md). Add project-specific contracts to `AGENTS.md`.
Keep workflow rules in the linked skills instead of duplicating them.

[AGENTS.md](AGENTS.md) routes all nine skills.
[Continuity](codex-reports/CONTINUITY.md) is the resume entry point;
[decisions](codex-reports/DECISIONS.md), [pending issues](codex-reports/PENDING.md),
and [validation](codex-reports/VALIDATION.md) retain the evidence.

Codex documents repository skills under `.agents/skills/`, with `SKILL.md` and
optional `agents/openai.yaml` metadata. Same-named skills from other locations
remain separate entries; reconcile existing instructions when installing.
See [official skills documentation](https://learn.chatgpt.com/docs/build-skills)
and [AGENTS discovery](https://learn.chatgpt.com/docs/agent-configuration/agents-md).
If newly copied skills do not appear, restart Codex and verify its discovery
paths. Copying this kit does not verify a running session's skill registration.
