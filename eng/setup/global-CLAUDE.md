<!-- agents-vault-template:begin eng -->
# Engineering workspace — repos + project vault

<!--
  This is the GLOBAL instructions file for Claude Code. Copy it into
  ~/.claude/CLAUDE.md so Claude reads it at the start of EVERY session,
  no matter which folder you're working in.

  Keep the agents-vault-template:begin/end marker lines — they let setup
  (or Claude, via ONBOARDING.md) update this block in place later instead
  of appending a duplicate.

  If you placed the workspace somewhere other than ~/repositories, change
  the paths below to match.
-->

My engineering workspace lives at `~/repositories`: source repos are cloned at
its root, and `~/repositories/agents/` is an Obsidian vault for running
**projects** — investigations, plans, decisions, and documents that span
tickets or repos.

**At the start of every session, before substantive work:**

1. **Read** `~/repositories/AGENTS.md` (workspace conventions) and
   `~/repositories/agents/AGENTS.md` (vault guide) if the session hasn't
   loaded them already — do this even when the working directory is elsewhere.
2. **Small, self-contained task?** Work directly in the repo.
3. **Multi-ticket, cross-repo, or research-heavy task?** Open or create a
   project in the vault:
   ```bash
   bash ~/repositories/agents/scripts/new-project.sh <slug> [--tickets PROJ-1,PROJ-2]
   ```
   and file investigations, plans, and decisions there as the work happens,
   following the vault guide's naming and frontmatter conventions.

**Distilled, not a transcript** — vault notes carry the conclusion, the
decision and why, the finding that matters; never a chat log. Code stays in its
repo; the vault only references it (`file:line`).
<!-- agents-vault-template:end eng -->
