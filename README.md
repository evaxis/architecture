![Evaxis logo](https://avatars.githubusercontent.com/u/349042465?v=4)

# Evaxis architecture

**Evidence Across Every Axis.**

Architectural records, roadmap, diagram sources, specifications and threat-model
planning for the independent, provider-neutral security evidence, provenance,
historical analysis and assurance platform.

**Confirmed:** foundation/design stage only. No product services, evidence
processing or storage exist here. Evaxis remains independent of Maester and
all individual technology providers.

| Area | Contents |
|---|---|
| [Architectural records](adr/README.md) | Decision process and confirmed foundation constraints |
| [Diagrams](diagrams/README.md) | Intended location of the original animated architecture artifact; source not supplied |
| [Specifications](specifications/README.md) | Planned Evidence Envelope work; no approved schemas |
| [Threat model](threat-model/README.md) | Preliminary boundaries and analysis questions, not a completed security assessment |
| [Roadmap](roadmap/README.md) | Evidence Envelope and conformance before implementation |
| [Repository governance](repository-governance.md) | Least-privilege GitHub baseline and sole-maintainer workflow |

**Proposed:** Maester integration via possible Packs and Cloud Plugins. Maester
is not Evaxis's execution or storage foundation. Provider APIs, evidence storage,
commercial licensing and revenue sharing are not established contracts.
No partnership, affiliation or endorsement is claimed.

**Undecided:** implementation language, build system, database, cloud, execution
model, detailed cryptographic/identity design and commercial licensing.
Public visibility does not mean licensed open source. No Evaxis licence has
been selected. [Third-party notices](THIRD_PARTY_NOTICES.md) apply to cARL assets.

See the [future core](https://github.com/evaxis/evaxis),
[shared contribution workflow](https://github.com/evaxis/.github/blob/main/CONTRIBUTING.md),
[code of conduct](https://github.com/evaxis/.github/blob/main/CODE_OF_CONDUCT.md)
and [private security reporting](SECURITY.md).
Canonical agent governance is under `.github/carl/`, not in generated adapters.
