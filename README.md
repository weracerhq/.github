# .github

Org-wide defaults for weracerhq: issue templates (story, task, bug) and the PR template.
Repos without their own templates use these.

**This repo is public — never put anything sensitive here.**

## Reusable workflows

Call them from a repo's workflow with `uses: weracerhq/.github/.github/workflows/<file>.yml@main`.

| Workflow | What it does |
|---|---|
| `go-ci.yml` | golangci-lint, govulncheck, `go test` with a PostgreSQL 17 + PostGIS service (`DATABASE_URL`) |
| `openapi-ci.yml` | Spectral lint, oasdiff breaking-change check vs. latest release asset (or base branch) |
| `gradle-ci.yml` | JDK 17 + Gradle cache, `./gradlew check` (skips while there is no `gradlew`) |
| `infra-validate.yml` | `kustomize build` per overlay + kubeconform (skips overlays without a kustomization) |
| `gitleaks.yml` | gitleaks CLI scan of the full git history |

Third-party actions are pinned to commit SHAs and CLI binaries are pinned by version + SHA-256.
Dependabot bumps the actions; bump the binary versions/checksums in the `env:` blocks by hand.
