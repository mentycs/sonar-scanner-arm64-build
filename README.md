# sonar-scanner-arm64-build

Multi-arch (linux/amd64 + **linux/arm64**) build of the official
[SonarSource/sonar-scanner-cli-docker](https://github.com/SonarSource/sonar-scanner-cli-docker)
image, which upstream publishes for amd64 only (arm64 support was proposed in
[PR #307](https://github.com/SonarSource/sonar-scanner-cli-docker/pull/307) but not released).

`Dockerfile`, `bin/entrypoint.sh` and `LICENSE` (LGPL-3.0) are taken verbatim from
upstream master. The scanner zip used is the generic JRE-less distribution; the JRE
comes from the multi-arch `amazoncorretto:21-al2023` base, so no arch-specific
patching is needed.

## Image

```
ghcr.io/mentycs/sonar-scanner-cli:<scanner-version>
ghcr.io/mentycs/sonar-scanner-cli:latest
```

Built by `.github/workflows/build.yml` (buildx + QEMU) on every change to the
Dockerfile and on manual dispatch.

## Updating

Bump `ARG SONAR_SCANNER_VERSION` in the Dockerfile (and refresh the files from
upstream if they changed), push to `main` — the workflow tags the image with the
new version automatically.

Not affiliated with or supported by SonarSource.
