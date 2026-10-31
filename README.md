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
| [Diagrams](diagrams/README.md) | Animated architecture and roadmap proposal, with local viewing instructions |
| [Specifications](specifications/README.md) | Proposed Evidence Envelope v0.1 semantics; pending review |
| [Maester compatibility research](research/maester-compatibility.md) | Pinned Pack/runtime findings and proposed adapter boundary; not an Evaxis foundation |
| [Threat model](threat-model/README.md) | Preliminary boundaries and analysis questions, not a completed security assessment |
| [Roadmap](roadmap/README.md) | Evidence Envelope and conformance before implementation |
| [Repository governance](repository-governance.md) | Least-privilege GitHub baseline and sole-maintainer workflow |

The [animated architecture and roadmap](diagrams/evaxis_architecture_roadmap_animated.html)
is an interactive design exploration, not a deployed site or an approved
implementation plan. GitHub displays its source; download it and open it in a
browser as described in the [diagram guide](diagrams/README.md).
Technology, API, encryption and commercial examples in the diagram remain
illustrative. [Confirmed foundation boundaries](adr/0001-foundation-boundaries.md)
and the [specification-first roadmap](roadmap/README.md) govern future decisions.

**Proposed:** Maester integration via possible Packs and Cloud Plugins. Maester
is not Evaxis's execution or storage foundation. Provider APIs, evidence storage,
commercial licensing and revenue sharing are not established contracts.
No partnership, affiliation or endorsement is claimed.
The [pinned compatibility research](research/maester-compatibility.md) confirms
the current native result boundary and is not an approval of an adapter.

**Undecided:** implementation language, build system, database, cloud, execution
model, detailed cryptographic/identity design and commercial licensing.
Public visibility does not mean licensed open source. No Evaxis licence has
been selected. [Third-party notices](THIRD_PARTY_NOTICES.md) apply to cARL assets.

See the [future core](https://github.com/evaxis/evaxis),
[shared contribution workflow](https://github.com/evaxis/.github/blob/main/CONTRIBUTING.md),
[code of conduct](https://github.com/evaxis/.github/blob/main/CODE_OF_CONDUCT.md)
and [private security reporting](SECURITY.md).
Canonical agent governance is under `.github/carl/`, not in generated adapters.
