# Onboarding guide — instructions for Claude

You (Claude) are setting up a work vault from this repo for the user. The goal: a copy of one area kit in its home folder, the user's global Claude Code config pointing at it, and the vault open in Obsidian. The user may be non-technical — do the terminal work yourself, explain briefly as you go, and never assume they know git, paths, or editors.

## 0. Pick the area, the location, and the language

Three required inputs — collect all of them from the user before copying anything; none has a default.

**Area** — ask which kit fits their role if it isn't obvious from their request:

| Area | Kit |
|---|---|
| Engineering | `eng/` |
| Product | `product/` |

**Location** — ask **where the vault should live**. Never pick a location for them. Help a non-technical user turn their answer ("in my Documents", "with my repos") into one concrete folder path, and confirm it back. Whatever they choose is `<home>` everywhere below. These steps assume macOS.

**Language** — ask whether they want their vault notes in **English or Spanish**. Don't infer it from the conversation's language — ask explicitly.

After copying, personalize the kit: replace the `<home>` placeholders in the global config snippet with the chosen path, rewrite the example paths in the workspace and vault `AGENTS.md`s to match it, and set the `> **Vault language: …**` line at the top of `<home>/agents/AGENTS.md` to the chosen language.

## 1. Copy the kit into place

```bash
git clone --depth 1 https://github.com/RaulFintoc/agents-vault-template /tmp/agents-vault-template
cp -R /tmp/agents-vault-template/<area> <home>
rm -rf /tmp/agents-vault-template
```

- If the home folder **already exists**, stop and show the user what's there before touching anything — never overwrite. If it's a previous copy of the kit, offer to add only the missing files; otherwise ask for a different target path.
- The copy is intentionally **not** a git repo (no `.git` comes along) — don't `git init` it.
- The kit is the vault + guides only. For **eng**, the user's existing code repos stay exactly where they are — never move or reclone them; they get *recorded*, not relocated (see step 4).

## 2. Install the global Claude Code config

The kit ships its snippet at `<home>/setup/global-CLAUDE.md`, wrapped in `<!-- agents-vault-template:begin <area> -->` / `end` markers.

- No `~/.claude/CLAUDE.md` yet → create it with the snippet's full contents (`mkdir -p ~/.claude` first).
- File exists **without** this area's markers → append the snippet at the bottom, separated by a blank line. Never modify the user's existing content.
- File exists **with** this area's markers → replace everything between (and including) the markers with the new snippet.
- Replace the `<home>` placeholders inside the snippet with the chosen path before installing it — never install a block that still contains `<home>`.

## 3. Obsidian

- Check for it (`ls /Applications/Obsidian.app`). If missing, send the user to https://obsidian.md to download and install it (free), and wait.
- Then walk them through: open Obsidian → **Open folder as vault** → select the **`agents/` folder inside the copy** (not the home folder itself) → Open, and trust the vault if asked.

## 4. Verify and hand off

- List what was created: the home folder, the vault path, and the updated `~/.claude/CLAUDE.md` (show the marker block so they can find it later).
- Point them at the kit's `AGENTS.md` guides (workspace root and `agents/`) for everyday use.
- For **eng**, offer to fill the Repos table in `<home>/AGENTS.md` with the repos they already work on (name, path, one-line description) — that table is how future sessions find their code.
- Offer to scaffold their first project with `bash <home>/agents/scripts/new-project.sh <slug>` as a test run.

## Rules

- Don't push, publish, or create anything on GitHub — this is a local setup.
- Don't install anything beyond the steps above without asking.
- If a step fails twice, stop and explain instead of improvising around it.
