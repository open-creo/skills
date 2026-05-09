# open-creo

Open skills for agentic coding tools, distributed through the Skills CLI and readable on skills.sh.

## Install

Public install command, matching the style skills.sh displays:

```bash
npx skills add https://github.com/sjunepark/open-creo --skill darty
```

For local development before the repository is published or indexed:

```bash
npx skills add . --list
npx skills add . --skill darty
```

`bunx skills ...` works too if you prefer Bun.

skills.sh generates the skill page's install command from the GitHub source and skill name. This README keeps the canonical command visible for people browsing the repository directly.

## Skills

### darty

Use the Darty CLI for read-only Korean DART disclosure search and retrieval. The CLI is published on npm as `@sjunepark/darty`; agents should inspect Darty's own help output for current commands, menus, options, and output shape instead of relying on a copied manual in this repository.

Learn more after indexing: <https://skills.sh/sjunepark/open-creo/darty>

## Layout

- `skills/` is the installable skill source.
- Each skill lives at `skills/<skill-name>/SKILL.md`.
