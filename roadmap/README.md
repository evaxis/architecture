# Initial roadmap

**Confirmed current stage:** organisation/repository foundations, governance and
architectural documentation. No production service or product release exists.

The [animated architecture and roadmap proposal](../diagrams/evaxis_architecture_roadmap_animated.html)
explores possible later integrations, deployments and commercial stages.
See [viewing instructions and decision status](../diagrams/README.md).
Its phase labels are illustrative, not approved milestones: this roadmap keeps
the Evidence Envelope and synthetic conformance fixtures first. Named storage,
identity, encryption and commercial options do not select technologies or terms.

| Order | Proposed milestone | Exit evidence |
|---|---|---|
| 1 | Review the proposed Evidence Envelope v0.1 and linked Core schemas/fixtures | Explicit architectural approval; aligned semantics, versioned schemas, synthetic expected results and recorded open decisions |
| 2 | Review the separate Evidence Preservation v0.1 capture proposal | Explicit decision on capture semantics, with unresolved cross-repository questions addressed; no implementation authorization implied |
| 3 | Refine observation, assessment, manifest and capture contracts if review identifies gaps | Reviewed relationships, incomplete/incomparable outcomes and schema/evaluator compatibility |
| 4 | Historical comparison semantics and threat-model refinement | Distinction between environmental, collection, schema, identity-resolution and evaluator change |
| 5 | Evaluate portable execution/storage/cryptographic options | Documented alternatives and approved ADRs, without mandatory provider or paid-service coupling |
| 6 | Consider optional Maester integrations and commercial model | Explicit provider/API/licensing/entitlement decisions, only after investigation |

The Evidence Envelope and Evidence Preservation proposals exist for review;
neither completes its review milestone or approves normative semantics.
Licensing and contribution rights must be resolved before substantial
implementation. No language, build system, database, cloud, delivery date,
hosted offering or commercial arrangement is committed.
Cloud infrastructure deployment is not the next milestone.
