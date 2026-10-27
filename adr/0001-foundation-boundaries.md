# 0001: Foundation boundaries

**Status: Confirmed constraints.** These decisions constrain future design;
they are not claims of implemented capabilities.

## Context

Evaxis (EVidence + AXIS) is an independent, provider-neutral security evidence,
provenance, historical analysis and assurance platform in the foundation/design
stage. Its tagline is **Evidence Across Every Axis.**

## Confirmed decisions

1. **Core independence.** Evaxis remains independent of Maester, Microsoft,
   Netlify, Cloudflare, Azure and every other individual technology provider.
2. **Execution independence.** Assessment and comparison must not depend on one
   fixed execution environment. Customer-controlled runners, hosted processing,
   hybrid processing and future Maester Cloud runners remain potential options,
   not selected dependencies.
3. **Storage portability.** Permit interchangeable implementations, including
   local and customer-managed storage. No backend provider is selected.
4. **Cryptographic flexibility.** Preserve client-side, server-side and hybrid
   processing options. No cryptographic implementation or algorithm is selected.
5. **Evidence integrity.** Design for immutable evidence, provenance, source and
   collector identity, collection timestamps, completeness, freshness and replay
   protection. Define validation and failure semantics before claiming assurance.
6. **Semantic correctness.** Separate real environmental drift from changes to
   schema, collection, identity resolution and evaluation. Missing or stale
   evidence must not imply compliance or a confirmed environmental change.
7. **Commercial independence.** Useful baseline functionality should remain
   accessible without requiring a hosted paid service. Premium entitlements must
   not become inseparably coupled to a storage provider.
8. **Maester separation.** Maester is an intended integration, not Evaxis's
   execution or storage foundation. No provider API, structured evidence
   storage, commercial licence or revenue-sharing arrangement is established.
9. **Governed development.** Each repository uses canonical cARL governance from
   its first commit. Subsequent content changes use PRs. Do not weaken
   protection settings, bypass reviews or select reserved decisions implicitly.
10. **Canonical branding.** Reference the existing organisation avatar at
    `https://avatars.githubusercontent.com/u/349042465?v=4`; do not recreate,
    substitute or duplicate the logo.

## Proposed directions

Per-customer key isolation and envelope encryption are preferred design
directions, not completed security controls. Maester Packs and Maester Cloud
Plugins are integration opportunities only.

## Undecided

Implementation languages, build system, providers, database/storage technology,
execution topology, identity model, key custody/rotation, cryptographic details,
schemas, licensing, contribution rights, premium entitlements, integration APIs
and commercial/revenue-sharing terms need separate investigation and approval.
Public repositories are not a declaration of open-source licensing. Avoid
substantial implementation before licensing is decided.

## Alternatives and consequences

A provider-specific or Maester-dependent foundation would constrain storage,
execution and commercial portability, so it is outside these boundaries.
No particular portable implementation is selected instead.
Implementation must wait for reviewed contracts; portability and assurance
claims require actual conformance evidence, not diagrams or intent alone.

## Validation direction

The next milestone is the Evidence Envelope specification and approved
synthetic conformance fixtures. Record source/collector identity, time,
completeness and evaluator context before implementing comparison.
Keep cARL memory consistent with any reviewed architectural amendment.
