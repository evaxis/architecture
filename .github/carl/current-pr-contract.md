# Initial architecture foundations contract

## Contract status

Closed for initial file preparation: local governance, links, workflow syntax
and credential-pattern validation passed. Publication and security-setting
verification remain bootstrap operations reported separately. This historical
contract does not authorise future product implementation.

## Goal and approved scope

Establish cARL-governed architectural records and planning, preserving all open
technical/commercial decisions. Tier 1 scoped writes and Tier 2 governance/API
writes are approved only for the three named Evaxis repositories.
No harness authority changes are approved.

## Plan and expected files

1. Inspect the workspace, remote state and documented cARL runtime.
2. Initialise cARL, select/activate foundations policy and populate memory.
3. Add `README.md`, `SECURITY.md`, `THIRD_PARTY_NOTICES.md`,
   `adr/`, `diagrams/`, `specifications/`, `threat-model/`, `roadmap/` documents,
   `.github/CODEOWNERS` and read-only governance CI.
4. Validate and push the initial commit; apply supported protections.
5. Verify remote state and report the missing original HTML explicitly.

## Non-goals and forbidden scope

No implementation, fictional schemas/findings/tests, language/cloud/database
choice, cryptographic implementation, licensing/commercial decision, hosted
services, paid resources, releases, other projects or new organisation members.
Do not recreate the missing HTML or logo, bypass reviews, enable auto-merge,
force-push, delete resources, weaken protections or publish secrets.

## Architectural and security constraints

Record every requested invariant in `memory.md` and architecture documents.
Clearly distinguish Confirmed, Proposed and Undecided. Keep Maester separate.
Keep cARL managed assets canonical; repository-specific policy lives in memory.
The original avatar URL is the sole graphic; no copied image asset is needed.

## Contract assertions and validation

1. Remote initial history/tree contains cARL and required architecture docs.
2. `carl doctor`, `status`, `pack effective`, `trace`, `harness status` pass;
   only core governance and CI/CD packs are effective.
3. Every invariant and undecided decision is documented; no fictional
   implementation or published-HTML claim exists.
4. Markdown targets, repository URLs and the canonical avatar resolve.
5. Staged whitespace/credential checks and real cARL CI pass; verify actual
   GitHub protections and report unsupported/blocked controls precisely.

## Risks, stop conditions and escalation

Stop an operation if permissions/policy block it or existing work conflicts.
Escalate any reserved decision, lockout risk or broader scope.
With one maintainer, require PRs without impossible self-approval; do not grant
an automation bypass or weaken controls to make checks succeed.

## Carry-forward and context reset

Only stable memory/invariants survive the bootstrap scope. Later changes use a
feature branch, a fresh contract and a PR. Close this contract after preparation
and local validation; it is historical evidence, not future execution authority.
