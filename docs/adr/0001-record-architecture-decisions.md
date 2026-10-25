# ADR-0001: Record architecture decisions

- **Status:** Accepted
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

Reservoir will be built by a changing group of volunteers over many years. Without a record of *why* things are the way they are, decisions get relitigated or silently reversed, and newcomers cannot tell what is deliberate.

## Options considered

1. Wiki pages — easy to edit, hard to review and version.
2. Ad-hoc comments in issues — lost over time.
3. **ADRs in the repository** — versioned, reviewable, discoverable.

## Decision

Use lightweight ADRs in `docs/adr/`, following the template, reviewed by pull request.

## Consequences

- A small overhead per significant decision.
- A durable, searchable history of reasoning.
- Proposed ADRs invite challenge — which is the point.
