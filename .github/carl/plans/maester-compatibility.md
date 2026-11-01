# Maester compatibility review remediation plan

## Plan metadata
- PR / branch: [Architecture PR #4](https://github.com/evaxis/architecture/pull/4) / `research/maester-compatibility`
- Status: Historical — PR #4 merged; this remediation plan is closed
- Purpose: Correct status language and keep proposed ADR 0002 open to future, mechanism-neutral evidence-preservation approaches.
- Created: 2026-10-28
- Last updated: 2026-11-02

## Status and scope

The remediation addressed Architecture findings F1 and F4 on the former PR
branch. PR #4 is merged. The v0.1 specification and schemas are merged to their
respective default branches but the authoritative semantic document remains
explicitly proposed pending architectural approval. No tenant, secrets,
publication, catalogue submission, adapter implementation, or schema amendment
was part of that remediation.

## Goal

Correct the research's v0.1 status wording and revise ADR 0002 so a future
reusable evidence-preservation wrapper/helper is an alternative to native
Maester export changes. Approve only the abstract boundary, not an adapter or
capture mechanism.

## Affected files

- `research/maester-compatibility.md`
- `adr/0002-maester-compatibility-boundary.md`
- `.github/carl/memory.md`
- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/maester-compatibility.md`

## Required principles

- Maester remains optional and Core evidence semantics provider-neutral.
- Avoid requiring each Pack author to reinvent evidence plumbing.
- Qualify source identity by authority and scope; state defensible collection
  timestamps, run identity, source attempts and coverage explicitly.
- Keep observations distinct from evaluations; missing/failed collection does
  not automatically mean an assessment failure.
- A wrapper cannot reconstruct missing provenance from ordinary result rows.
- Preserve original evidence or durable references; producer claims are not
  receiver-verified trust.
- Independently validate a wrapper's security and identity claims.
- Preserve privacy, least privilege, source attribution and version compatibility.
- Do not select or mandate a helper, module, sidecar, collector, backend,
  transport, native export change or adapter.

## Validation and stop conditions

Verify authoritative specification status, ADR is still marked Proposed,
no v0.1 semantics/schemas change, claims match the existing research, cARL
diagnostics and plan validation pass, and both PRs remain open/unmerged. Stop
if a proposed edit implies approval of the v0.1 contract or concrete
implementation.
