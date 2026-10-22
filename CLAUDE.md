# .github — org-wide defaults (PUBLIC repo)

Issue forms, PR template, org profile and the reusable workflows every WeRacer repo calls (`go-ci`, `openapi-ci`, `gradle-ci`, `infra-validate`, `gitleaks`). This repo is public: never put secrets, internal URLs or plans here.

## Commands
- Lint workflows: `actionlint`
- Pin every third-party action to a full commit SHA with the version in a comment.

<!-- team-rules:start -->
## WeRacer team rules (synced from weracerhq/docs/agents/team-rules.md — edit there, not here)

**Work**
- Start from a GitHub issue with acceptance criteria. If there is none or it is vague, stop and ask instead of guessing.
- One issue → one small PR to `main` (squash merge). Conventional commits (`feat:`, `fix:`, `chore:`, `docs:`, `ci:`…). Put `Closes weracerhq/<repo>#<n>` in the PR body.
- CI must be green before merge (the Free plan can't enforce it — we do). Don't merge your own PR unless the human asked; `/wave` PRs are the exception: its Codex merger agent merges them under the checks in the wave skill (add `manual` to `/wave` to merge them yourself).
- Never add Claude attribution: no `Co-Authored-By: Claude` trailer, no "Generated with Claude Code" line in PRs, issues or comments.
- Never mention other products or competitors by name in code, docs, issues or PRs.
- Ask before anything destructive or hard to undo: force-push, history rewrite, deleting branches/data, changing org or repo settings, touching production.
- English for everything: code, comments, commits, issues, PRs and docs.
- Runner minutes are limited (Free plan: 2,000 a month for private repos). Run the repo's checks locally before pushing and push when they pass, not after every work-in-progress commit. Keep iOS builds local: macOS runners cost 10× the minutes.

**Context** — plan and architecture live in `weracerhq/docs` (`plan.md`, `product/scope.md`, `architecture/`, `decisions/`). Board: https://github.com/orgs/weracerhq/projects/1. Read only the sections you need.

**Model routing (save tokens)** — sessions run on Sonnet by default. Delegate:
- `scout` (Haiku): searching code, reading CI logs, listing issues/PRs, summarizing long files or diffs.
- `tech-lead` (Opus): splitting an issue into tasks, design decisions, final review against acceptance criteria.
- `api-designer` (Opus): any change to the OpenAPI contract.
- `security-reviewer` (Opus): before merging auth, tokens, personal data, secrets, infra exposure or CI workflow changes.
- Implementation agents (Sonnet): `backend-dev`, `mobile-dev`, `infra-dev`, `test-writer`.
- Don't use Opus for routine coding. Don't read whole large files when grep will do. Keep at most 2–3 agents in parallel.
- Codex sessions: the agents above are Claude-only; do the work directly and keep to the same rules.
<!-- team-rules:end -->
