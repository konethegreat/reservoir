# ADR-0003: Polyglot stack with contract-first schemas

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

The founder wants modern, powerful, fast languages and is open to a multi-language approach. Different parts of Reservoir have genuinely different needs: a lean, safe, cheap-to-run core; the Python-dominated ML ecosystem; a mobile client for weak devices; SEO-friendly web pages. See [technology research](../research/tech-stack-research.md).

## Options considered

1. **Single language (TypeScript everywhere)** — simplest, biggest pool; weak for ML, heavier at runtime.
2. **Single language (Python everywhere)** — great for ML; poor for mobile and slow/heavy for the core.
3. **Polyglot, each language in its lane, bound by shared schemas.**

## Decision

| Area | Language |
|---|---|
| Core API & sync | Rust |
| Agents / ML | Python |
| Mobile | Dart (Flutter), see ADR-0004 |
| Web | TypeScript (Next.js) |
| Contracts | JSON Schema + OpenAPI, with generated types/clients for all of the above |

**Rule:** languages communicate only through versioned, schema-defined interfaces (HTTP/JSON, later gRPC if needed). No shared in-process FFI between areas unless an ADR justifies it.

## Consequences

- ✅ Each component uses the best tool; Rust gives a tiny hosting bill; Python gives ML velocity.
- ❌ Four toolchains to maintain; higher onboarding cost; need good dev-container/`make` ergonomics.
- ❌ Risk of schema drift → mitigated by codegen and CI checks that fail on drift.
- Contributors can work in whichever lane suits them; the core stays small.

## Validation

Track contributor onboarding time and CI complexity. If the polyglot cost outweighs benefits after Phase 1, consider collapsing the core to a simpler language — recorded as a superseding ADR.
