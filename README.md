# LM-Nexus Marketplace

This repository is the public GitHub-based marketplace index for LM-Nexus module
packages.

The canonical index file is [`lm-nexus-marketplace.json`](lm-nexus-marketplace.json).
LM-Nexus reads the raw version of that file from:

```text
https://raw.githubusercontent.com/Aveer/lm-nexus-marketplace/main/lm-nexus-marketplace.json
```

Package archives are distributed as GitHub Release assets. The marketplace index
contains package metadata, version metadata, release asset URLs, and required
SHA-256 checksums.

## Safety model

LM-Nexus keeps the marketplace workflow conservative:

- every package version must include a SHA-256 checksum;
- remote archives are verified before validation or install;
- packages are validated with the LM-Nexus package validator before installation;
- operators must explicitly trust the source/package and approve declared
  permissions before activation;
- package install scripts, hooks, and shell commands are never executed;
- installed backend routers activate only after restart/startup validation;
- installed frontend payloads use generated-bundle/rebuild metadata rather than
  runtime imports from app-data.

This repository is an index and distribution convention. It is not a hosted
marketplace service, account system, payment system, moderation system, signing
authority, sandbox, or runtime permission-enforcement layer.

## Publishing workflow

1. Create a Nexus module package with a safe `nexus.module.json` manifest.
2. Validate the package with LM-Nexus:

   ```bash
   scripts/nexus packages validate /path/to/package
   ```

3. Pack the package and compute its SHA-256 checksum.
4. Create a GitHub Release in the package source repository.
5. Upload the package ZIP as a release asset.
6. Open a pull request updating `lm-nexus-marketplace.json` with the package and
   version metadata.

Preferred release asset URL shape:

```text
https://github.com/<owner>/<repo>/releases/download/<package-id>-v<version>/<package-id>-<version>.zip
```

Package source repositories may be separate from this marketplace index
repository.

## Index schema

The index uses `schema_version: 1`:

```json
{
  "schema_version": 1,
  "marketplace_id": "lm-nexus.community",
  "display_name": "LM-Nexus Marketplace",
  "description": "Open GitHub-based marketplace index for LM-Nexus modules.",
  "packages": []
}
```

Each package version entry must include an HTTPS GitHub `archive_url` and a
`sha256` checksum. Packages without checksums may be reviewed as metadata but are
not installable by LM-Nexus.
