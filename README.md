# agents-vault-template

Starter kits for running your work with **Claude Code** and an **Obsidian vault** — one self-contained template per area. Pick the folder that matches your role and set it up with the steps below.

| Area | Folder | Made for |
|---|---|---|
| **Engineering** | [`eng/`](eng/) | A vault of investigations, plans, and decisions across tickets — pairs with your code repos, wherever they live |
| **Product** | [`product/`](product/) | Specs, research, roadmap reviews, strategy, and meeting notes — no coding tools needed |

Where a kit lives is up to you — you pick the folder during setup; the docs call it `<home>`.

## Easiest setup — let Claude do it

If you already have [Claude Code](https://docs.claude.com/en/docs/claude-code) installed, skip the manual steps entirely: open Terminal, run `claude`, and paste

> Set me up with the **product** vault from https://github.com/RaulFintoc/agents-vault-template — fetch its ONBOARDING.md and follow it.

(or **eng** for the engineering kit). Claude asks where you want the kit, copies it there, updates your global `~/.claude/CLAUDE.md` so every future session knows about the vault, and walks you through opening it in Obsidian.

## Manual setup

> **Terminal?** It's a built-in Mac app. Open it by pressing `Cmd + Space`, typing `Terminal`, and pressing `Enter`. You'll paste commands into it and press `Enter` to run them.

1. **Choose where the kit will live.** Any folder path works. Write the full path down — the steps below call it `<home>`, and you replace `<home>` with your path wherever it appears.

2. **Download the kit and put the copy in place:**

   ```bash
   git clone --depth 1 https://github.com/RaulFintoc/agents-vault-template /tmp/agents-vault-template

   # Engineering:
   cp -R /tmp/agents-vault-template/eng <home>
   # Product:
   cp -R /tmp/agents-vault-template/product <home>

   rm -rf /tmp/agents-vault-template
   ```

3. **Open the vault in Obsidian.** Install Obsidian (free) from https://obsidian.md, choose **"Open folder as vault"**, and select the **`agents/` folder inside `<home>`** (not `<home>` itself — the vault is the `agents` subfolder). Trust the vault if asked. No community plugins are required; Mermaid diagrams render natively.

4. **Install Claude Code** following https://docs.claude.com/en/docs/claude-code, then check it worked with `claude --version`.

5. **Install the global config** so every Claude Code session knows about the vault: merge `<home>/setup/global-CLAUDE.md` into `~/.claude/CLAUDE.md` (no file yet? `mkdir -p ~/.claude`, then create it with the snippet's contents; already have one? paste the snippet at the bottom — don't overwrite). Replace every `<home>` placeholder inside with your path, and keep the `agents-vault-template:begin/end` marker lines — they let a later setup update the block in place.

6. **Personalize the guides**: the copied `AGENTS.md` files reference the workspace by example paths — find-and-replace them with your path (or ask Claude to do it).

7. Optionally enable **Obsidian Sync** (Settings → Sync) to keep the vault backed up and in sync across machines.

## Everyday use

```bash
cd <home>
claude
```

Tell Claude what you're working on — it files the substantive output (findings, decisions, plans, deliverables) into the right project following the vault's conventions. The full guide for your kit — folder structure, project types, scaffolding scripts, naming, frontmatter — is `<home>/agents/AGENTS.md`; you can read it right inside Obsidian.

## What's in a template

Each area folder is a complete kit: an `agents/` Obsidian vault (guide, note templates, scaffolding scripts, minimal `.obsidian/` config), workspace-level `AGENTS.md`/`CLAUDE.md` instructions that Claude Code reads automatically, and a `setup/global-CLAUDE.md` snippet for your global config. The templates share the same core ideas — work is organized in **projects**, notes carry YAML frontmatter, wikilinks connect them — but each is tuned to its area's workflow and deliverables.

Notes default to **English**; each vault's language is a one-line setting (English or Spanish) at the top of its `agents/AGENTS.md`.

## Adding an area

Want a vault for another area (design, ops, data)? Copy the closest existing folder, adapt its project types, templates, and guides, and open a PR adding it here.

## Credits

The `product/` template was authored by [@dmelberg](https://github.com/dmelberg) (imported from [dmelberg/product-vault-template](https://github.com/dmelberg/product-vault-template)).
