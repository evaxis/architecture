# PR #3: Evidence Envelope v0.1 architecture proposal

## Contract status

Active review-revision scope for https://github.com/evaxis/architecture/pull/3.
The user requests cross-PR corrections before merge; keep the PR open and the
specification proposed, not approved. Revise trust-claim authority, identity
continuity language, and comparison preconditions to align with core PR #1.

## Goal and approved scope

Clarify human-readable, provider-neutral Evidence Envelope v0.1 semantics in
`specifications/evidence-envelope-v0.1.md`: producer assertions versus
receiver-established verification; collection coverage/package invariants;
identity continuity limits; assessment input basis; and defensible comparison
preconditions. Keep the existing PR linked to core PR #1.

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
5. Consumers cannot turn producer-claimed verification/authentication into
   established trust; receiver results are separate derived records.
6. Distinct native IDs do not imply replacement; comparison conclusions list
   freshness, identity, scope, coverage, semantic and receiver-trust prerequisites.
7. Cross-links and authority/version alignment identify architecture as the
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

After the revision is pushed and PR checks verified, close this execution
contract as submitted for review, not as an approved specification. Carry
durable semantics into architecture memory; do not merge automatically.
