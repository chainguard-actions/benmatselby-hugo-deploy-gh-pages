<!-- markdownlint-disable -->

# Hardening Report: benmatselby--hugo-deploy-gh-pages/v2.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **benmatselby--hugo-deploy-gh-pages/v2.3.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses `actions/checkout@v4`, which is a mutable tag reference rather than a pinned 40-character commit SHA. This means the action could be silently updated or compromised without the workflow noticing, creating a supply-chain risk.

Locations:

- `.github/workflows/build.yml:9`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key, and the only job (`build`) also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions (which may be `write-all`), granting broader access than necessary.

Locations:

- `.github/workflows/build.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned `actions/checkout@v4` to full SHA `34e114876b0b11c390a56381ad16ebd13914f8d5` with `# v4` comment for readability. 2. Added top-level `permissions: contents: read` block — the minimum required for the checkout step — eliminating the risk of inheriting write-all default token permissions.

