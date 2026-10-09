---
name: authoring-tests
description: Write and review direct behavioral tests with independent expected results, low cognitive load, faithful reference coverage, and meaningful failure cases.
---

# Authoring tests

Read the actual contract, public interface, callers, nearby tests, and test
registration before writing a case. Follow
[project verification](../project-workflow/references/verification.md).

## Direct evidence

1. State the observable behavior and independent expected result. Use explicit
   values, contract examples, manually derived results, or trusted reference
   fixtures. Never calculate an expectation with the implementation under test
   or a copy of its algorithm.
2. Choose the smallest boundary that proves the behavior. Test real composition
   when the contract crosses components. Mock only external boundaries where
   needed; a test of a mock's configured response proves no application behavior.
3. Make arrange, act, and assert visible. Cover relevant success, boundary,
   failure, state, and cleanup effects. Check atomic failure leaves state intact
   when required; verify partial effects where the contract permits them.
4. Prefer a named case or a short table of explicit inputs and expected values.
   Do not branch on the production result, hide cases inside nested loops, or
   recreate business logic inside assertions. Generative tests need a simple,
   independent invariant and reproducible counterexamples.
5. Run the cases and confirm discovery and counts. For a regression, demonstrate
   failure before and success after the fix where practical. A disabled test,
   empty selection, incidental call count, or checked constant is not coverage.

## Low cognitive load is a gate

No tautological tests: reject self-comparisons, round trips used as the sole
oracle when both sides can share a bug, and assertions that merely restate setup.
Do not manufacture tests for prose edits or tests that mirror implementation
without checking a meaningful contract.

Helpers are welcome when they make the scenario easier to read. Give them one
clear purpose, explicit inputs, and visible effects. Avoid hidden assertions,
mutable globals, branching fixture builders, implicit timing, or helpers that
force readers to chase several layers to understand a case. Keep expected values
and important ordering beside the test. A test needing a long explanation or
substantial mental execution must be rewritten before acceptance.

Review test comments with [documentation](../documentation/SKILL.md). A clearer
name, explicit fixture, or shorter sequence usually replaces explanatory prose.

## Porting existing coverage

When porting behavior, find and read every corresponding reference test. Preserve
cases, fixtures, inputs, event order, expected values, assertions, tolerances,
and boundaries exactly; adapt only language and harness mechanics. Record the
source-to-destination mapping and run the ported cases. Extra cases supplement
rather than replace required coverage.

If a reference test conflicts with the intended contract, record the conflict
and obtain the primary's explicit resolution before accepting; never silently
soften or omit it. Keep reference repositories untouched. If no counterpart
exists, record the search and write independent behavioral coverage.

For external resources, concurrent work, or lifecycle behavior, also read
[integration testing](references/integration-testing.md).
