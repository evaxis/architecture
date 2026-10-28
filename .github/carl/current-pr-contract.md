# PR #1: Animated architecture documentation reconciliation

## Contract status

Closed after local validation. The owner explicitly requested documentation/file
updates and a commit on the existing `goldjg-patch-1` branch for PR #1.
Publication and remote CI verification follow; do not merge this PR.

## Goal and approved scope

Reconcile the supplied animated HTML with current documentation and canonical
cARL memory without promoting illustrative options into accepted architecture.
Tier 1 documentation writes and Tier 2 scoped governance/PR-branch publication
are authorised by the request.

## Plan and expected files

1. Inspect the uploaded HTML, resource references, scripts and current policy.
2. Update `README.md`, `diagrams/README.md`, `roadmap/README.md` and
   `.github/carl/memory.md` to reference the actual artifact and explain how to
   view it locally without deployment.
3. In `diagrams/evaxis_architecture_roadmap_animated.html`, replace the embedded
   logo with the canonical avatar URL and clarify proposal/decision status,
   unresolved source claims and the specification-first milestone.
4. Validate governance, links, HTML references, script syntax and branding;
   close this contract, commit and push to the existing PR branch.
5. Update the PR description and verify remote commit/check results.

## Constraints and non-goals

Preserve all memory invariants and bundled managed cARL files. The HTML is a
design exploration, not implementation, approved API/crypto/storage/licensing
contracts, provider endorsement or a hosted site. Preserve its interactions.
No new product implementation, dependencies, infrastructure, releases, provider
choices, licence terms, review bypass, auto-merge or changes to other repos.

## Contract assertions and validation

1. The actual HTML path is linked from the repository, diagram and roadmap
   documentation; local Markdown targets exist and stale missing-source claims
   are removed.
2. The diagram uses the existing avatar URL, without embedded replacement
   artwork; its proposal banner preserves undecided technology/commercial
   status and the Evidence Envelope/conformance next milestone.
3. Inspect resource URLs and browser scripts; check JavaScript syntax, unique
   DOM IDs and navigation/dialog targets. No new active external dependencies.
   Report browser execution limitations rather than claiming visual validation.
4. Run pinned cARL 1.0.2 doctor, status, effective packs, trace and harness
   status; run whitespace and credential-pattern checks.
5. Push only the PR branch, verify the remote commit and real governance CI;
   do not merge or modify repository protections.

## Stop conditions and escalation

Stop on conflicting worktree/remote edits, protection failures or requests to
select reserved technical/commercial decisions. Do not repair managed runtime
assets or expand this PR into product design/implementation.

## Carry-forward and reset

Record only durable artifact location, viewing instructions and proposal
authority in memory. Close this contract after validation; future work requires
new scoped approval. The previous bootstrap contract is superseded.

## Validation evidence and limitations

Pinned cARL 1.0.2 diagnostics pass with the unchanged foundations effective
pack set and five synced adapters. Markdown/HTML local targets, seven tab
targets, 39 interactive-node metadata records and unique IDs pass checks.
Both inline scripts pass `node --check`; the canonical avatar is the only
external resource and no embedded image remains. Credential-pattern and
whitespace checks pass. No browser engine is installed, so visual rendering
and native browser interaction checks were not run. No dependencies were added.
