# Evidence Preservation v0.1

**Status: Proposed — this document is a design proposal, not an approved
contract or implementation authorization.** It does not approve or amend
[Evidence Envelope v0.1](evidence-envelope-v0.1.md), whose human-semantic
specification remains Proposed pending explicit architectural approval.
[ADR 0002](../adr/0002-maester-compatibility-boundary.md) remains Proposed and
is unchanged; it does not approve a helper or implementation. This proposal's
distinct capture-boundary decision is recorded in
[ADR 0003](../adr/0003-evidence-preservation-capture-boundary.md), also
Proposed.

This is an Architecture-owned semantic proposal. It defines requirements and
conceptual behavior for preserving source and collection facts before an
assessment framework may discard them. It defines no Core wire schema, API,
PowerShell module, Maester integration, storage, transport, or runtime.

## 1. Purpose and scope

Evidence preservation accounts for what a collector tried to observe, what it
actually observed, what it could not observe, and how any later assessment
used the resulting evidence. These are separate facts:

1. **Collection** describes source attempts, access/visibility limits,
   observations and coverage.
2. **Assessment** describes an evaluator's conclusion against declared inputs.
3. **Package assembly** groups related records and checks internal references
   without elevating producer assertions into independently verified truth.

The capture model is provider- and assessment-framework-neutral. Maester is
one potential consumer/integration, not a required dependency or the source of
the common abstraction. Reuse should permit independent collectors and future
assessment systems without copying source-specific assumptions into a shared
contract.

This proposal specifies requirements, not a claim that the behavior exists.
Evidence Envelope v0.1 remains a separate proposed package contract. Its
semantic and machine-readable conformance must be reviewed independently.

## 2. Normative vocabulary and status

The words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** express
requirements of this proposed contract only. They are not active normative
requirements until this proposal is explicitly approved.

- **Run:** one bounded capture execution with a unique run identity and
  collector context.
- **Source:** an authority and scope boundary from which facts may be read.
- **Attempt:** one declared operation against a source and intended scope.
- **Target:** an authority-qualified, provider-native subject identity.
- **Observation:** source-reported or directly captured data, distinct from an
  evaluator's conclusion.
- **Assessment:** an evaluator's conclusion about a declared subject and input
  basis.
- **Coverage:** the relationship among expected, observed, not-observed and
  unknown target sets, bounded by the declared scope and inventory knowledge.
- **Capture time:** a time at which the collector performed a capture event.
- **Source time:** a time reported by the source as describing the observed
  fact; it is not interchangeable with capture time.

## 3. Run context and source attempts

A run record SHOULD identify: a unique run ID; capture contract version;
collector authority, identity and version; requested scope; actual start and
completion times; and optional execution-framework context. Source
configuration version or digest MAY be included only when legitimately
available and its meaning is stated. Framework context supplements rather
than replaces collector and source provenance.

Each declared source SHOULD identify source authority, intended scope,
attempted operation and any known permission/visibility boundary. An attempt
records start and terminal times, an explicit outcome, limitations, and
non-sensitive error classifications sufficient for diagnosis. Avoid embedding
raw error payloads or source data in diagnostic text.

Attempts distinguish at least:

- `pending` — declared but not yet begun;
- `in_progress` — collection began and has not reached a terminal outcome;
- `succeeded` — the declared operation completed successfully for its
  explicitly bounded scope;
- `partial` — some results were obtained but known gaps remain;
- `unavailable` — source or required service could not be reached;
- `denied` — authorization or visibility was insufficient;
- `unsupported` — the operation is not supported by this collector/source;
- `failed` — the attempt terminated with an operational error;
- `not_attempted` — explicitly not run, with reason.

These are collection outcomes, not assessment outcomes. `succeeded` applies
only to the declared operation and scope; it does not imply full inventory or
absence of unobserved targets. A run MUST NOT complete with in-progress
attempts. A terminal attempt MUST NOT be silently reopened. Completion of a
terminal run is idempotent only if the repeated request makes no changes;
attempting to change its facts MUST fail explicitly. Invalid state transitions
MUST be rejected.

## 4. Capture lifecycle and conceptual interface

The following operation sequence is illustrative and provider-neutral, not a
required public API:

1. Begin a run with required collector identity, contract version and scope.
2. Declare source authority and requested scope.
3. Begin an attempt and record its actual capture start.
4. Record each observation with source, target, type/schema and time
   provenance; preserve source representation or a durable reference.
5. Record known unavailable, denied, unsupported or otherwise not-observed
   targets and their reasons independently of observations.
6. Complete the attempt with a terminal outcome and actual completion time.
7. Optionally record assessments with explicit subject, evaluator and input
   references.
8. Complete the run after every declared attempt is terminal.
9. Assemble a package and validate its schema and cross-record consistency.

An observation MUST identify one run and source, have a unique observation ID
within its declared identifier scope, and reference a stable target identity.
IDs MUST NOT be silently reused to overwrite earlier facts. A capture boundary
MUST fail explicitly when required context is absent or an observation is
attached to a different run. Package assembly MUST resolve required
references, detect duplicate IDs and reject contradictions rather than
repairing or inventing facts.

