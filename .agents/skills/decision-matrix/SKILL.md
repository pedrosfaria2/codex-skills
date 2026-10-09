---
name: decision-matrix
description: Research alternatives on the internet and select project choices with equal-weight evidence-backed matrices, measured runtime performance, and primary-only tie breaks.
---

# Researched decision matrices

Use before each project choice between alternatives, including dependencies,
architecture, algorithms, tools, data representation, UI, and delivery layout.
An explicit user requirement is a constraint, not an option to vote away.
Record matrices in [DECISIONS.md](../../../codex-reports/DECISIONS.md).

1. State the task ID, problem, requirements, and current constraints. Inspect
   existing project solutions first.
2. **Search the internet for alternatives before selecting or scoring.** Prefer
   official documentation, upstream repositories, and primary research. Include
   existing facilities and maintained libraries where feasible. Record queries,
   access dates, versions, links, findings, and rejected infeasible alternatives.
   Do not substitute recollection or marketing for research. If access fails,
   attempt available remedies and record the exact limitation; keep a decision
   requiring that missing evidence open.
3. Freeze criteria, scoring anchors, and comparison workload before results.
   Include simplicity, readability, measured performance, and relevant concrete
   tradeoffs. Avoid redundant criteria that multiply one preference.
4. Use equal weights: **1 very bad, 2 bad, 3 OK, 4 good, 5 very good**. Support
   every score. Compare equivalent correct outcomes with matched inputs,
   environment, resource budgets, and measurement boundaries. Record versions,
   commands, warmup, repetitions, units, raw results, and limitations.
5. Never give neutral points to unmeasured performance. Install tools and run
   representative experiments, including relevant failure paths. Difficulty or
   an absent dependency does not excuse measurement. Only demonstrated literal
   impossibility after attempted remedies permits an explicit exception; never
   invent a score. Record how that exception affects the ability to decide.
6. Sum the applicable criteria. **The highest total always wins.** Only a tie
   permits the primary to choose, with a stated reason. Do not change criteria,
   weights, thresholds, workloads, or implementation quality after results to
   force a winner. New evidence can justify a separately recorded comparison
   that treats every affected candidate consistently.
7. Record winner, totals, evidence, limitations, and consequences. Link the
   decision from its task and handoff. A matrix never replaces correctness,
   review, verification, or actual operational use.

For a pure prose or file-organization decision, runtime performance may have no
meaning. Explain this and mark it N/A for every candidate, excluding it equally
from totals. This is not an exception for executable choices. If runtime
performance exists but literally cannot be measured, record attempted remedies
and keep selection open until the primary establishes an explicit, justified
basis for proceeding; do not present an incomplete score as a measured winner.
