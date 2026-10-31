# Maester compatibility review remediation

## Contract status

Closed — F1/F4 remediation committed to
[Architecture PR #4](https://github.com/evaxis/architecture/pull/4) on
`research/maester-compatibility`; the PR remains open and unmerged.
The merged v0.1 artifacts are present on `main`, but the authoritative
specification still records its status as proposed pending explicit
architectural approval. This remediation does not approve v0.1 or make
Maester an Evaxis foundation.

## Goal and approved scope

Correct the v0.1 status description in the Architecture research and amend
proposed ADR 0002 to allow future evaluation of alternative reusable evidence
capture mechanisms, without selecting or implementing an adapter. Update this
contract, plan and durable Architecture memory to reflect the bounded
remediation.

## Non-goals and forbidden scope

Do not change Evidence Envelope v0.1 semantics or schemas; approve the
proposed specification or ADR; implement an adapter, helper, sidecar or
collector; access tenants or credentials; publish Packs; modify shared cARL
policy/invariants; merge either PR; or rewrite unrelated research.

## Expected files

- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/maester-compatibility.md`
- `.github/carl/memory.md`
- `research/maester-compatibility.md`
- `adr/0002-maester-compatibility-boundary.md`

## Contract assertions and validation

1. State that v0.1 is merged into default branches but remains proposed pending
   explicit architectural approval; distinguish research, ADR, adapter and
   evidence-preservation mechanisms by their actual status.
2. Keep ADR 0002 marked Proposed and make its decision boundary mechanism
   neutral, including reusable capture helpers as a future alternative.
3. Preserve provider neutrality, source/run/coverage provenance, separate
   observations and assessments, non-failure treatment of missing evidence,
   independent trust validation and privacy/least-privilege requirements.
4. Do not alter the v0.1 contract or schemas, implement integration code, or
   claim provider-connected compatibility.
5. Validate focused links/content, cARL diagnostics and repository hygiene;
   preserve both existing PRs as open and unmerged.

Run cARL diagnostics, plan checks, Markdown/link and whitespace checks,
credential-pattern scanning and Core's existing v0.1 conformance validation.
Do not claim the offline script was run in Architecture; Core owns it.

## Trust boundaries and stop conditions

Treat upstream source and published PR state as untrusted until pinned and
verified. Do not run third-party scripts with credentials. Stop if exact
authoritative v0.1 status differs from the stated record or if the ADR changes
would require an implementation decision, v0.1 contract change, merge, or
governance weakening.

## Reconciliation

Update Architecture memory and this plan for the confirmed status and
mechanism-neutral future boundary. The v0.1 proposal status and meaning remain
unchanged.