This lifecycle does not mandate persistence during collection, atomic file
formats, or a specific helper design. Any implementation that materializes a
package MUST define its own atomicity and recovery behavior in a separately
approved implementation contract.

## 5. Target identity and source observations

Target identity MUST be qualified by source authority and source scope (for
example, a tenant or account boundary), include a stable provider-native
identifier where available, and state object type. Display name MAY be
preserved as descriptive metadata, but MUST NOT be the sole identity or
correlation key. A family suffix, rule name or test display string is not a
native target identifier.

Lifecycle information MAY be captured only where the source exposes it with
defensible semantics. The contract does not infer a deleted target from
absence, rename, display-name changes or incomplete inventory.

An observation SHOULD have a unique identity, source and target references,
type and schema/version, capture provenance, and source observation time when
the source supplies one. Preserve the source-native representation or an
explicit durable reference, along with any transformation description and
lineage. A digest MAY be recorded only if actually computed over identified
bytes and with its algorithm and coverage stated. A digest binds data to bytes;
it does not establish source truth, time, identity or collector authority.

Assessments, explanatory Markdown, test names and verdicts MUST NOT be
manufactured into source observations. Assessment-only records do not imply
an Observation exists.

## 6. Time authority and clock assumptions

Capture start, observation-captured, attempt-completion and run-completion
times SHOULD describe actual events measured by the collector's clock. Such
times MUST identify their producer/clock context and MUST NOT be backdated to
look like source observation times.

Caller-supplied source time MUST be preserved as source-asserted data, with its
source and known clock basis, precision, timezone/offset and uncertainty
retained where available. If those properties are unknown, record that
uncertainty; do not silently treat an unspecified timestamp as UTC or as
authoritative collector time. Parsing/normalization MAY produce a derived
time only when the original value and transformation remain available.

This proposal selects no trusted clock, synchronization service, maximum clock
skew, freshness interval or timestamp-signing model. Monotonic clocks MAY
support elapsed-duration measurement but do not by themselves establish
wall-clock time. Timestamps alone do not prove ordering across unsynchronized
collectors, freshness, authenticity or non-replay.

## 7. Coverage and collection health

Coverage is scoped to a declared source and requested scope. Where inventory
is known, preserve expected targets, observed targets and explicitly
not-observed targets, including the reason and relevant attempt. Where
inventory is incomplete or unknown, state that explicitly rather than
inventing an expected set.

For a known expected set, observed and not-observed targets MUST be unique and
disjoint; their union may be smaller than the expected set only when
unresolved/unknown targets or an explicit limitation explains the gap. A
target cannot simultaneously be reported observed and not-observed for the
same source, scope and run without an explicit time/version distinction.
`complete` coverage is permitted only when the collector can substantiate the
expected inventory boundary and account for every target in that boundary.
Successful query execution alone does not establish this.

Collection health summarizes attempt outcomes and known limitations; it is
not a security-control result. Partial, unavailable, denied, unsupported,
failed and not-attempted collection remain distinct. An unavailable target or
failed source attempt MUST NOT be mapped to an assessment `Fail`. Unknown
inventory MUST NOT be represented as complete coverage. Any summary is
derived from preserved attempt and coverage facts and MUST NOT erase them. A
run-level summary MUST NOT claim wholly successful or complete collection
while contradictory failed, partial, denied or unresolved attempts remain
within that summary's declared scope.

Exact aggregate status names, ratios, thresholds and whether one failed
attempt makes a run-level summary partial or failed are open design questions;
no single score is selected here.

## 8. Assessment linkage

When an assessment is performed, preserve stable rule identity and version,
evaluator identity and version, assessment subject, assessment time and its
provenance, execution state, conclusion, input basis and applicable control
coverage. References SHOULD resolve to the precise observations evaluated,
not merely to a run or package containing unrelated evidence.

An assessment MUST identify whether its basis consists of captured
observations, other explicitly declared inputs, or both. Assessment-only
records MAY exist when their legitimate declared basis is not an Observation,
but MUST NOT imply that source evidence was captured. A verdict with neither
resolved observations nor a defensible declared input basis is invalid.

Collection attempt status and assessment execution status are separate.
Skipped/unavailable collection does not become an assessment failure; an
assessment evaluator may itself fail to execute, which is not a control
conclusion. A package MUST reject contradictory execution-state/conclusion
pairs according to the eventual contract's defined mapping rather than
guessing one.

## 9. Package assembly invariants

The package assembler is a consistency boundary, not a truth oracle. Subject
to the eventual approved Evidence Envelope and schema definitions, assembly
SHOULD check:

- contract/version compatibility across all included records;
- unique run, attempt, observation and assessment identifiers in their
  declared scopes;
- every record's run/source references resolve to the intended run;
- source and target authority/scope are explicit and identities are not
  display-name-only;
- coverage sets are internally consistent with observations and attempts;
- terminal states, completion times and derived health summaries do not
  contradict one another;
- assessment subjects, evaluator context, input basis and observation
  references resolve and align;
- transformations retain lineage to original representation or reference;
- producer verification claims remain producer assertions and are not
  promoted to receiver verification.

