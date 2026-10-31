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

## Proposed decision

Keep any Maester adapter optional and outside provider-neutral Core
interfaces. Treat Maester output as an untrusted, versioned external
assessment record. Preserve its exact original representation or immutable
reference. Never infer Observations, source authority, target identity,
coverage, integrity verification or environmental completeness from a result
verdict, prose, progress event or Pack installation.

Do not implement an Evidence Envelope package adapter until the input can
provide a complete, defensible manifest and assessment subject/time. Where
source facts are emitted, require explicit source schema, authority, scope,
native ID, observation time and collection-health provenance. Keep any future
Maester-to-Evaxis importer distinct from a future Evaxis-to-Maester test
provider.

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

A supported, versioned Maester export plus an explicit Pack evidence contract
provides immutable source data/reference, source and tenant authority, native
object identity, collection attempts/coverage, run and observation times,
rule/evaluator versions and portable offline fixtures. Then review a separate
adapter implementation proposal and its threat/privacy controls.
