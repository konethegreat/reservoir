# ADR-0007: Offline-first with SQLite and custom sync

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

Patchy connectivity and expensive data make offline-first a core requirement. Sync must respect per-claim consent and visibility ([ADR-0008](0008-knowledge-sovereignty-model.md)).

## Options considered

1. **Online-only with caching** — simple; fails the mission.
2. **Off-the-shelf sync engine** (PowerSync, ElectricSQL, etc.) — fast to adopt; permission models are usually row-level and may not map onto per-claim consent and "most-restrictive-wins" merging.
3. **Custom pull/push sync over append-only claims** — more work; fits the model precisely.

## Decision

SQLite on device; PostgreSQL on server; **custom cursor-based pull/push sync** over append-only, immutable claims, with restrictive-monotonic consent merging. Evaluate an off-the-shelf engine in a time-boxed spike first; adopt it only if it can express our consent rules without leaking restricted content.

## Consequences

- ✅ Few conflicts by construction; consent semantics preserved.
- ❌ We own sync correctness — needs strong property-based tests.

## Validation

Sync prototype with simulated intermittent connectivity and revocation races; no restricted-claim leakage in tests.
