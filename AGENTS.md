# AGENTS.md

## Scope
- This repository stores open skills for agentic coding tools and is meant to be consumed with `bunx skills`.
- Treat `skills/` as the distributable source for this repository.
- Keep repo-local agent configuration out of the distributable skill tree unless it is intentionally part of a skill.
- Add nested `AGENTS.md` files only when a skill subtree needs different rules.

## Skill layout
- Store each skill in `skills/<skill-name>/`.
- Keep `SKILL.md` as the entry point for each skill.
- Keep OpenAI/Codex-facing metadata in `agents/openai.yaml` when a skill needs it.
- Put supplemental docs in `references/` only when `SKILL.md` references them.
- Keep the directory name and the `name:` field in `SKILL.md` aligned.

## Working commands
- Validate this repository as a local skills.sh-style source with `bunx skills add . --list`.
- Validate the distributable skill subtree with `bunx skills add ./skills --list`.
- Validate one skill directly with `bunx skills add ./skills/<skill-name> --list`.
- Inspect project-visible skills with `bunx skills list`.
- Inspect user-level global installs with `bunx skills list -g`.

## Editing expectations
- Keep skills concise, tool-facing, and resilient to upstream CLI/API changes.
- Prefer telling agents how to discover current behavior from the tool itself over duplicating manuals that will drift.
- Write `SKILL.md` bodies so they read well on skills.sh: clear purpose, when to use, source-of-truth guidance, and operational guardrails.
- Do not duplicate skills.sh's generated install block inside every skill unless the installation detail changes how the agent should use the skill.
- When a skill behavior changes, update `SKILL.md` and any referenced metadata in the same change.
