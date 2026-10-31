# Maester Pack compatibility research

**Status:** Source-verified research; not a new Evaxis contract. The
Evidence Envelope v0.1 specification remains a proposal pending approval.
Research performed 2026-10-28 against the pinned `main` commits below.

## Executive result

Maester 3 has a real native Pack lifecycle, native PowerShell test engine,
typed result rows, and versioned result JSON. Its results are assessments,
not source snapshots. A narrow future importer is possible for assessments
when the caller supplies valid run/subject context and preserves Maester's
original result as an external reference. The standard per-test rows alone
are insufficient to form a complete Evidence Envelope package: they do not
contain a source collection manifest, source observations, an exact
per-assessment timestamp, or an authority-qualified subject identity for
every test. No production adapter or schema change is justified yet.

Synthetic offline execution demonstrated Pass, Fail, Investigate, Skip,
Error, disconnected-service Skip and three distinct family row IDs.
Structural validity did not establish execution, source collection, assessment
correctness or coverage. No Microsoft tenant was accessed.

## Pinned upstream references

| Repository | Owner / default branch | Commit | License | Compatibility |
|---|---|---|---|---|
| [maester](https://github.com/maester365/maester) | `maester365` / `main` | `b8ad89557a831d3d3d7c369174300701243af8a6` | MIT | module 3.0.0; PowerShell 7.4+; `Microsoft.Graph.Authentication` 2.27.0; repo build uses .NET SDK 10.0.300 |
| [maester-pack-demo](https://github.com/maester365/maester-pack-demo) | `maester365` / `main` | `3f83cc8b674ac7c195f4611473e21bec6c50e8f3` | MIT | `RequiresMaester >=3.0`; synthetic tests plus one Graph test |
| [maester-pack-lpms](https://github.com/Mynster9361/maester-pack-lpms) | `Mynster9361` / `main` | `f6aa60d98cc8b0efab233b7332d1269a4bd9690c` | MIT | `RequiresMaester >=3.0`; Azure, Graph and Log Analytics |
| [maester-pack-rksolutions](https://github.com/royklo/maester-pack-rksolutions) | `royklo` / `main` | `852a83b1b57fc2490d8d5554d7ca6102504b63d4` | MIT | `RequiresMaester >=3.0`; Graph/Intune checks |

The local read-only reference clones and repeatable PowerShell command are in
`~/git/evaxis-upstream-lab`. Each clone was clean at its recorded SHA. The
lab's `outputs/` files are local synthetic runtime output, not tenant data and
not part of either product repository.

## Lifecycle and command surfaces confirmed in source

- `New-MtPack` scaffolds `maester-pack.json`, suite, first `MP.<Code>.1001`
  native test and optionally a connector. IDs use a pack-owned Code; the pack
  has a persistent GUID and semantic version.
- `Test-MtPack` reads and validates the manifest, tests, scripts, IDs and
  declared Uses without installing the pack or running its test bodies. It
  reports `IsValid`, risk, findings, test IDs and a digest.
- `Invoke-MtTest -Path <pack-folder>` is the documented local-development path.
  It runs native tests from the folder with its helpers/connectors and returns
  Maester rows; `-Id` can select an explicit subset. This was used for offline
  execution.
- `Install-MtPack` supports an upstream built-in ID, local folder or GitHub
  source. For external packs it inspects before code execution, applies policy,
  blocklist and cooldown, pins commit/digest and module digests in
  `maester-packs.lock.json`, and asks for risk approval. The lock/config are
  required to restore the approved artifact. Public GitHub install sends an
  anonymous installation event unless telemetry is disabled.
- `Update-MtPack` repeats the checked install process, compares changes and
  retains locked artifacts. `Restore-MtPack` restores a lock-pinned commit.
- `Invoke-Maester -Pack <Code|Id>` runs a named installed/built-in pack.
  Installing alone does not run it. `-SkipBuiltIn`, `-AllPacks`, test
  selection, config selectors, preview/long-running switches, and
  `-PassThru` are implemented. The exact local-development path is
  `Invoke-MtTest -Path`; Pack selection in `Invoke-Maester` is not a substitute
  for installation and lock state.
- `Connect-Maester` handles standard and Pack-declared connectors. It reports
  per-service connection state. A native test's `Service` attribute is gated
  by the engine; absent connection yields a `Skipped` row with reason code
  `ServiceNotConnected`, not a control Fail.

Installation success, static validation, discovery, execution, source
collection, assessment and complete source coverage are independent states.
`Test-MtPack` passing establishes only static acceptance at that source
snapshot; it does not prove a test ran or collected anything.

## Pack identity, test identity and result structures

The official built-in Zero Trust Assessment pack has ID
`maester.zero-trust-assessment`, code `ZTA`, version `0.1.0`, static
`catalog.json`, and one native suite test `ZTA`. Its catalog is generated from
the separately versioned Microsoft `ZeroTrustAssessment` module
(`2.6.0`, external URL in manifest), not a catalog of per-object Maester test
rows. The manifest declares Graph and many delegated/application Graph
permission names, no tenant writes, and module processing `"Child"` for the
module. Maester's built-in identity is reserved and cannot be uninstalled.
An external Pack using reserved `maester`/`maester365` publishers, `MP.` or
`ZTA.` identifiers needs official validation/ownership; it is not equivalent
to installing an arbitrary external Pack.

The starter Pack's `Initialize-MtPackFromDemo` is a PowerShell scaffolder
function. It rewrites pack identity, GUID, code, test IDs, service/function
names and repository URLs in the copied template, updates suite metadata and
retains selected optional manifest fields. It is not itself a runtime feature.
The demo has IDs MP.DEMO.1001–1009. Its only Graph-dependent example is 1007;
1001–1005 and 1009 use made-up values, 1006 has a made-up connector, and 1008
is a long-running synthetic progress/report example.

The Maester 3.0 result object advertises `SchemaVersion: "2.1"` and top-level
fields including `ExecutedAt`, `CurrentVersion`, `TenantId`, `TenantContext`,
`RunMetadata`, `Tests`, attachments and output metadata. Native rows include
`Id`, `Result`, `ResultDetail`, `Duration`, `ReasonCode`, `ReasonDetail`,
`ParentId`, `InstanceId`, `Parameters`, typed attributes, and `Package`
(`Id`, `Version`, `Commit`, `Publisher`, `BuiltIn`, `Runtime`). `Commit` was
null for the local demo run; installed-lock provenance may be available in
other contexts. Maester's row schema is versioned independently from Evaxis.

Native family expansion preserves a Maester result identity: the family test
ID remains `ParentId`, and each `InstanceId` is the full test ID plus the
instance-source suffix, e.g. `MP.DEMO.1009.app-one`. This is not proof that
the suffix is globally unique or an authority-qualified provider-native ID.
In the LPMS test source, the suffix is deliberately the service-principal
`PrincipalId`; a mapping still needs its source authority and tenant scope.
The RK Intune tests are currently test-level rows, not one row per device;
device names in Markdown summaries are not stable identities.

`ResultDetail.TestResult`, markdown tables, error text, attachments,
`TenantName`, account and Graph context can contain sensitive tenant,
identity, or configuration data. An importer should minimize and redact
before persistence; preserve an immutable original only in a purpose-approved
private evidence store. Do not copy raw reports or tenant identifiers into
public fixtures, logs or pull requests.

## Third-party execution and trust boundaries

Maester explicitly states that a Pack runs PowerShell in the Maester process
with its connections, environment and files; it is not a sandbox. Read-only
Graph scopes restrict tenant writes, not local file access or exfiltration.
Install-time scanning and risk approval are supply-chain controls, not
isolation or proof of author trust. `Uses` declares services, Graph scopes,
network hosts, writes and modules. A child-process module has a separate
installation/trust implication and may increase risk. External module versions
and folder digests are part of the approval/lock process.

Connector scripts, helper code, child-process modules, PowerShell errors,
progress logs and HTML report attachments are untrusted inputs. Progress
(`Write-MtTestOutput`, `Write-MtTestProgress`, `##maester[progress]`) is
execution telemetry, not evidence. `Add-MtReportAttachment` adds content to
the Maester report; it does not automatically make that report a source
Observation or an immutable evidence reference.

## Independent Pack findings

### LPMS

`mynster9361.least-privileged-msgraph` / `LPMS` is version 1.0.2.
Its `InstanceSource` creates per-service-principal results from `PrincipalId`
after a cached module-backed data collection. Tests include excess
permissions, unmatched activity, unused permissions, no activity and unknown
permission analysis. The Pack uses `EntraAuth` 1.8.56 and
`LeastPrivilegedMSGraph` 3.3.0, Microsoft Graph `Application.Read.All`,
Azure/Log Analytics access, `api.loganalytics.io` and `graph.microsoft.com`.
The guide needs the Entra `MicrosoftGraphActivityLogs` diagnostic setting, a
workspace ID/configuration, and Monitoring Reader (or Reader) on that
workspace. The Guide notes logs can take up to 48 hours to arrive; the default
analysis window is 30 days. A service principal with no log activity is
`Investigate`, not an automatic Fail; activity outside the window, delayed or
missing logs, unmatched API endpoints, disconnected Azure and permission
denials limit the analysis. It attaches an HTML analysis report.

### RKSolutions Intune Anomalies

`royklo.rksolutions-intune-anomalies` / `RKS.IA` is version 0.1.4 with eight
test IDs. It uses Graph scopes including
`DeviceManagementManagedDevices.Read.All`,
`DeviceManagementConfiguration.Read.All`,
`DeviceManagementServiceConfig.Read.All`, `BitlockerKey.ReadBasic.All`,
`DeviceLocalCredential.ReadBasic.All` and `Directory.Read.All`. Test helpers
call Graph directly through an adapter and reuse code mirrored from
`RKSolutions-Module` under `helpers/core`; the code is explicitly synchronized
from upstream module commit `ec3c365`. It has no declared external module.
The pack and tests use connected Graph with device-level objects and can skip
LAPS/BitLocker checks when access is denied. Current result rows are per-test,
while device-specific findings are markdown detail (limited to 200 rows) and
the optional full report comes from the external RKSolutions module.

Its CI validates each pack with `Test-MtPack`, requires Low risk/no findings,
runs pack tests through `Invoke-MtTest`, and runs helper Pester tests. A
release job is gated on `PACK_RELEASES=true` and tags
`<pack-folder>-v<Version>`. It does not publish automatically from a pull
request.

## Mapping to Evidence Envelope v0.1

| Evaxis record/fact | Maester source | Assessment |
|---|---|---|
| Envelope producer/runtime | `CurrentVersion`/module version in full run; pack `Package` per row | Adapter can identify Maester runtime and Pack only when run-level data or installed provenance is retained. It cannot infer a missing source commit. |
| Run identity/time | Optional `RunMetadata`; top-level `ExecutedAt` in full result; none in `Invoke-MtTest` rows | Optional arbitrary metadata is not a guaranteed unique run ID. `ExecutedAt` is run-result metadata, not necessarily a per-row assessment timestamp. Require explicit provenance or reject. |
| Stable test/rule identity | Row `Id`; `ParentId` and `InstanceId`; pack version | Stable test ID can map to rule ID; Pack version is a package version, not a separately declared rule implementation version. Preserve rule-version uncertainty. |
| Source authority/scope | `TenantId`/`TenantContext` may be in full result; row alone has neither | Only use an actual native tenant ID and explicit scope. Never use tenant display name or disconnected sentinel. |
| Source Observation | No standard row field for raw source object/data, source schema or observation timestamp | Do not create one from verdict, markdown, family suffix, or report. Pack-specific APIs/data adapters would be needed. |
| Collection Manifest | Connection summary and test-level reasons in full run; not a source-attempt inventory | A Maester report does not enumerate all expected source targets/permissions or complete coverage. Disconnected `ServiceNotConnected` can be captured as a limitation, but not generalized to all source attempts. |
| Assessment | `Result`, reason, test ID, details, `Duration`, package provenance | Pass/Fail/Investigate/Skipped/Error are Maester execution/assessment claims. Map only with a documented assessment basis; lack of evidence cannot become Fail. |
| Trust | Pack publisher, commit/digest, module digest and install risk | These are supply-chain and producer assertions. They do not establish receiver-verified evidence or source truth. |
| Family identity | `ParentId`, `InstanceId` plus `InstanceSource` implementation | Preserve as Maester test-instance identity. Promote to source target identity only with explicit source authority, tenant scope and verified mapping from that exact instance source. |
| Unknown fields | Versioned Maester result JSON and typed row extensions/details | Preserve raw result or immutable reference and unknown fields as non-authoritative; do not merge them into normative fields. |

The minimal input to any future assessment importer must include an unmodified
versioned Maester run result, exact Maester runtime, pack ID/version and
artifact provenance (commit or digest when available), a unique capture/run
identity, explicit assessment timestamp provenance, exact test row identity,
and source authority/scope/native target identity. Any required item not
provided must be rejected or represented as unknown; the schema's required
subject and timestamp fields cannot be populated with placeholders.

For assessment-only imports with no source payload, no Observation is emitted.
If a complete record package cannot be made without inventing target or
collection context, reject the package instead of fabricating empty
observations or claiming complete coverage. A separately specified claim-only
archive format may preserve raw Maester results, but that is not itself a
schema-valid Envelope package.

## Validation evidence and readiness

| Stage | Result |
|---|---|
| A — Static source/manifests | Confirmed against the pinned Maester and Pack sources. |
| B — Offline execution | PowerShell 7.6.0; Maester 3.0.0 imported from the pinned source. `Test-MtPack` returned valid for the demo, built-in ZTA, LPMS and RK Intune packs. `Invoke-MtTest -Path` ran seven selected demo IDs and returned nine rows: Passed, Failed, Investigate, custom Skip, Error, connector-not-connected Skip, and three family instances. The repeat script asserts the expected IDs/statuses, disconnected reason and family identities. No Graph test, connector or tenant credentials were used. |
| C — Evaxis adapter | Deferred. The source rows do not supply defensible manifest/observation/timestamp/subject data for all cases. |
| D — adversarial cases | Mapping limitations enumerated above; no adapter exists to run executable adversarial mapping tests against. |
| E — governance/conformance | cARL diagnostics healthy in Architecture and Core. Core's existing v0.1 conformance suite remains the schema/package validator; it does not validate Maester semantics. |

An exploratory `Invoke-Maester` call against the uninstalled demo folder
reported that the Pack was not installed/locked and did not complete as a
valid full run. It was stopped; no run-envelope output from that attempt is
used as evidence. The repeatable lab script intentionally limits itself to
`Invoke-MtTest -Path` until a reproducible installation/lock-based workflow is
documented and validated.

The lab's reproducible command is
`pwsh -NoProfile -File ~/git/evaxis-upstream-lab/scripts/verify-maester.ps1`.
It disables Maester telemetry, runs only reviewed synthetic demo IDs, and
does not install a Pack, call `Connect-Maester`, or access Microsoft Graph.

The published docs at `maester.dev/docs/next` and `packs.maester.cloud/publish`
describe Pack authoring, security, result schemas and publication. Source and
offline execution above take precedence where docs are incomplete or differ.
For example, the fetched publishing page had a malformed concatenated example
for `Invoke-MtTest` and `Test-MtPack`; actual source and demo README show those
as separate commands.

## First-Pack readiness and future directions

**Ready offline:** scaffold a Pack, validate its structure, discover IDs,
execute reviewed synthetic native tests, test disconnected-service behavior,
and run pack CI without a production tenant. The demo shows native attributes,
parameters/settings, connector contracts, long-running progress/report
attachment and test families. Avoid Graph/tenant examples in the first
credential-free CI stage.

**Still required before a real first Pack:** explicit target inventory and
source-attempt semantics; source authority, scope and native IDs; per-run and
per-observation timestamps; collection coverage and permission/connection
health; stable rule/implementation version; raw minimal evidence or durable
reference; change/history compatibility; least-privilege Graph permission
review; privacy-approved report persistence; adapter acceptance tests against
captured production-safe fixtures. Pack results alone cannot satisfy these.

Maester's catalogue publication requires a public GitHub Pack repository,
valid manifest and IDs, test or connector, a tagged release, owner eligibility
and an owner/admin publishing through the catalogue flow. This work does not
create a Pack or submit to the catalogue.

**Maester → Evaxis** would import Maester assessment claims and associated
evidence only where separately available. **Evaxis → Maester** would require
a distinct supported Maester test interface to surface Evaxis-derived
assessments; no shared adapter or supported Evaxis ingestion API is assumed.
