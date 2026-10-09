# Decision register

Status: no scored project choices. TASK-001 research is recorded below.
Use [decision-matrix](../.agents/skills/decision-matrix/SKILL.md) before selection.

## Entry structure

For each DEC ID, record:

1. Task, problem, requirements, constraints, and feasible alternatives.
2. Internet queries, access date, source links, versions, findings, and excluded
   alternatives. Record existing project facilities considered.
3. Criteria, equal weights, 1–5 scoring anchors, and comparison protocol frozen
   before results: inputs, correctness oracle, environment, and workload.
4. Commands, raw evidence, repetitions, measured results, and limitations.
5. A matrix with one row per criterion and one column per alternative, evidence
   for every score, and totals. Include simplicity, readability, performance,
   and specific tradeoffs. Inapplicable criteria need a common explicit basis.
6. Highest-total winner, or the primary's reasoned tie break, plus consequences
   and links to acceptance evidence. Missing scores never mean neutral points.

Scale: **1 very bad · 2 bad · 3 OK · 4 good · 5 very good**.
Preserve previous comparisons when revising a decision; state what changed.

## Matrix template

Copy into a DEC entry, name candidates, and add specific tradeoffs before
scoring. This unscored template records no selection.

| Criterion | Candidate A | Candidate B | Evidence / scoring anchor |
| --- | --- | --- | --- |
| Simplicity | Not evaluated | Not evaluated | Establish before scoring |
| Readability | Not evaluated | Not evaluated | Establish before scoring |
| Performance | Not measured | Not measured | Define workload and units |
| **Total** | Not calculated | Not calculated | Highest sum wins |

## Decisions

None yet. Add the first entry only after establishing an actual project choice.


## TASK-001 — Research for the requested security gate

The user fixed the scope: a blocking secrets/infrastructure review and dependency
provenance before installation. No new dependency, runtime architecture, or
scanner implementation is selected; no scored technology choice is being made.
Existing Git/search tools support the contextual review. A configured scanner
must also run; the instructions do not claim that a regex search proves safety.

Research performed 2026-10-08. Queries included
`site.github.com/gitleaks/gitleaks README git staged redact dir scan`,
`site:git-scm.com gitignore already tracked files`, and
`site:docs.github.com dependencies trusted publisher provenance not guarantee secure`.

- [Git ignore rules](https://git-scm.com/docs/gitignore): already tracked files
  require explicit review; ignoring a filename does not remove its staged data.
- [Git staged diff](https://git-scm.com/docs/git-diff): review the index rather
  than substituting the working-tree content.
- [Artifact attestations](https://docs.github.com/en/actions/concepts/security/artifact-attestations):
  verify artifact provenance with the ecosystem's supported evidence.
- [Gitleaks documentation](https://github.com/gitleaks/gitleaks/blob/master/README.md)
  and [TruffleHog documentation](https://github.com/trufflesecurity/trufflehog/blob/main/docs/man/trufflehog.1):
  established scanner approaches exist. Neither was installed or made a kit
  dependency. Use redacted/offline detection when scanners are configured.

These are protocol and tool references, not proof that any arbitrary package
is trustworthy. Each actual install/update requires current package-specific
provenance, integrity, and advisory evidence before execution.
