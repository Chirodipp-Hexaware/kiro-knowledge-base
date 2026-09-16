# kiro-knowledge-base

Central, version-controlled knowledge base that Kiro pulls into context across
the organization. It packages the org's **steering** rules, **guardrails**,
**agents**, and **hooks** so every Kiro session — spec or vibe — starts from the
same governed baseline.

## What lives here

| Path | Purpose |
|---|---|
| `steering/org-standards/` | Always-on org standards (coding, tests, security, git). |
| `steering/design-template.md` | The `design.md` skeleton used by `sdlc_orchestrator_agent`. |
| `guardrails/mcp-allowlist.json` | MCP servers allowed by the Kiro Profile (MCP governance). |
| `guardrails/permission-policy.json` | `fs_write` / shell deny rules (permission policies). |
| `guardrails/model-policy.json` | Allowed models. |
| `agents/` | Custom agent definitions. |
| `hooks/` | Agent hooks (run on IDE events such as file save). |
| `.github/workflows/publish.yml` | CI that validates and publishes the knowledge base. |

## Governance

- Ownership is enforced by [`CODEOWNERS`](./CODEOWNERS): every change routes to
  `@org/kiro-platform-team`.
- Changes land through reviewed pull requests only — no direct pushes to the
  default branch.
- The `publish` workflow validates JSON policy files and Markdown before a
  change is considered publishable.

## How Kiro consumes this repo

1. **Steering** — files in `steering/` are loaded as context. Files under
   `org-standards/` are always included; `design-template.md` is referenced by
   the orchestrator agent when it drafts `design.md`.
2. **Guardrails** — the JSON policies under `guardrails/` are served to the Kiro
   Profile to constrain MCP access, filesystem/shell operations, and model
   selection.
3. **Agents** — Markdown definitions under `agents/` register custom agents.
4. **Hooks** — JSON files under `hooks/` trigger automation on editor events.

## Repository layout

```
kiro-knowledge-base/
├── CODEOWNERS
├── README.md
├── steering/
│   ├── org-standards/
│   │   ├── coding-standards.md
│   │   ├── test-conventions.md
│   │   ├── security.md
│   │   └── git-workflow.md
│   └── design-template.md
├── guardrails/
│   ├── mcp-allowlist.json
│   ├── permission-policy.json
│   └── model-policy.json
├── agents/
│   ├── sdlc_orchestrator_agent.md
│   ├── design_artifact_sync_agent.md
│   └── coding_standards_agent.md
├── hooks/
│   ├── test-on-save.hook.json
│   └── lint-on-save.hook.json
└── .github/workflows/
    └── publish.yml
```
