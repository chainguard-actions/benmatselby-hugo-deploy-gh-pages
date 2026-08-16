<!-- markdownlint-disable -->

# Hardening Report: benmatselby--hugo-deploy-gh-pages/v2.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **benmatselby--hugo-deploy-gh-pages/v2.4.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses `actions/checkout@v4`, which is pinned to a mutable tag (`@v4`) rather than an immutable 40-character commit SHA. This means the referenced action could be silently replaced with a different (potentially malicious) version. It should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/build.yml:9`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/build.yml` has no top-level `permissions:` key and the single job (`build`) also has no `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be broader than necessary (e.g. write access). A minimal `permissions:` block such as `contents: read` should be added at the top level or job level.

Locations:

- `.github/workflows/build.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned `actions/checkout@v4` to its full commit SHA `34e114876b0b11c390a56381ad16ebd13914f8d5` with a `# v4` comment for readability. 2. Added a top-level `permissions: contents: read` block to restrict the workflow token to the minimum required permissions.

