<!--
IDENTITY: AGENTDIRPRO LAB / WO-2 / CI housekeeping
PROVENANCE: Muse housekeeping review and user-directed three-part fix, 2026-10-22
-->
# Agentdirpro

Agentdirpro is an infrastructure archaeology audit lab and a repository for its reproducible public records.

## Project page

The public project page is [`index.html`](index.html). It describes the audit method, GhostHunter corpus, sealed-deliverable escrow, and contact path.

## Integration suite

The GitHub Actions workflow lives at [`.github/workflows/integration-suite.yml`](.github/workflows/integration-suite.yml). It runs on pushes to `main`, provisions Python 3.12, restores a virtual-environment cache, installs the pinned dependencies in [`requirements-lock.txt`](requirements-lock.txt), and runs the future `tests/` suite.

The cache key hashes only the stable lockfile content. The lockfile contains no timestamps or generated metadata, so unchanged dependency content produces the same key.

## Conventions and records

Repository conventions are defined in [`AGENTS.md`](AGENTS.md). Review outcomes and work-order self-reports are recorded in [`SWEEP_LOG`](SWEEP_LOG).

<!--
SELF-REPORT
Status: complete
Work order: WO-2 CI housekeeping
Implemented: moved the workflow from README into .github/workflows/integration-suite.yml, added requirements-lock.txt with stable pinned content, and retained README as documentation rather than executable configuration.
Verification: checked that README no longer contains the workflow YAML, the workflow hashes only requirements-lock.txt, and the lockfile has no timestamped metadata.
Limitations: tests/ is not present in the repository, so the integration test command was not executed.
-->
