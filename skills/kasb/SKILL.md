---
name: kasb
description: Use the KASB CLI for read-only Korean accounting standards and KASB Q&A search and retrieval. Use when the user asks about Korean accounting standards, K-IFRS/KASB standard text, standard section structures, paragraph lookup, KASB Q&A documents, or source-backed Korean accounting reference material and wants current data through the kasb command-line tool.
---

# KASB

KASB gives agents read-only access to Korean Accounting Standards Board standards and Q&A materials through a command-line interface.

## When to Use This Skill

Use this skill when the user needs to search, inspect, or summarize KASB source material, including:

- Korean accounting standard searches
- K-IFRS/KASB standard structures, sections, or paragraphs
- paragraph lookup by standard number and paragraph number
- KASB Q&A searches or document lookup
- current accounting-reference evidence that should come from KASB rather than memory

## What is KASB?

KASB is a read-only CLI that turns public KASB standards and Q&A screens into structured JSON output that agents can inspect, summarize, and cite in follow-up work.

The CLI source is available in this workspace at `../kasb` when that sibling checkout exists. The CLI is published on npm as `@sjunepark/kasb` and exposes the `kasb` command.

## Installing or Finding KASB

When the sibling checkout exists, inspect the local source version first:

```sh
cd ../kasb && bun run src/cli.ts --help
```

Prefer the npm distribution when Node is available and the local checkout is unavailable:

```sh
npx @sjunepark/kasb --help
```

If the user wants a persistent install and Node/npm are available, install from the npm registry:

```sh
npm install -g @sjunepark/kasb
```

The npm package requires Node.js 20.18.1 or newer.

## Source of Truth

Do not treat this skill as the KASB command manual. KASB changes frequently, so the CLI's own help output is the source of truth for available commands, options, required inputs, and output shape.

When using this skill:

- Prefer the local sibling checkout at `../kasb` when it is available in the workspace.
- Otherwise use the installed or package-runner KASB CLI from npm package `@sjunepark/kasb` when Node/npm are available.
- Start by asking KASB itself for help, then inspect the help for any relevant command before running a real query.
- Do not assume a command, option, or field exists just because it existed in a previous session.
- Keep queries read-only and as narrow as the user's request allows.

## Working Style

- Use the CLI output as evidence; do not invent KASB results from memory.
- Preserve important query inputs in the answer, such as standard numbers, paragraph numbers, section identifiers, Q&A document numbers, keywords, titles, and warnings.
- Summarize results in the user's language when possible, but keep exact standard names, identifiers, paragraph references, Q&A document numbers, and warnings intact.
- Make clear that the CLI provides source-reference material, not accounting, legal, tax, investment, or audit advice.
- If KASB reports warnings, partial content, truncation, missing sections, or upstream source issues, surface that limitation.
- If the available help output does not expose a path for the requested task, say so and explain what information is missing.
