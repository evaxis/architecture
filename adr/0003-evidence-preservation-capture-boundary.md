# ADR 0003: Preserve source evidence at an explicit capture boundary

- **Status:** Proposed
- **Date:** 2026-11-01
- **Decision authority:** Proposal for review only. This ADR does not approve
  Evidence Envelope v0.1, a helper, adapter, sidecar, implementation, or
  operational deployment.
- **Related:** [Evidence Preservation v0.1 proposal](../specifications/evidence-preservation-v0.1.md);
  [Proposed ADR 0002](0002-maester-compatibility-boundary.md).

## Context

Assessment frameworks can retain conclusions while omitting the source facts,
collection attempts, subject identity, timestamps and coverage needed to
account for how those conclusions were produced. Reconstructing missing
provenance from a verdict or display text would fabricate facts. The
architecture needs a reusable description of capture requirements that does
not bind the common evidence model to Maester or any particular collector
implementation.

The Evidence Envelope v0.1 specification and Core schemas are present in
their repositories, but the human-semantic specification remains Proposed
pending explicit architectural approval. This ADR is separate from Envelope
approval and does not change it.

## Proposed decision

Define a provider- and framework-neutral capture boundary that preserves run
context, source attempts, source observations, target identity, time
provenance, coverage limitations and optional assessment links as distinct
facts. Assessment results MUST NOT be used to manufacture missing source
observations, identity, source time or complete coverage.

Treat any framework sidecar as optional. If used, require explicit run and
execution association; filename or timestamp coincidence is insufficient.
Treat digests as byte-consistency metadata, not proof of producer identity,
truth, authenticity or receiver verification.

This records a proposed architectural choice, not approval to implement it.
ADR 0002 remains Proposed and unchanged; it does not approve the helper
implementation or select any capture mechanism.

## Alternatives considered

1. **Use framework assessment rows as source observations.** Rejected because
   a conclusion does not establish what the source returned, its native
   identity, observation time or collection coverage.
2. **Make Maester the common capture contract.** Rejected because it would
   couple neutral evidence semantics to one optional assessment framework.
3. **Mandate a helper or execution-associated sidecar.** Deferred; the
   appropriate implementation boundary and association mechanism are
   unvalidated and require separate review.
4. **Leave capture semantics implicit in each integration.** Rejected as a
   proposal because it invites inconsistent provenance and lossy mappings;
   implementation architecture remains open.

## Consequences

- Reusable semantic requirements can be evaluated across Maester and
  independent collectors without embedding framework-specific types in the
  common contract.
- Capture and assessment remain independent; missing collection cannot be
  interpreted as a failed control.
- Source identity, clock authority, expected inventory, assessment input
  declarations and run-level health aggregation remain open where the
  evidence contract does not settle them.
- No specific API, module, language, file format, backend, transport,
  atomicity mechanism or security control is selected.
- Envelope/schema conformance, package consistency, observed source truth and
  receiver verification remain distinct claims.

## Trust boundaries

The source controls what can be observed; the collector controls how and when
it is read; an evaluator controls how inputs become conclusions; the producer
controls package claims; and the receiver controls independent verification.
Each boundary can be incomplete or compromised. Preserve attribution and
uncertainty across them. Never treat a producer's digest, timestamp or
verification assertion as receiver-established assurance.

## Validation and revisit

Review against the separately Proposed Evidence Envelope semantics and Core
schemas without implying either is approved. Before implementation, define
contract assertions, supported state transitions, identifier/reference
constraints, clock assumptions, coverage semantics, privacy controls and
sidecar association tests in a new scoped implementation contract.

Revisit when maintainers explicitly decide whether to approve this semantic
boundary and when cross-repository review determines which concepts fit the
current Envelope version. Do not merge this proposal as evidence of approval.
