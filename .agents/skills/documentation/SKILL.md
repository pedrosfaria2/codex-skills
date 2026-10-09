---
name: documentation
description: Write and review concise English documentation, reports, comments, and docstrings; remove redundant prose and explain only necessary current behavior and constraints.
---

# Concise documentation

Write simple, direct, objective English. Use the fewest words that preserve the
necessary contract, instructions, evidence, and limitations. Prefer a concrete
statement or short example over a long explanation. Avoid repetition across
files; link the source of truth. Keep current instructions separate from history.

## Comments and docstrings

Review every new or changed comment and every existing comment affected by a
change. Each must earn its place by explaining a necessary contract, unit,
invariant, subtle constraint, or current rationale that code alone cannot
express clearly. Improve names or structure before adding explanation.

Delete tautological, redundant, stale, and unnecessary comments. Comments explain
the code's actual behavior and constraints. Never describe what the code does
not do, advertise absent features, retain commented-out code, or narrate past
versions and changes. Version history belongs in Git and continuity reports.
Required public API documentation should state useful current contracts without
paraphrasing each line of implementation.

A comment explaining a maze is evidence to simplify the code. Tests needing a
long narrative should be rewritten into visible setup, action, and assertions.
Small helpers are useful when they reduce reading effort without hiding behavior.

## Review and verify

Read the final text from its audience's perspective. Remove filler, duplicated
rules, vague claims, and obsolete instructions. Check commands, examples, links,
file paths, and terminology against the current deliverable. Run or render
instructions where applicable; distinguish observed results from plans.

Keep reports compact but complete enough to resume: what changed, why, evidence,
remaining issues, and next action. Do not sacrifice correctness or hide a failed
check merely to shorten a report. Apply the normal acceptance workflow to
instruction and documentation changes too.