Schema validation, package-consistency validation, capture behavior, and
independent receiver verification are different checks. Passing one does not
imply another. This proposed document does not promise that the current Core
validator checks these conditions or select its accepted cardinality.

## 10. Optional sidecar association

A structured sidecar is one optional integration design, not a required
architecture component or the default mechanism. If used, its association
with an assessment execution MUST be explicit and verifiable within the
declared trust model. A shared filename or approximate timestamp is
insufficient.

Candidate association evidence includes a producer-assigned execution ID
carried by both artifacts, explicit run ID references, and a manifest
containing exact artifact digests plus producer and version metadata.
Association MUST reject mismatched or ambiguous IDs. A digest detects
byte-level mismatch relative to the manifest but does not authenticate the
producer or prove the asserted execution occurred. The receiver's independent
verification state remains separate.

Filesystem safety, ACLs, atomic finalization, symlink/path traversal,
concurrent writers, stale/partial output, retention and crash recovery are
implementation-specific threats requiring a separately approved design and
tests. This proposal does not claim that a local sidecar is immutable.

## 11. Reusability beyond Maester

The shared contract describes source authority, attempts, targets,
observations, time, coverage, run context and optional assessment linkage. It
MUST NOT embed Maester-native types, fields or result-state names as the
provider-neutral model. Framework adapters may map native information only
when the mapping is documented and preserves its origin and limitations.

Collectors may be integrated with Maester, another assessment framework, or
run independently. A future adapter may consume assessment results without
source observations only where the declared input basis legitimately supports
that assessment-only representation. It MUST NOT reconstruct absent source,
target, timestamp, run or coverage facts from test text or outcomes.

## 12. Privacy, security and threat-model implications

Treat source evidence and metadata as potentially sensitive. Collection SHOULD
minimize data to purpose and scope, and avoid unnecessary payload copies,
raw error strings, credentials, tokens, tenant identifiers and personal data.
Diagnostic failures SHOULD identify the failing operation and safe
classification without echoing evidence or secret-bearing payloads.

The trust model distinguishes source authority, source visibility,
collector identity and permissions, transformations, evaluator, package
producer and receiver. A collector may be compromised, overprivileged,
misconfigured or unable to see all data. A producer may assert false
provenance. A valid schema or digest does not establish source truth,
authenticity, authorization, freshness, completeness or independent review.

Least-privilege access, explicit scope, secure handling, access controls,
retention/deletion, transport, signing, key custody and encryption require
implementation-specific decisions. No automatic upload, cloud, tenant
connection, permission expansion or persistence destination is authorized by
this proposal. The existing preliminary
[threat-model scope](../threat-model/README.md) remains incomplete and must be
refined before any operational deployment.

## 13. Proposed decisions and unresolved questions

### Proposed in this document

1. Preserve collection attempts, source observations, coverage and assessment
   conclusions as separate but explicitly linkable facts.
2. Require authority/scope-qualified source identity and stable native target
   identity; names alone are descriptive.
3. Keep source time distinct from collector capture time and retain clock
   provenance/uncertainty.
4. Treat coverage as bounded by an explicit scope and inventory basis; unknown
   inventory never implies completeness.
5. Treat package validation as structural/relational validation, not proof of
   producer truth or receiver verification.
6. Permit a sidecar only as an optional, explicitly associated integration
   pattern; no filename/time-based association.

These are Proposed, not approved decisions or implementation authorization.
See [ADR 0003](../adr/0003-evidence-preservation-capture-boundary.md).

### Unresolved

- Which concepts and exact fields can be represented in Evidence Envelope
  v0.1 without amending it, and which require a future contract version?
- What identifier uniqueness scope, ID generation, and duplicate-resolution
  rules are interoperable?
- How should source and scope identifiers be canonicalized across provider
  boundaries without implying cross-provider identity?
- Which source clock claims and precision/uncertainty representations are
  portable and testable?
- How should inventory snapshots, pagination, target churn and partial
  visibility define a complete expected set?
- What run-level health summary, if any, avoids misleading aggregation?
- Which assessment execution-state and conclusion combinations are valid?
- What minimum input-basis declaration supports legitimate assessment-only
  records?
- Must one run be limited to one source authority and scope, or may a run
  contain multiple source boundaries? If a capture implementation needs
  attempt IDs, intended-target details or clock/capture lineage beyond the
  approved Envelope schema, should those be represented in a separately
  versioned namespaced extension rather than new shared-schema fields?
- How should execution IDs be issued and bound across a framework and
  separately emitted sidecar?
- What storage, atomicity, access control, retention, privacy and independent
  verification controls are required for each implementation?
- How should this proposal align with Core schemas and validation without
  treating merged artifacts as explicit architectural approval?

## 14. Approval and evolution

This proposal remains Proposed until maintainers explicitly review and approve
its semantic decisions. Changes to package semantics require coordinated
review with Core, but Core schema state alone is not approval of Architecture
semantics. Any helper, interface, sidecar implementation, adapter, language,
storage, transport or operational trust decision needs its own scoped
implementation contract and validation evidence.

No behavior described here should be represented as already implemented,
tested, secure, immutable or independently verified.
