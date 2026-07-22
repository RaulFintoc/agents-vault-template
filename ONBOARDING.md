# Onboarding guide — instructions for Claude

You (Claude) are setting up a work vault from this repo for the user. The goal: a copy of one area kit at the user's chosen path, the user's global Claude Code config pointing at it, and the vault open in Obsidian. The user may be non-technical — do the terminal work yourself, explain briefly as you go, and never assume they know git, paths, or editors.

## 0. Pick the area, the path, and the language

Three required inputs — collect all of them from the user before copying anything; none has a default.

**Area** — ask which kit fits their role if it isn't obvious from their request:

| Area | Kit | Vault folder after copy |
|---|---|---|
| Engineering | `eng/` | `<path>` itself — the kit folder **is** the vault |
| Product | `product/` | `<path>/agents` — the kit folder contains the vault |

**Path** — ask **where the vault should live, including the folder's name** (both are theirs to pick). Never choose either for them. Help a non-technical user turn their answer ("in my Documents", "with my repos") into one concrete folder path, and confirm it back. Whatever they choose is `<path>` everywhere below. These steps assume macOS.

**Language** — ask whether they want their vault notes in **English or Spanish**. Don't infer it from the conversation's language — ask explicitly.

After copying, personalize the kit: replace the `<path>` placeholders in the kit's `AGENTS.md`(s) and global config snippet with the chosen path, rewrite any remaining example paths to match it, and set the `> **Vault language: …**` line at the top of the vault `AGENTS.md` to the chosen language.

## 1. Copy the kit into place

```bash
git clone --depth 1 https://github.com/RaulFintoc/agents-vault-template /tmp/agents-vault-template
cp -R /tmp/agents-vault-template/<area> <path>
rm -rf /tmp/agents-vault-template
```

- If the target folder **already exists**, stop and show the user what's there before touching anything — never overwrite. If it's a previous copy of the kit, offer to add only the missing files; otherwise ask for a different path.
- The copy is intentionally **not** a git repo (no `.git` comes along) — don't `git init` it.
- The kit is the vault + guides only. For **eng**, the user's existing code repos stay exactly where they are — never move or reclone them; they get *recorded*, not relocated (see step 4).

## 2. Install the global Claude Code config

The kit ships its snippet at `<path>/setup/global-CLAUDE.md`, wrapped in `<!-- agents-vault-template:begin <area> -->` / `end` markers.

- No `~/.claude/CLAUDE.md` yet → create it with the snippet's full contents (`mkdir -p ~/.claude` first).
- File exists **without** this area's markers → append the snippet at the bottom, separated by a blank line. Never modify the user's existing content.
- File exists **with** this area's markers → replace everything between (and including) the markers with the new snippet.
- Replace the `<path>` placeholders inside the snippet with the chosen path before installing it — never install a block that still contains `<path>`.

## 3. Obsidian

- Check for it (`ls /Applications/Obsidian.app`). If missing, send the user to https://obsidian.md to download and install it (free), and wait.
- Then walk them through: open Obsidian → **Open folder as vault** → select the vault folder from the area table (**eng**: `<path>` itself; **product**: the `agents/` folder inside `<path>`) → Open, and trust the vault if asked.

## 4. Verify and hand off

- List what was created: the vault path and the updated `~/.claude/CLAUDE.md` (show the marker block so they can find it later).
- Point them at the kit's `AGENTS.md` guide(s) for everyday use.
- For **eng**, offer to fill the Repos index at the top of `<path>/AGENTS.md` with the repos they already work on (name, path, one-line description) — that index is how future sessions find their code.
- Offer to scaffold their first project as a test run (**eng**: `bash <path>/scripts/new-project.sh <slug>`; **product**: `bash <path>/agents/scripts/new-project.sh <slug>`).

## Rules

- Don't push, publish, or create anything on GitHub — this is a local setup.
- Don't install anything beyond the steps above without asking.
- If a step fails twice, stop and explain instead of improvising around it.
