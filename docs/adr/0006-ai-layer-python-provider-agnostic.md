# ADR-0006: Python, provider-agnostic AI layer

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

Reservoir needs agents, retrieval, speech and vision across 12+ languages, many of them low-resource. The model landscape changes monthly, vendor terms vary in compatibility with community data, and costs must stay low.

## Options considered

1. Single hosted LLM vendor, direct SDK use everywhere.
2. Single open-weight model self-hosted.
3. **A model gateway that routes per task, per language and per data tier across hosted, open-weight and on-device models.**

## Decision

- Implement the agent fleet in **Python** in `services/agents`.
- All model calls go through a **gateway** that: filters context by `ai_use`/visibility, routes by task and language, logs, budgets, and can swap providers without agent changes.
- The **orchestrator is deterministic workflow code**; LLMs supply judgement inside steps.
- **Evaluation harness** is part of the codebase and gates changes.

## Consequences

- ✅ Best-model-per-language, vendor independence, privacy enforced in one place.
- ✅ Python ecosystem for speech/vision/evals.
- ❌ Gateway is more work than calling one SDK; routing quality depends on our evals.
- ❌ Two runtimes (Rust core, Python agents) → clear API boundary and OpenTelemetry tracing needed.

## Validation

Per-language quality scorecards; cost per active user; zero incidents of `ai_use` violations in red-team tests.
