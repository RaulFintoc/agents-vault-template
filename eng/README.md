# agents-vault-template

A barebones scaffold for a `~/repositories` workspace that pairs source-code
repos with an Obsidian vault for running structured **projects** — investigations,
plans, decisions, and documents — across multiple tickets.

---

## What this is

A clean starter with no real project data and no custom plugins. Clone it once
to bootstrap the workspace layout, then add your own repos and start creating
projects.

---

## Layout

```
repositories/              ← workspace root (a copy of this eng/ folder)
  AGENTS.md                ← workspace guide (cloning, conventions, how we work)
  CLAUDE.md                ← @AGENTS.md (Claude Code reads this)
  README.md                ← this file
  agents/                  ← Obsidian vault
    AGENTS.md              ← vault guide (file naming, frontmatter, linking, Mermaid)
    CLAUDE.md              ← @AGENTS.md
    templates/             ← note templates (project, investigation, plan, decision)
    scripts/
      new-project.sh       ← scaffold a new project folder
      archive.sh           ← archive finished projects into _archive/
    projects/              ← one folder per project (ships empty)
    .obsidian/             ← Obsidian config (core plugins only, default theme)
```

---

## Setup

1. **Copy this `eng/` folder** to become your workspace root:
   ```bash
   git clone --depth 1 https://github.com/RaulFintoc/agents-vault-template /tmp/agents-vault-template
   cp -R /tmp/agents-vault-template/eng ~/repositories
   rm -rf /tmp/agents-vault-template
   ```
   (Use a different target path if you keep your repos elsewhere, e.g.
   `~/work/repositories`.)

2. **Open the vault in Obsidian**: File → Open vault → select the `agents/`
   folder inside your clone.

3. **No community plugins required.** Only Obsidian core plugins are configured.
   Mermaid diagrams render natively.

4. **Point every Claude Code session at the workspace**: merge
   `setup/global-CLAUDE.md` into your `~/.claude/CLAUDE.md` (create the file
   with its contents if you don't have one). Keep the
   `agents-vault-template:begin/end` marker lines — they let a later setup
   update the block in place.

5. Optionally enable **Obsidian Sync** (Settings → Sync) to keep the vault
   backed up and in sync across machines.

---

## Usage

### Scaffold a project

```bash
bash agents/scripts/new-project.sh <slug>
bash agents/scripts/new-project.sh my-feature --tickets PROJ-1,PROJ-2
bash agents/scripts/new-project.sh my-feature --tickets PROJ-3 --linear https://linear.app/...
```

This creates `agents/projects/YYYY-MM-<slug>/` with subfolders
(`investigations/`, `plans/`, `decisions/`, `documents/`) and a pre-filled
`<slug>_project.md` overview.

### Archive a finished project

```bash
bash agents/scripts/archive.sh <project>            # name or unique substring
bash agents/scripts/archive.sh --dry-run <project>  # preview only
```

This marks the project `status: archived` and moves its folder to
`agents/_archive/`, where it stays searchable.

### Add a repo

Clone repos at the workspace root alongside `agents/`:

```bash
gh repo clone <org>/<repo>
```

Then update the Repos table in the top-level `AGENTS.md` with a one-line
description.

---

## Further reading

- **`AGENTS.md`** (workspace root) — how the workspace is organized, cloning
  conventions, and how to decide between working directly in a repo vs. opening
  a project in the vault.
- **`agents/AGENTS.md`** (vault) — full vault guide: folder structure, file
  naming, YAML frontmatter, Obsidian links/transclusion, Mermaid diagrams, and
  the project lifecycle (start → archive).

---

> `agents/projects/` ships empty by design. Add projects with `new-project.sh`.
