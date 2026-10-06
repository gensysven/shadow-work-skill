# shadow-work-skill

Signed release binaries for `shadowbench-runner`, the command-line runner behind the ShadowBench skill.

This repository is a download mirror. It holds no source code. The files are release assets, byte-for-byte as they were built and signed; every archive has a matching `.cosign.bundle` Sigstore signature bundle.

## Releases

- `skill-v1.0.0`: `shadowbench-runner-<platform>.tar.gz` and `shadowbench-runner-<platform>.tar.gz.cosign.bundle` for each supported platform.

## Verify before you run

```bash
cosign verify-blob \
  --certificate-identity "https://github.com/gensysven/shadow-work/.github/workflows/skill-release.yml@refs/tags/skill-v1.0.0" \
  --certificate-oidc-issuer "https://token.actions.githubusercontent.com" \
  --bundle shadowbench-runner-<platform>.tar.gz.cosign.bundle \
  shadowbench-runner-<platform>.tar.gz
```

The signing identity names the workflow that built the archives, not this repository, so the signatures stay valid wherever the files are hosted. Do not run an archive that fails verification.

## Install

The ShadowBench skill installer downloads from this repository when `SHADOWBENCH_RELEASE_URL_BASE` is set:

```bash
export SHADOWBENCH_RELEASE_URL_BASE=https://github.com/gensysven/shadow-work-skill/releases/download/skill-v1.0.0
```

