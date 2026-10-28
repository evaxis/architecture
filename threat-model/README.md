# Initial threat-model scope

**Confirmed:** this is preliminary analysis scope, not a completed threat model,
security review, certification or implemented control set.

| Boundary / asset | Threat to investigate | Required design direction |
|---|---|---|
| Source and collector -> evidence | Forged identity, alteration, replay, stale or partial collection | Provenance, integrity, identity, timestamps, completeness, freshness and replay semantics |
| Evidence -> evaluator -> historical comparison | Environmental drift confused with schema, collection, identity-resolution or evaluation change | Preserve comparison context; define incomparable/incomplete outcomes |
| Customer/tenant -> execution and storage | Cross-customer disclosure, confused deputy, overprivileged adapters | Explicit authorization and isolation; provider-neutral contracts |
| Keys -> processing environment | Key disclosure, incorrect custody, shared-customer failure domain | Preserve client/server/hybrid choices; investigate per-customer keys and envelope encryption |
| Core -> Maester/provider integration | Implicit publisher trust, API/licence/entitlement coupling | Independent core; explicitly validated optional integration boundary |
| Contributor -> governance -> agent | Prompt injection, policy tampering, stale memory | Canonical cARL, scoped PR contracts, effective-pack hydration and review |
| Fork/PR -> CI -> GitHub administration | Secret exposure or privileged contributor-code execution | Read-only token, no secrets or self-administration workflow, no bypass |
| Private report -> public collaboration | Credentials, evidence or personal information disclosed | Private reporting and non-sensitive reproductions |

**Proposed:** model customer-controlled, hosted, hybrid and potential future
Maester Cloud runner environments without treating one as mandatory.
Key isolation and envelope encryption are preferred directions, not controls
that exist today.

The proposed [Evidence Envelope v0.1](../specifications/evidence-envelope-v0.1.md)
addresses evidence-specific threats: cross-tenant confusion, spoofed source or
collector identity, forged provenance, replay/staleness, malicious collector
output, sensitive metadata leakage, overcollection, ambiguous object
correlation, schema confusion, unsafe transformations and false historical
conclusions. It distinguishes integrity assertions from source truth,
authenticity, freshness and collection completeness. These are design
requirements, not implemented controls or a completed threat assessment.

**Undecided:** data classification, detailed adversary capabilities, key
custody, identity/authentication model, cryptographic algorithms, retention and
deletion obligations, authorization semantics, storage consistency and
residual risk acceptance. The proposal selects none of them.
