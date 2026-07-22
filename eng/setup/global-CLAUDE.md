<!-- agents-vault-template:begin eng -->
# Engineering workspace — repos + project vault

<!--
  This is the GLOBAL instructions file for Claude Code. Copy it into
  ~/.claude/CLAUDE.md so Claude reads it at the start of EVERY session,
  no matter which folder you're working in.

  Keep the agents-vault-template:begin/end marker lines — they let setup
  (or Claude, via ONBOARDING.md) update this block in place later instead
  of appending a duplicate.

  Replace every <path> placeholder below with the vault folder you chose
  during setup.
-->

My engineering project vault lives at `<path>` — an Obsidian vault for
running **projects**: investigations, plans, decisions, and documents that
span tickets or repos. Source repos live in their own locations; the Repos
index in `<path>/AGENTS.md` maps each repo name to its path.

**At the start of every session, before substantive work:**

1. **Read** `<path>/AGENTS.md` (repos index + conventions + vault guide) if
   the session hasn't loaded it already — do this even when the working
   directory is elsewhere.
2. **Small, self-contained task?** Work directly in the repo.
3. **Multi-ticket, cross-repo, or research-heavy task?** Open or create a
   project in the vault:
   ```bash
   bash <path>/scripts/new-project.sh <slug> [--tickets PROJ-1,PROJ-2]
   ```
   and file investigations, plans, and decisions there as the work happens,
   following the vault guide's naming and frontmatter conventions.

**Distilled, not a transcript** — vault notes carry the conclusion, the
decision and why, the finding that matters; never a chat log. Code stays in its
repo; the vault only references it (`file:line`).
<!-- agents-vault-template:end eng -->
