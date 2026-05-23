# Contributing to the LM-Nexus Marketplace

Contributions are made by pull request against `lm-nexus-marketplace.json`.

## Requirements

- The package archive must be hosted as an HTTPS GitHub Release asset.
- The package version entry must include a SHA-256 checksum of the exact uploaded
  archive bytes.
- The package must validate with `scripts/nexus packages validate`.
- Package metadata must accurately list module IDs, dependencies, optional
  dependencies, permissions, compatibility, source repository, license, and
  author information.
- Packages must not include secrets, local machine paths, runtime data, install
  scripts, hooks, shell commands, or other executable install-time directives.

LM-Nexus verifies checksums, validates packages, and asks operators for trust and
permission approval before activation. This repository does not provide
cryptographic publisher signing, sandboxing, runtime permission enforcement,
accounts, payments, ratings, comments, or moderation workflows.

## Review checklist

Reviewers should confirm:

1. `lm-nexus-marketplace.json` remains valid JSON.
2. The release asset URL is an allowed HTTPS GitHub URL.
3. The checksum is present and formatted as a SHA-256 digest.
4. The package source repository and license are clear.
5. Permission and dependency declarations match the package manifest.
6. The submitted validation output shows the package validates with LM-Nexus.
