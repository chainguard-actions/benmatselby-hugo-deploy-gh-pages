<!-- markdownlint-disable -->

# Hardening Report: benmatselby--hugo-deploy-gh-pages/v2.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **benmatselby--hugo-deploy-gh-pages/v2.5.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses `actions/checkout@v5`, which is a mutable tag reference rather than a pinned 40-character commit SHA. If the tag is moved (e.g. by a supply-chain compromise), the workflow will silently execute different code. Pin to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v5`.

Locations:

- `.github/workflows/build.yml:9`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and the `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository default (often `write-all`), granting unnecessarily broad access. Add a minimal `permissions:` block, e.g. `permissions: read-all` or specific scopes such as `contents: read`.

Locations:

- `.github/workflows/build.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both findings in .github/workflows/build.yml: (1) Pinned actions/checkout@v5 to the full commit SHA 93cb6efe18208431cddfb8368fd83d5badbf9bfd, preserving the tag as a comment. (2) Added a top-level `permissions: contents: read` block — the minimum required for the checkout step — replacing the implicit broad default permissions.

