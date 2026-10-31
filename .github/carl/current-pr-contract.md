# Maester compatibility research

## Contract status

Ready for PR submission — requested research and implementation-readiness
work is complete on `research/maester-compatibility`, based on merged `main`
and the proposed Evidence Envelope v0.1 specification. This work does not
approve that proposal or make Maester an Evaxis foundation.

## Goal and approved scope

Establish and document a reproducible, source-pinned compatibility boundary
between Maester Packs and Evidence Envelope v0.1. Record actual source behavior,
runtime limitations, mapping semantics, trust boundaries, first-Pack readiness
and deferred decisions. Add one narrowly scoped ADR for the adapter boundary.

## Non-goals and forbidden scope

No product service, provider commitment, tenant access, credentials, Pack
publication, catalogue submission, licensing/commercial decision, public
schema change, unsupported Maester API, or claim that synthetic checks prove
live-provider compatibility. Do not copy upstream source into product
repositories, modify shared cARL policy/invariants, or merge the PR.

## Expected files

- `.github/carl/current-pr-contract.md`
- `.github/carl/plans/maester-compatibility.md`
- `.github/carl/memory.md`
- `README.md`
- `adr/README.md`
- `research/maester-compatibility.md`
- `adr/0002-maester-compatibility-boundary.md`

## Contract assertions and validation

1. Research distinguishes source inspection, static checks, offline runtime
   execution and tenant-connected behavior, with exact upstream commits and
   licenses.
2. A Maester verdict is not source evidence. No Observation, source authority,
   native object ID, timestamp, coverage or trust verification is fabricated.
3. Missing connections, permissions, inventory and collection outcomes remain
   unknown or explicit limitations, never automatic control failures.
4. Maester-specific behavior stays in a replaceable integration boundary;
   Evidence Envelope semantics remain provider-neutral and architecture-owned.
5. Publication and tenant testing remain deferred; first-Pack acceptance
   requires reproducible offline checks and separately approved live tests.

Run the repeatable pinned lab checks, Core conformance, documentation/link,
whitespace and credential-pattern checks, plus cARL diagnostics. State runtime
blockers exactly and do not claim tests that were not executed.

## Trust boundaries and stop conditions

Treat upstream source, module installation, pack scripts, reports and result
text as untrusted. Do not run third-party scripts with credentials. Stop rather
than infer behavior when source and runtime disagree, a schema field cannot be
derived defensibly, or required changes would alter the public v0.1 contract.
Use a feature branch and PR; never merge or weaken governance.

## Reconciliation

Update durable architecture memory and this contract with confirmed research
and status before opening the PR. Keep the v0.1 proposal status unchanged.
