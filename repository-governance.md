# Repository governance baseline

This document describes the intended baseline, not a substitute for reading
actual GitHub settings. Unsupported or permission-blocked controls must be
reported rather than silently treated as enabled.

## Authority and change flow

Each repository owns canonical `.github/carl/` state and effective instruction
packs. Generated harness adapters are loaders, not independent policies.
Bundled managed files remain canonical. Repository-specific invariants and
trust boundaries live in protected `memory.md`, supplementing bundled guidance.
Public community-file inheritance does not propagate cARL or rulesets.

Only the initial bootstrap is pushed directly to empty `main`. Subsequent
content changes use feature branches, scoped cARL contracts and PRs.
No auto-merge, force push, protected-branch deletion or automation bypass.

## Sole-maintainer review and recovery

Initially there is one owner. Require PRs but zero enforced approving reviews;
GitHub authors cannot approve their own PRs, so requiring another approval would
lock out the only maintainer. CODEOWNERS records responsibility without an
impossible required code-owner approval. This is a declared separation-of-duties
limitation, not an independent-review claim. Maintainer review is still expected.
Revisit approval requirements only through an explicit governance decision
when another authorised reviewer exists; do not add members during bootstrap.

Use named, passing checks only after real governance CI runs successfully.
Fix broken checks in a branch and PR, retain the same required job name and
rerun transient failures. Do not disable required checks or grant bypass to
merge a fix. Keep account recovery codes and phishing-resistant credentials
under the owner's private control, outside these public repositories.
Account recovery or unavailable approvals require owner action, not an agent
changing organisation ownership, adding members or weakening protection.

## Least-privilege settings

Require organisation 2FA and prefer phishing-resistant methods where supported.
The owner must verify recovery methods privately before enforcing an
authentication policy. Restrict base member permissions and unnecessary
repository/Pages creation. Do not purchase services to obtain unavailable
controls.

Use `main`, block force pushes and deletion, require PRs and real checks.
Set default `GITHUB_TOKEN` permissions to read-only and disallow Actions from
creating/approving PRs. Governance CI needs no secrets, cloud identity or
administration rights; never self-administer repository settings in a workflow.
Use reviewed, pinned actions and checksum-verified cARL binaries.

Enable dependency alerts/security updates, secret scanning, push protection
and private vulnerability reporting when supported. With no dependency
manifests, Dependabot settings are preventative, not a claim of dependency
coverage. No fake product checks, code-scanning claims or decorative badges.
