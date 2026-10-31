# ADR 0002: Maester is an optional assessment import boundary

- **Status:** Proposed
- **Date:** 2026-10-28
- **Context:** Research against Maester `b8ad89557a831d3d3d7c369174300701243af8a6`
  and the synthetic demo Pack at
  `3f83cc8b674ac7c195f4611473e21bec6c50e8f3`.
- **Decision authority:** This ADR is a proposal for review, not an approved
  amendment to Evidence Envelope v0.1.

## Context

Maester 3 exposes Pack-native assessment results and stable test/family row
identities. It does not turn a verdict into source data. Standard rows lack
source payloads and source schema/timestamps; `Invoke-MtTest` rows lack
run-level identity and time. Result subjects and coverage are not uniformly
available. Some Pack outputs can include object names, permissions, report
HTML, tenant context and error text.

## Proposed decision boundary

Evaxis may accept Maester-derived evidence when independently sufficient
provenance is preserved by a supported capture mechanism. This proposal
approves only that architectural boundary for review; it does not approve or
select a concrete adapter, capture mechanism, interface, or implementation.
Maester remains optional to Evaxis, and Core's evidence contract remains
provider-neutral.

Any future capture mechanism must preserve evidence at a legitimate source
collection boundary, before relevant provenance is lost. Alternatives for
future evaluation include:

1. A reusable helper invoked within a Maester Pack.
2. An instrumented provider/source collector.
3. A structured evidence sidecar associated with a specific Maester execution.
4. A supported native Maester export containing equivalent provenance.

These are alternatives, not requirements or implementation decisions. Do not
require Pack authors to modify every test unnecessarily or reinvent
Evaxis-specific evidence plumbing for each Pack. Do not mandate a sidecar,
helper library, PowerShell module, storage backend, transport, or Maester
export change.

The capture boundary and any later adapter must preserve these properties:

- Source identity is qualified by authority and scope; source observations
  have defensible collection timestamps.
- Run identity, source attempts, and coverage are explicit. Missing evidence
  or collection failure is not automatically an assessment failure.
- Source observations remain distinct from evaluation outcomes. A wrapper
  cannot reconstruct missing provenance from ordinary Pass/Fail rows.
- Original source evidence or durable references are preserved according to
  the evidence contract. Producer claims do not become receiver-verified trust.
- The wrapper's own security and identity claims require independent
  validation.
- Privacy, least privilege, source attribution, and version compatibility are
  preserved.

Any future Maester-to-Evaxis importer remains distinct from a future
Evaxis-to-Maester test provider. Standard Maester result rows remain
insufficient wherever required provenance is absent; do not fabricate
Observations, authority, target identity, timestamps, coverage, integrity
verification, or environmental completeness from a verdict, prose, progress
event, or Pack installation.

## Consequences

- Evaxis does not adopt Maester's result schema, test engine, connector model,
  Pack catalogue or Microsoft dependencies as its evidence foundation.
- Current offline Pack authoring, structural validation, discovery and
  synthetic execution are reproducible without tenant credentials.
- A first source-connected Pack needs an explicit evidence contract beyond
  native result rows and must not report full coverage from test count.
- Existing v0.1 schemas remain unchanged. Inability to populate a required
  field is a reject/unknown boundary, not an invitation to add placeholder
  identities or timestamps.
- Result details and attachments need data minimization, access control,
  retention and tenant-identifier review before any storage design.

## Alternatives considered

1. Treat Maester Pass/Fail as Observation: rejected because a test conclusion
   is not source-reported configuration.
2. Manufacture a tenant target, run ID, source attempt or timestamp from test
   names/display text/duration: rejected because those facts are not
   defensibly available in every supported result path.
3. Make Maester the foundational evidence model: rejected because this would
   couple neutral evidence semantics to one runtime and provider ecosystem.

## Revisit when

Source inspection or controlled offline evidence shows that any one of the
candidate mechanisms—or another supported mechanism—can preserve the
contract-required source/run/attempt/coverage provenance before it is lost,
with portable versioned references and independently reviewable security,
identity, privacy, least-privilege, and compatibility properties. Native
Maester export changes are not a prerequisite when another supported capture
boundary provides equivalent provenance. Then review the proposed boundary
and a separate adapter implementation proposal; do not treat this ADR as
approval to build one.
