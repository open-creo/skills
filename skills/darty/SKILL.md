---
name: darty
description: Use the Darty CLI for read-only Korean DART disclosure search and retrieval. Use when the user asks about Korean corporate filings, DART disclosures, listed-company reports, filing body searches, company disclosure histories, company profiles, or report sections and wants current data through the Darty command-line tool.
---

# Darty

Darty gives agents read-only access to Korean DART disclosure data through a command-line interface.

## When to Use This Skill

Use this skill when the user needs to search, inspect, or summarize Korean corporate disclosures from DART, including:

- filing body searches
- company disclosure histories
- company profiles or identifiers
- report tables of contents, sections, or receipt-number based report lookup
- current filing evidence that should come from DART rather than memory

## What is Darty?

Darty is a read-only tool that turns DART disclosure search and report-viewing screens into structured output that agents can inspect, summarize, and cite in follow-up work.

The CLI source is available in this workspace at `../darty` when that sibling checkout exists. The CLI is published on npm as `@sjunepark/darty` and exposes the `darty` command. The package also provides reusable integration entry points, but agents should prefer the CLI unless the host environment explicitly needs a package API.

## Installing or Finding Darty

When the sibling checkout exists, inspect the local source version first:

```sh
cd ../darty && bun run src/cli.ts --help
```

Prefer the npm distribution when Node is available and the local checkout is unavailable:

```sh
npx @sjunepark/darty --help
```

If the user wants a persistent install and Node/npm are available, install from the npm registry:

```sh
npm install -g @sjunepark/darty
```

The npm package requires Node.js 20.18.1 or newer.

## Source of Truth

Do not treat this skill as the Darty command manual. Darty changes frequently, so the CLI's own help output is the source of truth for available menus, commands, options, required inputs, and output shape.

When using this skill:

- Prefer the local sibling checkout at `../darty` when it is available in the workspace.
- Otherwise use the installed or package-runner Darty CLI from npm package `@sjunepark/darty` when Node/npm are available.
- Start by asking Darty itself for help, then inspect the help for any relevant menu or command before running a real query.
- Do not assume a command, option, or field exists just because it existed in a previous session.
- Keep queries read-only and as narrow as the user's request allows.

## Working Style

- Use the CLI output as evidence; do not invent DART results from memory.
- Preserve important query inputs in the answer, such as company names, company codes, keywords, dates, report names, or receipt numbers.
- Summarize results in the user's language when possible, but keep exact filing names, dates, identifiers, and warnings intact.
- If Darty reports warnings, partial content, truncation, missing sections, or upstream DART issues, surface that limitation.
- If the available help output does not expose a path for the requested task, say so and explain what information is missing.
