# Guidance for AI coding agents

This file is read by AI coding assistants (Claude Code and similar) working in this repository. Humans: see [CONTRIBUTING.md](CONTRIBUTING.md).

## What this project is

Reservoir preserves South African cultural knowledge (plants, practices, languages) on terms set by the people who hold it. Read [`docs/vision/principles.md`](docs/vision/principles.md) before making design decisions. **The principles outrank convenience.**

## Hard rules

1. **Never invent cultural or medicinal facts.** No made-up plant uses, names, translations, proverbs or practices — not in docs, tests, fixtures or seed data. Use clearly-marked placeholders (`status: example`) and cite real sources.
2. **Never put real community knowledge, personal data or secrets in the repo.** Test data must be synthetic.
3. **Consent is structural.** Do not add a code path that reads, returns, indexes, caches, exports or sends to a model any claim without evaluating its consent. Default to the most restrictive setting.
4. **No medical advice** in code, copy or prompts. Traditional use ≠ treatment.
5. **Do not make architectural decisions silently.** Anything affecting an ADR gets a new/updated ADR.
6. **Do not add dependencies** without noting licence and maintenance status in the PR.
7. **Language and orthography** belong to language custodians; do not "fix" indigenous-language strings without a custodian-reviewed source.

## Repository conventions

- Monorepo layout: `apps/`, `services/`, `packages/`, `data/`, `docs/` (see [ADR-0002](docs/adr/0002-monorepo.md)).
- Contracts first: change `packages/schemas` before the code that depends on it.
- Conventional Commits; sign off with `-s`.
- South African English spelling.
- Docs are Markdown, linted in CI.

## Stack (proposed — see ADRs)

Rust core API · Python agents/ML · Flutter mobile (pending benchmark) · TypeScript/Next.js web · PostgreSQL + SQLite.

## When unsure

Ask in the issue or PR. When a request touches consent, safety, language or community data, pause and ask a human maintainer rather than guessing.
