---
name: security-dependency-review
description: Block every commit until secrets, environment files, and private infrastructure exposure are reviewed; verify dependency and tool provenance before any installation or update.
---

# Secrets and dependency provenance

Use before every commit, including documentation and report commits, and before
installing or updating any dependency or tool. This is a blocking workflow gate.
The primary owns acceptance; workers return redacted evidence.

## Before installing or updating

Check provenance before the first install, build script, package lifecycle hook,
or execution of downloaded code. This applies to application dependencies,
transitive changes, development tools, system packages, plugins, containers,
CI actions, and temporary experiments. An instruction to install missing tools
always means: verify first, install second, then rerun the required check.

1. Establish the exact package identity, version, publisher, official upstream,
   and distribution channel using current primary sources. Cross-check the
   upstream's installation documentation against the registry or package source.
   Check suspicious names, lookalikes, ownership changes, and unexpected sources.
   Inspect registry metadata and proposed dependency graphs as data before
   installing packages. Resolve and review new transitive entries without
   executing their lifecycle/build hooks; accept manifest/lockfile updates only
   after that review passes.
2. Verify the selected artifact through the ecosystem's supported integrity and
   provenance mechanisms: authenticated package metadata, checksums from a
   trusted channel, signatures or attestations where available. A checksum from
   the same unverified download location does not establish a trusted publisher.
3. Review current advisories, upstream security notices, maintenance, installation
   scripts, and relevant transitive changes. Use existing ecosystem audit tools;
   check their provenance too. Registry presence, popularity, stars, HTTPS, or
   an empty advisory result alone is insufficient evidence of trust.
4. Record package/version, upstream and registry links, access date, integrity
   evidence, advisory results, and why the source is trusted. Pin the reviewed
   version or artifact and preserve the project's lockfile conventions. Recheck
   when the source, version, publisher, install behavior, or evidence changes.
5. Install only after the evidence establishes a trusted origin and resolves
   security findings affecting the intended use. If provenance, integrity, or
   required advisory checks cannot be verified, stop the installation. Investigate
   or choose a verified alternative through the decision workflow. Do not run
   arbitrary installers, pipe downloaded scripts into a shell, disable integrity
   checks, or install first and audit afterward.

State exactly what was verified. No dependency can be guaranteed free of future
vulnerabilities; uncertainty about its current origin or an unresolved applicable
security finding is a blocker, not a claim that it is safe.

## What must stay out of commits

- Credentials, passwords, tokens, private keys, signing material, session cookies,
  authenticated URLs, connection strings with credentials, and secret-bearing
  dumps, logs, screenshots, fixtures, reports, or generated artifacts.
- Real server/database IPs, deployment hostnames, internal domains, private service
  URLs, and infrastructure identifiers, even when reachable from the internet.
  Inject these through local configuration or secret management. Merely removing
  a password does not sanitize a private endpoint.
- Actual `.env` files and environment-specific variants. A reviewed `.env.example`
  may contain empty values or obvious placeholders and loopback defaults only.
  A filename ending in `example` does not make its contents safe.

`localhost`, `127.0.0.1`, and `::1` are acceptable local defaults, with no real
credentials. Wildcard binds and arbitrary non-loopback IPs are not localhost
exceptions. Prefer placeholders over realistic invented infrastructure addresses.
Public documentation links and official public vendor/package endpoints may
remain when their public purpose is verified; this does not permit publishing
an organization's deployment endpoints.

Keep local environment files ignored. Check tracked files explicitly:
`.gitignore` does not remove files already tracked and is not a security gate.
Never force-add a sensitive file. Preserve the user's local configuration while
removing it from a candidate when necessary.

## Blocking pre-commit review

1. Review `git status --short`, `git diff --cached --name-status`, and
   `git diff --cached --no-ext-diff`. Inspect the full staged content of every
   added or changed file, not just its working-tree copy. Include hidden files,
   reports, fixtures, and generated output. Read the exact proposed commit
   title/body before invoking Git. Review tracked filenames for environment
   files, keys, dumps, and other sensitive artifacts.
2. Search the staged candidate for credential material, IPs, private/internal
   hostnames, infrastructure identifiers, URLs, and connection strings. Run the
   project's configured secret scanner when present,
   with redacted output and offline detection; never test suspected credentials
   against a live service. Use existing Git/search tools for contextual review
   where no scanner is configured. Record the method, scope, and limitations;
   never claim a heuristic search alone proves the absence of secrets.
3. Inspect each finding without copying sensitive values into chat or durable
   reports. Classify safe placeholders, loopback defaults, verified public
   endpoints, and actual exposure by context. No blanket path exclusion,
   generic allowlist, baseline, or pending entry may waive a real exposure.
   Inspect non-text artifacts appropriately; unreadable content cannot silently
   pass. An unresolved finding or unavailable required check blocks the commit.
4. Verify dependency review evidence for every install/update in this task and
   every changed manifest, lockfile, source, or installation script. Include
   transitive changes. If none changed and nothing was installed, record that
   applicability explicitly instead of inventing an audit result.
5. Record PASS or BLOCKED, reviewed files, commands/tool versions, redacted
   findings and resolutions, dependency evidence, and remaining limitations in
   the existing validation/handoff report. Review that report too. Confirm the
   staged candidate still matches the reviewed content immediately before commit;
   any subsequent content change invalidates its pass and requires rechecking.

**No commit without this gate passing.** Documentation-only changes, urgency,
a previously clean scan, and passing build/tests do not waive it. Do not bypass
a configured check with `--no-verify`. A procedural gate is a primary-agent
obligation; do not claim that a Git hook or CI enforcement exists unless installed
and exercised. Apply the same review to outgoing commits before pushing.

If an exposure is discovered in existing history, stop the affected publication,
report only its location/type, and coordinate credential rotation and cleanup
within authorization. A deletion in the latest tree does not erase history.
Do not rewrite history, rotate credentials, or delete user files silently.

Follow [AGENTS.md](../../../AGENTS.md) and
[orchestration](../project-workflow/references/orchestration.md).
