# Workspace: ~/repositories

## What this folder is

This is the local workspace where repos are cloned for active development.
When starting a new engagement, clone the repo here:

```bash
gh repo clone <org>/<repo>          # preferred — handles auth, sets upstream
git clone git@github.com:<org>/<repo>.git
```

Keep one repo per directory at the root. Do not nest repos inside each other.

## Two areas

| Path | Purpose |
|---|---|
| `~/repositories/<repo-name>/` | Source code repos |
| `~/repositories/agents/` | Obsidian project vault — see [`agents/AGENTS.md`](agents/AGENTS.md) |

## How we work

Most sessions start here. The typical flow:

1. **Identify the repo** — the work almost always touches a specific repo under
   this root. `ls ~/repositories` to orient.
2. **Small, self-contained task?** Work directly in the repo.
3. **Multi-ticket, cross-repo, or research-heavy task?** Open or create a
   project in the vault (`agents/projects/`). Use the scaffold script:
   ```bash
   bash ~/repositories/agents/scripts/new-project.sh <slug> [--tickets PROJ-1,PROJ-2]
   ```
4. Use the vault to store plans, investigations, decisions, and documents that
   shouldn't live in any single repo.

## Repos

Repos are cloned here as work begins. Add a row to this table for each repo
with a short description of its role in your stack.

| Repo | Description |
|---|---|
| *(none yet — clone repos here as you start working on them)* | |

## Conventions

- **Cloning** — always clone at the root of `~/repositories/`, not inside
  another repo or inside `agents/`.
- **Worktrees** — git worktrees live inside the repo they belong to, under the
  default `.claude/worktrees/` path (e.g.
  `~/repositories/<repo>/.claude/worktrees/<branch>`). Never create them
  as sibling directories at the workspace root — only full repo clones live
  there.
- **Secrets** — never put credentials, `.env` files, or tokens in the vault.
  The vault may be synced via Obsidian Sync.
- **Vault internals** — do not commit or modify `agents/.obsidian/`; it is
  managed by Obsidian.
- **Repo hygiene** — each repo manages its own `CLAUDE.md`/`AGENTS.md` for
  project-specific instructions.
