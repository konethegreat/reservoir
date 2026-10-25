# ADR-0002: Single monorepo

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

Reservoir has several deployables (mobile, web, API, agents) sharing schemas and a governance model that must change *atomically* with code (e.g. a consent-field change touches all of them). The project is small; coordination cost dominates.

## Options considered

1. **Polyrepo** — clean ownership, but schema drift, cross-repo PRs, fragmented issue tracking and community.
2. **Monorepo** — one place for issues, docs, governance and atomic changes; needs per-area tooling and CI path filters.

## Decision

One public monorepo: `apps/`, `services/`, `packages/`, `data/`, `docs/`. Each area has its own README, toolchain and CI job, triggered by path filters. Language-native tooling per area (Cargo, pub, pnpm, uv) — no heavy monorepo build system until it hurts.

## Consequences

- One issue tracker, one governance surface — good for a community project.
- CI must be path-filtered to stay fast.
- Large binary/media or dataset files do **not** live in git (object storage / Git LFS where unavoidable).
- Real community data never lives in the repository (see `.gitignore`, `data/README.md`).

## Validation

Revisit if CI time or contributor friction grows materially, or if an area needs an independent release cadence or access policy.
