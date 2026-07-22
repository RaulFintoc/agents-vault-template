# agents-vault-template

Starter kits for running your work with **Claude Code** and an **Obsidian vault** — one self-contained template per area. Pick the folder that matches your role, copy it to its home, and follow that folder's own `README.md`.

| Area | Folder | Made for |
|---|---|---|
| **Engineering** | [`eng/`](eng/) | Code repos + a vault of investigations, plans, and decisions across tickets |
| **Product** | [`product/`](product/) | Specs, research, roadmap reviews, strategy, and meeting notes — no coding tools needed |

Where a kit lives is up to you — you pick the folder during setup; the docs call it `<home>`.

## Easiest setup — let Claude do it

If you already have [Claude Code](https://docs.claude.com/en/docs/claude-code) installed, skip the manual steps entirely: open Terminal, run `claude`, and paste

> Set me up with the **product** vault from https://github.com/RaulFintoc/agents-vault-template — fetch its ONBOARDING.md and follow it.

(or **eng** for the engineering kit). Claude copies the kit to its home, updates your global `~/.claude/CLAUDE.md` so every future session knows about the vault, and walks you through opening it in Obsidian.

## Manual setup

First decide where the kit should live — any folder path works. Replace `<home>` below with the path you chose:

```bash
git clone --depth 1 https://github.com/RaulFintoc/agents-vault-template /tmp/agents-vault-template

# Engineering:
cp -R /tmp/agents-vault-template/eng <home>

# Product:
cp -R /tmp/agents-vault-template/product <home>

rm -rf /tmp/agents-vault-template
```

Then open the copied folder's `README.md` and follow its setup steps (installing Obsidian, opening the vault, wiring up Claude Code).

## What's in a template

Each area folder is a complete kit: an `agents/` Obsidian vault (guide, note templates, scaffolding scripts, minimal `.obsidian/` config), workspace-level `AGENTS.md`/`CLAUDE.md` instructions that Claude Code reads automatically, and a `README.md` with the full setup walkthrough. The templates share the same core ideas — work is organized in **projects**, notes carry YAML frontmatter, wikilinks connect them — but each is tuned to its area's workflow and deliverables.

Notes default to **English**; each vault's language is a one-line setting (English or Spanish) at the top of its `agents/AGENTS.md`.

## Adding an area

Want a vault for another area (design, ops, data)? Copy the closest existing folder, adapt its project types, templates, and guides, and open a PR adding it here.

## Credits

The `product/` template was authored by [@dmelberg](https://github.com/dmelberg) (imported from [dmelberg/product-vault-template](https://github.com/dmelberg/product-vault-template)).
