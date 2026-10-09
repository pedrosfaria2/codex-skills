---
name: systematic-debugging
description: Investigate defects, test failures, and performance regressions by reproducing behavior, testing one hypothesis at a time, and verifying the cause before accepting a fix.
---

# Systematic debugging

1. Reproduce the failure. Capture inputs, environment, exact error, and the first
   incorrect state or output. Separate observations from assumptions. Reduce
   the reproducer while preserving the timing or ordering that matters.
2. Read the actual implementation, callers, contract, and tests. Compare a working
   path and relevant reference behavior. Consult official documentation for
   uncertain external contracts; research does not replace local reproduction.
3. State one hypothesis and the observation that would falsify it. Run a focused
   experiment. Avoid several speculative fixes at once, unexplained retries,
   swallowed errors, or changing expected values to make a test pass.
4. Fix the cause at its responsible boundary. Run the reproducer and relevant
   checks, remove unnecessary probes, and preserve a direct regression case
   under [authoring-tests](../authoring-tests/SKILL.md).
5. Review simplicity, code smells, comments, and measured performance through
   [project-workflow](../project-workflow/SKILL.md). Record cause, correction,
   evidence, limitations, and next action in
   [continuity](../../../codex-reports/CONTINUITY.md).

After three unsuccessful fix attempts, summarize the evidence and reconsider
the underlying assumptions before another patch. Continue authorized
investigation; ask only for genuinely missing information or a product choice.

Choose diagnostics from evidence: state tracing, resource monitoring, profilers,
concurrency or memory tools, and test-order isolation as applicable. Install
missing required tools and rerun; avoid a language-specific diagnostic framework
in a generic project. An environment claim needs a demonstrated dependency.

If a skill rule causes the problem, use [skill-issue](../skill-issue/SKILL.md).
Only the primary changes instructions; application workarounds do not repair an
unsuitable rule. Record unresolved findings under
[pending-issues](../pending-issues/SKILL.md).
