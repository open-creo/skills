# skills

Open skills for agentic coding tools, distributed through the Skills CLI and readable on skills.sh.

## Install

Public install command, matching the style skills.sh displays:

```bash
npx skills add open-creo/skills --skill darty
npx skills add open-creo/skills --skill kasb
npx skills add open-creo/skills --skill landprice
npx skills add open-creo/skills --skill tool-surface-spec
```

For local development before the repository is published or indexed:

```bash
npx skills add . --list
npx skills add . --skill darty
npx skills add . --skill kasb
npx skills add . --skill landprice
npx skills add . --skill tool-surface-spec
```

`bunx skills ...` works too if you prefer Bun.

skills.sh generates the skill page's install command from the GitHub source and skill name. This README keeps the canonical command visible for people browsing the repository directly.

## Skills

### darty

Use the Darty CLI for read-only Korean DART disclosure search and retrieval. The CLI is published on npm as `@sjunepark/darty`; agents should inspect Darty's own help output for current commands, menus, options, and output shape instead of relying on a copied manual in this repository.

Learn more on skills.sh: <https://skills.sh/open-creo/skills/darty>

### kasb

Use the KASB CLI for read-only Korean accounting standards and KASB Q&A search and retrieval. The CLI is published on npm as `@sjunepark/kasb`; agents should inspect KASB's own help output for current commands, options, and output shape instead of relying on a copied manual in this repository.

Learn more on skills.sh: <https://skills.sh/open-creo/skills/kasb>

### landprice

Use the Landprice CLI for read-only Korean official land price lookup from RealtyPrice/부동산공시가격 알리미. The CLI is published on npm as `@sjunepark/landprice`; agents should inspect Landprice's own help output for current commands, options, and output shape instead of relying on a copied manual in this repository.

Learn more on skills.sh: <https://skills.sh/open-creo/skills/landprice>

### tool-surface-spec

Use the Tool Surface Spec skill to design, review, scaffold, or validate reusable agent-tool packages with a CLI, runtime-neutral TypeScript toolset SDK, and Pi adapter over one deterministic capability core.

Learn more on skills.sh: <https://skills.sh/open-creo/skills/tool-surface-spec>

## Layout

- `skills/` is the installable skill source.
- Each skill lives at `skills/<skill-name>/SKILL.md`.
