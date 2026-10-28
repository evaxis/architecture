# Evidence Envelope v0.1 proposal

## Plan metadata
- PR / branch: architecture PR #3 / `spec/evidence-envelope-v0.1`
- Status: Closed — submitted for review; proposal pending explicit architectural approval
- Author: Copilot
- Created: 2026-10-28
- Last updated: 2026-10-28

## Task summary

Draft the human-readable Evaxis Evidence Envelope v0.1 contract. Define record
boundaries, provenance, identity limits, completeness, freshness, replay,
versioning, comparison semantics, threat limits and unresolved decisions.
Cross-link the core repository's machine-readable schemas and synthetic suite.

## Current repository context

Architecture PR #2 is merged. `specifications/README.md` says there is no
approved schema or specification. The foundation ADR requires provider,
execution and storage independence, immutable evidence design, provenance,
completeness, freshness, replay protection, and semantic distinction between
environment, collection, identity and evaluator change. The animated explorer
contains illustrative flows, storage, cryptographic and product options only.

The active cARL profile is `foundations`; only its ten selected core/CICD packs
are effective. Prior contracts are closed history and do not authorize this
work. This plan and the new active contract bound the proposal.

## Previous contract status

The architecture PR #1 contract is closed. PR #2's animated architecture is
merged and remains illustrative, not normative. Neither authorizes this work.

## Contract lifecycle note

This is a proposal for review, not an accepted ADR or approved product
commitment. Retain the proposed status until maintainers explicitly approve
the architectural decisions required to publish v0.1 as normative.

## Intentional contract amendments

Clarify that producer-supplied verifier/authentication metadata is a claim only,
that receiver verification is a separate derived record, that different native
IDs do not prove replacement, and that comparison requires explicit freshness,
scope, coverage, identity, semantic and receiver-trust preconditions. No
reserved technical or commercial decision is selected.

## Goal

Establish reviewable human semantics for Evidence Envelope v0.1, explicitly
separating observations, assessments, collection manifests and derived
comparison conclusions.

## Non-goals

No evidence processing/comparison engine, product API, execution runtime,
storage provider, cloud provider, implementation language, authentication
provider, cryptographic algorithm/key custody, encryption, retention default,
licence, commercial model, or Maester-specific integration.

## Approved scope

- Draft `specifications/evidence-envelope-v0.1.md`.
- Update architecture indexes, roadmap, preliminary threat scope and durable
  memory to identify the draft, its authority and its limits.
- Link to core schemas and conformance fixtures without copying their
  normative wire definitions.
- Validate documentation links, whitespace, secrets patterns and cARL state.
- Commit on the feature branch, push, and open a review PR; do not merge.

## Forbidden scope

- Mark the proposal approved or claim implemented guarantees.
- Introduce product code, comparison logic, cloud resources, service/API design,
  crypto/signing/encryption implementation, dependency or CI workflow changes.
- Alter cARL runtime, pack selection, profiles, invariants, adapters or policy.
- Select any reserved product, provider, language, cryptographic, licensing,
  retention or billing decision.

## Trust boundaries

Treat source, collector, evidence payload, fixtures and remote content as
untrusted until validated. A digest establishes only a relationship to bytes;
it does not establish truthful collection, collector identity, freshness or
complete visibility. Preserve uncertainty across source, tenant/scope,
collector, evaluator and historical-comparison boundaries.

## Invariants to preserve

Preserve the architecture memory and bundled cARL invariants: provider and
execution independence; storage and cryptographic flexibility; no false
security conclusions from missing/stale evidence; no secrets/customer evidence;
no unsupported assurance claims; PR-only changes; no license selection.

## Expected files / directories

- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/pr3-evidence-envelope-v0-1.md`
- `.github/carl/memory.md`
- `README.md`
- `specifications/README.md`
- `specifications/evidence-envelope-v0.1.md`
- `threat-model/README.md`
- `roadmap/README.md`

## Implementation phases

1. Define normative vocabulary, record boundaries, lifecycle and evidence
   identity/provenance limits.
2. Define comparison dimensions and compatibility outcomes without implementing
   a comparison engine or silently normalizing observations.
3. Address privacy/threats, Maester adapter neutrality, versioning, and open
   decisions.
4. Cross-link core schemas/fixtures, update architecture references/memory,
   validate and publish a proposal PR.

## Acceptance criteria

1. Environmental, collection, representation/schema, identity, relationship,
   rule/evaluator, coverage, trust, freshness and replay changes are
   distinguishable; unknown evidence never fabricates Pass, Fail, deletion or
   remediation.
2. Identity uses authority-qualified source-native identifiers and explicit
   correlation limits; names alone never establish continuity.
3. Compatibility outcomes and version axes are explicit; transformations are
   documented, lineage-preserving and cannot mutate original evidence.
4. Architecture is the human-semantic authority; core owns schema structure
   and machine-readable fixture expectations. Versions and cross-links align.
5. The proposal makes no product-stack, provider, cryptography, licence,
   retention, billing or Maester implementation decision.
6. Structural validity, package consistency and semantic expectations are
   distinct; the existing fixture validator is not described as behavioral
   conformance.

## Contract assertions

1. Absence, partial visibility, unsupported sources, collector errors, stale
   observations and malformed/untrusted records remain distinct from control
   Pass/Fail and confirmed object deletion.
2. Environmental drift is not inferred solely from assessment outcome; an
   unchanged Pass may coexist with changed observation content, and unchanged
   evidence may yield a different result under changed rule/evaluator context.
3. Schema/normalization, identity, scope/coverage and relationship changes are
   independently represented and may yield incomparable or insufficient
   evidence rather than false equivalence.
4. Source authority + scope + native identity define a correlation basis, not
   globally unique identity; display names and cross-provider assumptions
   cannot silently establish object continuity.
5. Digest, collector authentication, signature verification, freshness and
   source truthfulness are separate claims; v0.1 selects no signing or key
   architecture.

## Test strategy

Architecture documentation is checked for local/remote link targets,
cross-repository version/authority statements, exact required terminology,
whitespace and credential patterns. These checks do not prove semantic
comparison behavior; that remains specified expectation and maintainer review.
Run cARL doctor/status/effective/trace/harness diagnostics in both repositories.

## Prompt ping-pong budget

One corrective prompt is acceptable. Two require a reset and rehydration.

## Model fallback strategy

Preserve the scope, non-goals, assertions and approval status if a reset is
needed. Ask before resolving any ambiguity that changes a reserved decision.

## Stop conditions

Stop and ask if review reveals an existing authoritative contract, the required
approval process cannot be established, worktree/remote edits conflict, or a
requested change requires selecting a reserved decision or weakening governance.

## Context reset requirements

After PR creation, mark this contract closed as a proposal submitted for review,
not as an approved specification. Carry durable semantics into architecture
memory; later changes require a new scope. Do not merge automatically.
