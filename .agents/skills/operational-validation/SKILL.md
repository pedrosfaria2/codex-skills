---
name: operational-validation
description: Run and inspect usable partials and final deliverables in their actual supported environment; preserve real integration evidence and measurements before claiming completion.
---

# Operational validation

Use whenever a partial can be exercised and before final qualification.
A successful build or unit suite alone does not establish operational readiness.

1. Identify the intended user flow, prerequisites, observable outputs, failure
   behavior, and cleanup. Read the real entry points and run instructions.
2. Install and start dependencies required by the accepted design within scope.
   Use representative configuration and inputs. Do not add infrastructure just
   to simulate activity or hide a missing implementation.
3. Launch the actual deliverable. Interact with a GUI, invoke a CLI or service,
   execute a script, render a document, or inspect generated artifacts as
   applicable. Verify the result at the user's boundary, not only process liveness.
4. Exercise implemented external integrations against their real supported
   services when that is part of the contract and authorized. Label recorded
   fixtures and local substitutes accurately; neither proves a live integration.
   If unavailable, record attempts and leave that qualification incomplete.
5. Check relevant successful, invalid-input, failure, restart, and cleanup flows.
   Inspect outputs and state. Measure executable behavior under
   [verification](../project-workflow/references/verification.md).
6. Preserve commands, versions, configuration, timestamps, sanitized evidence,
   actual outcomes, limitations, and cleanup in
   [VALIDATION.md](../../../codex-reports/VALIDATION.md). Distinguish planned,
   attempted, observed, and accepted results.

Final qualification exercises all requested end-to-end flows on the final
candidate. Do not claim readiness while required flows or checks remain missing.
A blocked integration does not prevent independent authorized work.
Deployment, publication, destructive operations, and messaging still require
their applicable authorization; a local run is not permission for those actions.
