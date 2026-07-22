# Engineering workspace: ~/repositories

## What this folder is

The home of the engineering **project vault**: `agents/` is an Obsidian vault
for investigations, plans, decisions, and documents that span tickets or
repos, and this guide (plus `CLAUDE.md`) tells agents how to work with it.

**Code repos do not need to live here.** They stay wherever you already keep
them — one folder per repo, anywhere on your machine — and the
[Repos](#repos) table below records each path. Cloning repos next to
`agents/` in this folder works too, but it's a choice, not a requirement.

## Two areas

| Path | Purpose |
|---|---|
| `~/repositories/agents/` | Obsidian project vault — see [`agents/AGENTS.md`](agents/AGENTS.md) |
| *your repo paths* | Source code repos, wherever you keep them — listed in [Repos](#repos) |

## How we work

The typical flow:

1. **Identify the repo** — the work almost always touches a specific repo.
   Find its path in the [Repos](#repos) table.
2. **Small, self-contained task?** Work directly in the repo.
3. **Multi-ticket, cross-repo, or research-heavy task?** Open or create a
   project in the vault (`agents/projects/`). Use the scaffold script:
   ```bash
   bash ~/repositories/agents/scripts/new-project.sh <slug> [--tickets PROJ-1,PROJ-2]
   ```
4. Use the vault to store plans, investigations, decisions, and documents that
   shouldn't live in any single repo.

## Repos

Add a row for each repo you work on — where it's cloned and a short
description of its role in your stack. This table is how agents map a repo
name to a location, so keep it current. When starting a new engagement:

```bash
gh repo clone <org>/<repo>          # preferred — handles auth, sets upstream
git clone git@github.com:<org>/<repo>.git
```

| Repo | Path | Description |
|---|---|---|
| *(none yet — add repos as you start working on them)* | | |

## Conventions

- **Repos** — live wherever you keep them, one folder per repo. Never clone a
  repo inside `agents/` (the vault is notes-only and may be synced), and do
  not nest repos inside each other.
- **Worktrees** — git worktrees live inside the repo they belong to, under the
  default `.claude/worktrees/` path (e.g.
  `<repo-path>/.claude/worktrees/<branch>`). Never create them as sibling
  directories of the repo.
- **Secrets** — never put credentials, `.env` files, or tokens in the vault.
  The vault may be synced via Obsidian Sync.
- **Vault internals** — do not commit or modify `agents/.obsidian/`; it is
  managed by Obsidian.
- **Repo hygiene** — each repo manages its own `CLAUDE.md`/`AGENTS.md` for
  project-specific instructions.
