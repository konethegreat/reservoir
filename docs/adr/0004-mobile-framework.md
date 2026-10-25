# ADR-0004: Mobile framework — Flutter, pending benchmark

- **Status:** Proposed *(conditional)*
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

The primary users have low-to-mid Android phones. The app needs a camera, audio recording, an offline database and on-device inference. iOS matters but is secondary. Contributor availability matters.

## Options considered

1. **Flutter** — one codebase, great tooling, strong plugin ecosystem, large community. Unknowns: footprint/performance on 2 GB devices.
2. **React Native (TypeScript)** — largest pool; shares language with web. Unknowns: performance on weak devices, native-module churn.
3. **Kotlin Multiplatform + Compose Multiplatform** — native-grade performance on Android; smaller community.
4. **Native Android first** — best performance; no iOS.

## Decision

Proceed with **Flutter** as the working hypothesis, **subject to a benchmark spike** (APK size, cold start, RAM, camera → on-device inference latency, scroll jank) on ≥ 2 Android Go–class devices against a minimal native/KMP baseline. If Flutter misses the budgets in [offline-sync](../architecture/offline-sync.md#size-and-performance-budgets-initial-targets-to-be-validated), the fallback is Kotlin Multiplatform.

## Consequences

- One mobile codebase and a large contributor base if it passes.
- Dart is a new language for many contributors.
- A deliberate pause before building app code: the spike is a Phase 0 deliverable.

## Validation

Spike results published in `docs/research/spikes/`; this ADR is accepted, amended or superseded based on them.
