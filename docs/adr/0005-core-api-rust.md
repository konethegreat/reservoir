# ADR-0005: Core API in Rust

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

The core API enforces consent, serves sync, holds sensitive community data and must be cheap to host indefinitely. It is also the one component where a bug (e.g. a policy bypass) has serious human consequences.

## Options considered

Rust (axum/sqlx), Go, TypeScript (Node/Bun), Python (FastAPI). See [technology research](../research/tech-stack-research.md#backend-core).

## Decision

**Rust**, with axum, sqlx (compile-time-checked SQL), tower middleware, and OpenTelemetry. The consent/policy engine is modelled with the type system so illegal states (e.g. `sacred` + `ai_use=training_allowed`) are unrepresentable.

## Consequences

- ✅ Low memory/CPU → low cost; memory safety; strong guarantees around the sovereignty rules.
- ❌ Smaller contributor pool and slower iteration than Python/TS. Mitigations: keep the core small and well documented; invest in a good dev container; most feature work (agents, web, mobile) happens elsewhere; mentor newcomers.
- ❌ Hiring/volunteering friction → accepted trade-off.

## Validation

If by the end of Phase 1 core velocity is blocked by contributor availability, reconsider Go via a superseding ADR. The OpenAPI contract makes the implementation replaceable.
