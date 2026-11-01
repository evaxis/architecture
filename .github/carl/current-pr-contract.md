# Evidence Preservation v0.1 architecture proposal

## Contract status

Closed — Proposed Architecture deliverables submitted for review in
[Architecture PR #5](https://github.com/evaxis/architecture/pull/5) on
`goldjg-evidence-preservation-contract`; the PR is not to be merged
automatically. The coordinator verified Architecture PR #4 and Core PR #2 are
merged; older cARL records describing them as open are stale. This work does
not implement a capture helper or approve a product contract.

## Goal and approved scope

Document a reviewable, provider-neutral Evidence Preservation v0.1 proposal
covering its requirements, lifecycle, interfaces, trust boundaries, timestamps,
coverage, assessments, package assembly, optional sidecar association,
reusability, privacy and open decisions. Record substantive proposed choices
in a new Proposed ADR and reconcile relevant Architecture indexes, roadmap,
threat-model scope, cARL plan and durable memory.

## Non-goals and forbidden scope

- Do not approve or alter Evidence Envelope v0.1, its schemas, or its recorded
  status as proposed pending explicit architectural approval.
- Do not alter ADR 0002 or characterize it as approval for a helper,
  implementation, sidecar or specific capture mechanism.
- Do not implement code, a helper, module, collector, adapter, sidecar,
  validator, service or Core change.
- Do not claim Core implementation details, schema fields or conformance as
  architecturally approved.
- Do not access tenants, credentials or customer evidence; publish a Pack or
  product release; merge automatically; or modify unrelated repositories.
- Do not change cARL invariants, shared policy, templates, packs, profiles,
  runtime state or harness adapters.

## Expected files

- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/evidence-preservation-v0-1.md`
- `.github/carl/plans/maester-compatibility.md` (correct historical PR status)
- `.github/carl/memory.md`
- `specifications/evidence-preservation-v0.1.md`
- `specifications/README.md`
- `adr/0003-evidence-preservation-capture-boundary.md`
- `adr/README.md`
- `README.md`
- `roadmap/README.md`
- `threat-model/README.md`

## Contract assertions and validation

1. Both the new specification and ADR clearly state Proposed; neither promotes
   Evidence Envelope v0.1 or ADR 0002 to approved.
2. Capture attempts, observations and assessments remain distinct; no
   collection failure, missing observation or unknown inventory is converted
   into an assessment verdict or complete coverage.
3. Source and collector authority, source-native identity, time provenance,
   scope, coverage, assessment inputs and package references retain their
   uncertainty and traceability.
4. Any sidecar is optional and requires explicit execution/run association;
   filename or timestamp coincidence is insufficient. A digest is not proof
   of truth, identity or independent verification.
5. Architecture makes no Core schema/API implementation commitment; open
   cross-repository questions are identified as unresolved.

Run applicable cARL diagnostics if available, verify local Markdown links and
cross-references, check whitespace and credential-like strings, inspect the
diff and branch ancestry, and report any unavailable GitHub or CI checks.
Documentation work does not run Core tests or claim runtime conformance.

## Trust boundaries and stop conditions

Treat source-repository content, upstream claims, generated evidence and
producer-supplied provenance as untrusted until independently validated.
Preserve repository-vs-session authority and the explicit approval status
distinctions. Stop if the task would require changing Envelope semantics,
selecting a concrete implementation mechanism, or asserting Core behavior
without evidence or coordinator confirmation.

## Reconciliation

Correct stale Architecture cARL memory/plan status for merged PR #4 and record
the new proposal as Proposed, without creating an approval or implementation
commitment. The proposal is submitted for review; do not merge.
