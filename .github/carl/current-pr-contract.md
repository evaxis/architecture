# PR #3: Evidence Envelope v0.1 architecture proposal

## Contract status

Active. The user authorized drafting the specification, fixtures/tooling across
both repositories, validation, commits, pushes and linked PR creation. This
repository's PR will publish a **proposal pending maintainer review**, not an
approved architectural decision. Do not merge it.

## Goal and approved scope

Define human-readable, provider-neutral Evidence Envelope v0.1 semantics and
record boundaries in `specifications/evidence-envelope-v0.1.md`; cross-link the
core schemas and fixtures, reconcile documentation and memory, validate, and
open a review PR.

## Non-goals and forbidden scope

No comparison engine, product implementation, cloud/runtime/provider,
implementation-language, storage/API, authentication, cryptographic algorithm,
key custody, encryption, retention, licensing, billing or Maester-specific
decision. Do not change CI, cARL runtime/packs/profiles/invariants/adapters,
branch protections, or claim implementation/approval.

## Plan and expected files

Follow `.github/carl/plans/pr3-evidence-envelope-v0-1.md`. Expected:
`.github/carl/current-pr-contract.md`, `.github/carl/plans/pr3-evidence-envelope-v0-1.md`,
`.github/carl/memory.md`, `README.md`, `specifications/README.md`,
`specifications/evidence-envelope-v0.1.md`, `threat-model/README.md`, and
`roadmap/README.md`.

## Contract assertions and validation

1. Observation, assessment, manifest and comparison boundaries are separate;
   missing/partial/stale/untrusted evidence does not become Pass, Fail,
   deletion or remediation.
2. Environmental, collection, schema/representation, identity, relationship,
   scope/coverage and evaluator/rule changes remain distinguishable.
3. Identity/correlation limitations and compatibility outcomes are explicit;
   transformations preserve original evidence and lineage.
4. Provenance, integrity, authenticity, freshness, replay and completeness
   claims state their limits; no unsupported cryptographic guarantee is made.
5. Cross-links and authority/version alignment identify architecture as the
   semantic source and core as schema/fixture source.

Run documentation/link, whitespace and credential-pattern checks; run cARL
diagnostics in both repositories. Report all behavior not actually tested by
documentation checks or the core fixture validator.

## Constraints and stop conditions

Preserve architecture `.github/carl/memory.md` and bundled governance. Label
the proposed specification as pending approval. Stop on conflicting policy,
unexpected worktree edits, protection failures or requests to select reserved
decisions. Use a feature branch and PR; never merge, bypass requirements or
alter protection settings.

## Carry-forward and reset

Once the PR is opened, close this execution contract as submitted for review,
not as an approved specification. Carry durable semantics into architecture
memory; later changes require a new scope. Do not merge automatically.
