# Packages

LM-Nexus marketplace packages are distributed as GitHub Release assets, not as
files committed to this directory.

Use this directory for optional package-specific notes only. Release assets
should follow this convention:

```text
https://github.com/<owner>/<repo>/releases/download/<package-id>-v<version>/<package-id>-<version>.zip
```

Every package version listed in `../lm-nexus-marketplace.json` must include the
release asset URL and its SHA-256 checksum.
