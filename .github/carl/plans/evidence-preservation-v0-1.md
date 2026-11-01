# Evidence Preservation v0.1 architecture proposal

## Plan metadata
- PR / branch: Architecture PR to be opened / `goldjg-evidence-preservation-contract`
- Status: Active proposal; no implementation or approval
- Author: Copilot
- Created: 2026-11-01
- Last updated: 2026-11-01

## Task summary

Define an Architecture-owned, provider-neutral proposal for preserving source
evidence during collection and linking it to later assessments and Evidence
Envelope package assembly.

## Current repository context

The Evidence Envelope v0.1 document and Core schemas/fixtures are merged into
their default branches, but the human-semantic specification remains Proposed
pending explicit architectural approval. ADR 0002 is Proposed and defines a
mechanism-neutral Maester boundary; it is not helper or implementation
approval. Architecture PR #4 and Core PR #2 are verified merged; older
contract/plan statements to the contrary are stale.

This work produces architecture documentation only. Core implementation
details and schema semantics are not approved or changed by this plan.

## Previous contract status

The prior active contract covered Maester compatibility remediation and is
superseded by this scoped proposal. Its status references must be reconciled
with the verified merged PR state.

## Contract lifecycle note

The capture proposal and its ADR remain Proposed for review. They neither
approve Evidence Envelope v0.1 nor amend ADR 0002. Approval requires explicit
architectural review; implementation would require a separate scoped contract.

## Intentional contract amendments

Supersede the prior task's no-capture-mechanism decision boundary only for
documenting a proposed provider-neutral capture contract and conceptual
package lifecycle. Do not select or approve a helper, language, runtime,
framework, storage, transport or implementation.

## Goal

Document Evidence Preservation v0.1 requirements, capture lifecycle, interface
concepts, trust/timestamp/coverage semantics, assessment linkage, package
invariants, optional execution-associated sidecars, reuse beyond Maester,
privacy/threat implications, proposed decisions and unresolved questions.

## Non-goals

- Approving Evidence Envelope v0.1 or changing its semantics/schema.
- Implementing a helper, collector, module, Maester integration, sidecar,
  validator, Core change, service, database, queue, cloud or storage backend.
- Treating ADR 0002 or the current proposal as implementation authorization.
- Claiming complete coverage, source truth, immutability, authenticity or
  receiver verification from producer statements, filenames, timestamps or
  digests alone.
- Accessing tenants or credentials, publishing a Pack/release, or merging.

## Approved scope

- Add `specifications/evidence-preservation-v0.1.md`, explicitly Proposed.
- Add `adr/0003-evidence-preservation-capture-boundary.md`, explicitly
  Proposed, for the distinct provider-neutral capture boundary.
- Update Architecture README, specifications/ADR indexes, roadmap, preliminary
  threat-model scope and Architecture cARL memory.
- Supersede the current PR contract and correct the historical Maester plan's
  PR status; do not modify ADR 0002.
- Run documentation, governance and hygiene checks available in Architecture.
- Commit, push and open a review PR; do not merge.

## Forbidden scope

See `.github/carl/current-pr-contract.md`. In particular, do not change shared
cARL policy/invariants, Evidence Envelope v0.1, ADR 0002, or other repositories.

## Trust boundaries

Distinguish source authority and visibility, collector identity/authority,
framework assessment, package producer, and eventual receiver. Preserve the
provenance and uncertainty of each. A local file or producer assertion is not
an independent trust anchor.

## Invariants to preserve

- Evaxis remains provider-, execution- and storage-neutral.
- Observations, collection state and assessment conclusions remain separate.
- Source identity is authority/scope-qualified and based on provider-native
  identity, never display names alone.
- Unknown, partial, denied, failed, unsupported and not-attempted collection
  cannot silently become complete coverage or a control verdict.
- Producer claims do not become receiver-verified integrity/authenticity.
- No sensitive source data, customer evidence, tenant IDs or credentials enter
  public documentation or tests.
- Proposed status remains explicit.

## Expected files / directories

See the expected file list in `.github/carl/current-pr-contract.md`.

## Implementation phases

1. Specify the proposal and contract assertions.
2. Record the substantive proposed capture-boundary choice in ADR 0003.
3. Link the proposal, threat questions and roadmap without promoting it to an
   approved milestone.
4. Reconcile cARL memory and historical task status, validate, and submit PR.

## Acceptance criteria

1. Every requested architecture topic has an explicit, coherent treatment in
   the Proposed specification.
2. Run/attempt lifecycle has defined states and terminal/repeated completion
   behavior; completion cannot hide unresolved attempts.
3. Time authority, source-vs-capture time, clock uncertainty, scope and
   coverage semantics avoid unsupported precision or completeness claims.
4. Assessments reference exact evidence where available and may be
   assessment-only only when a legitimate declared input basis exists.
5. Optional sidecar association uses explicit run/execution binding; filename
   and timestamp coincidence are rejected as association evidence.

## Contract assertions

1. The capture proposal and ADR state Proposed; the Envelope proposal and ADR
   0002 remain unchanged and Proposed.
2. Unknown or partial collection and unavailable targets never imply a failed
   security control or complete inventory.
3. A collection attempt has explicit nonterminal and terminal states; a run
   cannot complete with unresolved attempts, and terminal attempts cannot be
   reopened.
4. Caller-provided source time remains attributed to its source and clock;
   automatically generated times describe actual capture events only.
5. Sidecar association proves linkage only to the declared execution/run
   context; digests, local files and producer claims do not prove truth,
   authenticity or receiver verification.

## Test strategy

This is documentation-only. Check all relative Markdown links, cross-reference
targets, status language, diff whitespace and credential-like strings.
Review the specification against Envelope v0.1 without editing it. Run cARL
diagnostics if the pinned CLI is present. Core schemas, executable tests,
tenant-connected behavior and Maester execution are out of scope and must not
be claimed as tested.

## Prompt ping-pong budget

One corrective prompt is acceptable. Two require reset and rehydration.

## Model fallback strategy

Preserve this proposal's scope, status, invariants and assertions. Treat any
conflict with current repository state as a stop-and-reconcile condition.

## Stop conditions

Stop if implementation, Envelope approval, cross-repository schema changes,
tenant access, credentials, publication or merge become necessary. Mark
mechanism, clock, coverage and assessment semantics unresolved rather than
guessing when existing architecture does not settle them.

## Context reset requirements

After PR creation, mark the contract closed as a proposal submitted for review,
not an approved capture contract. Preserve open decisions in the specification
and memory; a subsequent implementation requires a new contract.
