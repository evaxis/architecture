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
| 1 | Evaxis Evidence Envelope specification and conformance fixtures | Reviewed semantics for provenance, identity, time, completeness, freshness, replay and version context; approved synthetic fixtures and assertions |
| 2 | Observation, assessment and manifest contracts | Reviewed relationships, incomplete/incomparable outcomes and schema/evaluator compatibility |
| 3 | Historical comparison semantics and threat-model refinement | Distinction between environmental, collection, schema, identity-resolution and evaluator change |
| 4 | Evaluate portable execution/storage/cryptographic options | Documented alternatives and approved ADRs, without mandatory provider or paid-service coupling |
| 5 | Consider optional Maester integrations and commercial model | Explicit provider/API/licensing/entitlement decisions, only after investigation |

Licensing and contribution rights must be resolved before substantial
implementation. No language, build system, database, cloud, delivery date,
hosted offering or commercial arrangement is committed.
Cloud infrastructure deployment is not the next milestone.
