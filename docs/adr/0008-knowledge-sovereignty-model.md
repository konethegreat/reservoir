# ADR-0008: Per-claim consent as the core data model

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

Reservoir holds knowledge that belongs to communities and individuals. Consent, attribution, visibility and AI-use cannot be features added later; they shape the schema, sync, search, caching and AI layers.

## Options considered

1. **Per-entry permissions** — simple, too coarse (a plant's name may be public while a remedy is community-only).
2. **Per-user ACLs** — flexible but unmanageable for collective knowledge.
3. **Per-claim consent with community/custodian roles, enforced in the data layer.**

## Decision

Model knowledge as **claims**, each with a mandatory **source** and **consent** (visibility, attribution, `ai_use`, redistribution, TK labels). Enforce in the Core API policy engine, PostgreSQL row-level security (defence in depth), the sync layer and the model gateway. Defaults are the most restrictive. See [knowledge sovereignty](../architecture/knowledge-sovereignty.md) and [data model](../architecture/data-model.md).

## Consequences

- ✅ Fine-grained control that communities can trust; AI constrained structurally.
- ❌ More schema and more UX complexity; consent UI must be simple enough for low-literacy and voice-first users.
- ❌ Performance cost of policy checks; mitigated by indexes per visibility tier.
- Legal review required before launch.

## Validation

Policy rules tested like security properties; user-testing of consent UX with knowledge holders and custodians; legal sign-off.
