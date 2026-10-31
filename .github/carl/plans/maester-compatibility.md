# Maester compatibility research plan

## Plan metadata
- PR / branch: not opened / `research/maester-compatibility`
- Status: Ready for PR submission
- Purpose: Record verified Maester Pack compatibility and the provider-neutral Evidence Envelope v0.1 boundary.
- Created: 2026-10-28
- Last updated: 2026-10-31

## Status and scope

User-requested research branch from merged `main`; the Evidence Envelope v0.1
specification remains a proposal. Research the official Maester runtime and
three Packs at immutable commits. Deliver an architecture research record and
an ADR on the provider-specific adapter boundary. No tenant, secrets,
publication, catalogue submission, product-stack selection, schema amendment,
or merge.

## Purpose

Document source-verified Maester lifecycle/results, establish the v0.1
provenance boundary, and record first-Pack readiness and reviewable decisions.

## Goal

Complete the static and offline evidence record, validate Core conformance and
cARL governance, then submit an unmerged Architecture PR linked to the Core
compatibility PR.

## Affected files

- `research/maester-compatibility.md`
- `adr/0002-maester-compatibility-boundary.md`
- `README.md`, `adr/README.md`, `.github/carl/memory.md`
- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/maester-compatibility.md`

## Steps

1. Review pinned source and manifests for runtime, Pack lifecycle, security,
   permissions, dependencies and result data structures.
2. Exercise only reviewed synthetic tests and structural checks offline.
3. Record mapping gaps and the decision not to fabricate missing v0.1 facts.
4. Run repeatable lab checks, Core conformance and cARL diagnostics.
5. Commit and push this branch, then open a linked PR without merging.

## Test strategy

- Repeat `pwsh -NoProfile -File ~/git/evaxis-upstream-lab/scripts/verify-maester.ps1`.
- Run Core `python3 tools/validate_conformance.py`.
- Run cARL doctor/status/effective/trace/harness and plan checks.
- Check whitespace, documentation claims, and added content for secrets.

## Risks

No live tenant, connector success, Graph test, publication flow, or adapter
package mapping is tested. Source-level support must not be presented as
runtime-verified, and v0.1 proposal semantics remain pending approval.

## cARL/docs reconciliation

Research updates architecture memory and user-facing docs because the confirmed
result/trust boundary is durable. Close the active contract only after PR
submission; do not amend invariants or weaken governance.

## Acceptance assertions

1. Record owner, default branch, SHA, license, runtime/Pwsh requirements,
   services, permissions, modules, network destinations, and verification mode
   for each upstream reference.
2. Distinguish Pack install, structural validation, discovery, execution,
   source collection, assessment and coverage.
3. Map only fields Maester actually exposes; retain execution health,
   assessment claims, source observations and receiver trust as separate facts.
4. Keep Maester-specific concepts in an optional, replaceable adapter, not in
   neutral Evaxis Core or its normative schemas.
5. Identify offline versus external-infrastructure prerequisites and defer
   production-tenant testing and Pack publication.

## Work and validation

- Inspect merged architecture/Core contracts and effective cARL policy.
- Pin official repositories outside product source trees and inspect code,
  manifests, tests and docs.
- Attempt dependency-isolated offline runtime execution; record exact blocker.
- Document mapping, losses, privacy/security considerations, acceptance tests
  and deferred directions.
- Run cARL diagnostics, documentation/whitespace/secret checks and Core
  conformance validator; open a separate PR.

Do not treat static validation as runtime evidence or synthetic results as
provider compatibility.
