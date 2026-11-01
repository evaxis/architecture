# Specifications

## Evaxis Evidence Envelope v0.1

[Evidence Envelope v0.1](evidence-envelope-v0.1.md) is a proposed human-readable
semantic contract, pending maintainer review and explicit architectural
approval. It defines separate envelope, collection manifest, observation and
assessment records; identity/provenance limits; completeness and freshness;
compatibility outcomes; and rules for distinguishing environmental from
collection, schema, identity, relationship and evaluator changes.

The proposal selects no product language, cloud, API, storage, execution model,
cryptographic algorithm/key custody, encryption, retention default, licence,
billing or Maester integration. It is not evidence that a runtime or comparison
engine exists.

## Evidence Preservation v0.1

[Evidence Preservation v0.1](evidence-preservation-v0.1.md) is a separate
**Proposed** capture-boundary document. It describes collection attempts,
observations, time provenance, coverage, assessment linkage, package
consistency and optional sidecar association without selecting an
implementation. It does not approve or amend Evidence Envelope v0.1 or ADR
0002. Its decision proposal is recorded separately in [ADR 0003](../adr/0003-evidence-preservation-capture-boundary.md),
which is also Proposed.

The [core repository schemas and synthetic fixtures](https://github.com/evaxis/evaxis/tree/main/schemas)
own machine-readable record structure and expected conformance results. This
architecture document owns human semantics. The two repositories align using
the explicit contract version `0.1`; a meaning-changing update requires
corresponding reviewed updates in both.
