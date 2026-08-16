<!-- markdownlint-disable -->

# Hardening Report: benmatselby--hugo-deploy-gh-pages/v2.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **benmatselby--hugo-deploy-gh-pages/v2.1.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses actions/checkout@v4, which is pinned to a mutable tag rather than an immutable 40-character commit SHA. A tag can be moved to point to a different (potentially malicious) commit, enabling supply-chain attacks. Replace with the full SHA, e.g. actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.

Locations:

- `.github/workflows/build.yml:9`

### missing-permissions (severity: medium)

The workflow file has no top-level permissions: key and the single job (build) also has no job-level permissions: key. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions. Add a top-level permissions: block with the minimal scopes required (e.g. contents: read).

Locations:

- `.github/workflows/build.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed .github/workflows/build.yml: (1) Pinned actions/checkout@v4 to full commit SHA 11d5960a326750d5838078e36cf38b85af677262 # v4. (2) Added top-level permissions block with contents: read — the minimum required for checking out code and running shellcheck.

