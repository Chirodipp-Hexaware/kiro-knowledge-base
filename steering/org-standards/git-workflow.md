---
inclusion: always
---

# Git Workflow

How the org uses git and GitHub. Always loaded into Kiro context.

## Branches

- Never commit directly to `main`/`master`. Work on a branch.
- Branch naming: `feature/<short-desc>`, `fix/<short-desc>`,
  `hotfix/<defect-id>`, `chore/<short-desc>`.
- Push new branches with upstream tracking (`git push -u origin <branch>`).

## Commits

- Only create commits when explicitly asked. If unclear, ask first.
- Stage specific files by name; avoid `git add -A` / `git add .` to prevent
  committing unrelated changes.
- Write conventional, imperative commit subjects under ~70 chars
  (`fix: reject blank orderId`). Use the body for the why.
- Prefer new commits over `--amend`. Never rewrite pushed history.
- Never skip hooks (`--no-verify`) unless explicitly requested.
- Flag any file that may contain secrets (`.env`, `credentials.json`) before
  committing it.

## Pull Requests

- All changes land through reviewed PRs. `CODEOWNERS` review is required.
- PR title concise (< 70 chars); description covers: summary of changes, how it
  was tested, and any follow-ups or blocked items.
- Keep PRs focused and reviewable; split large changes.

## Safety

- Never change git config.
- Destructive commands (`push --force`, `reset --hard`, `clean -fd`,
  `branch -D`) require explicit human approval.
- Merging to a protected branch happens only through the GitHub review flow —
  agents never merge or force-push to a protected branch.
