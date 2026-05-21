---
name: landprice
description: Use the Landprice CLI for read-only Korean official land price lookup. Use when the user asks about Korean standard land prices, individual publicly announced land prices, RealtyPrice/부동산공시가격 알리미 land-price data, area or legal-dong code discovery, parcel-based land price lookup, or source-backed Korean land-price evidence through the landprice command-line tool.
---

# Landprice

Landprice gives agents read-only access to Korean official land price data from RealtyPrice/부동산공시가격 알리미 through a JSON command-line interface.

## When to Use This Skill

Use this skill when the user needs to search, inspect, or summarize Korean land-price source material, including:

- standard land prices (표준지 공시지가)
- individual publicly announced land prices (개별공시지가)
- parcel-based land-price lookup
- area, district, or legal-dong code discovery needed by the source site
- current land-price evidence that should come from RealtyPrice rather than memory

## What is Landprice?

Landprice is a read-only CLI for Korean official land prices. It uses public RealtyPrice web behavior and returns tool-friendly JSON that agents can inspect, summarize, and cite in follow-up work.

The CLI source is available in this workspace at `../landprice` when that sibling checkout exists. The CLI is published on npm as `@sjunepark/landprice` and exposes the `landprice` command.

Landprice is not a government-provided official API package. RealtyPrice website changes can affect results or parsing.

## Installing or Finding Landprice

When the sibling checkout exists, inspect the local source version first:

```sh
cd ../landprice && bun run src/cli.ts --help
```

Prefer the npm distribution when Node is available and the local checkout is unavailable:

```sh
npx @sjunepark/landprice --help
```

If the user wants a persistent install and Node/npm are available, install from the npm registry:

```sh
npm install -g @sjunepark/landprice
```

The npm package requires Node.js 20.18.1 or newer.

## Source of Truth

Do not treat this skill as the Landprice command manual. Landprice can change, so the CLI's own help output is the source of truth for available commands, options, required inputs, and output shape.

When using this skill:

- Prefer the local sibling checkout at `../landprice` when it is available in the workspace.
- Otherwise use the installed or package-runner Landprice CLI from npm package `@sjunepark/landprice` when Node/npm are available.
- Start by asking Landprice itself for help, then inspect the help for any relevant command before running a real query.
- Do not assume a command, option, or field exists just because it existed in a previous session.
- Keep queries read-only and as narrow as the user's request allows.

## Working Style

- Use the CLI output as evidence; do not invent RealtyPrice results from memory.
- Preserve important query inputs in the answer, such as years, address text, district codes, legal-dong codes, parcel numbers, surface/type choices, and source references.
- Summarize results in the user's language when possible, but keep exact addresses, parcel identifiers, years, price values, source references, and warnings intact.
- Make clear that the CLI provides source-reference material, not legal, tax, appraisal, audit, or investment advice.
- If Landprice reports warnings, partial content, truncation, missing records, or upstream source issues, surface that limitation.
- If the available help output does not expose a path for the requested task, say so and explain what information is missing.
