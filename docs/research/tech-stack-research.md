# Technology research

*Status: desk research, October 2026. Nothing here is validated by running code yet. Decisions live in the [ADRs](../adr/README.md); this page records the reasoning and the evidence still needed.*

## Constraints that drive the stack

1. **Target devices:** low-to-mid Android phones (2–4 GB RAM), patchy connectivity, expensive data. iOS is secondary at first.
2. **Funding:** the app is free forever — hosting and inference must be cheap. Every watt and megabyte matters.
3. **Contributors:** an open-source project of volunteers and students; the stack must be learnable and the toolchain approachable.
4. **AI/ML:** Python ecosystem is unavoidable for model work; mobile inference needs a compact runtime.
5. **Trust:** memory-safe, auditable core for a system that holds sensitive community data.
6. **Longevity:** this is meant to last decades; prefer boring, well-supported foundations for the data layer.

## Mobile client

| Option | For | Against |
|---|---|---|
| **Flutter (Dart)** | Single codebase Android/iOS/(web/desktop); own renderer gives consistent UI; strong plugin ecosystem for camera, audio, SQLite, TFLite/LiteRT; large community | Self-rendered UI adds binary size/memory (no measured data for low-end phones); Dart is a niche language outside Flutter |
| **React Native (TypeScript)** | Huge JS/TS contributor pool; native components; share code with the Next.js web app | Bridge/JS overhead on weak devices (improved by the new architecture); native-module churn |
| **Kotlin Multiplatform + Compose** | Native performance, shared logic, first-class Android; good fit for on-device ML | Smaller community; iOS UI maturity; fewer volunteers know it |
| **Native Android only** | Best performance and size | Excludes iOS; halves contributor leverage |
| **PWA** | Zero install, instant updates | Weak offline/camera/background capabilities; poor discoverability on Play Store |

Directional sources: [KMP 2026 overview](https://jetruby.com/blog/kotlin-multiplatform-2026), [React Native vs Flutter 2026](https://idealogic.io/blog/react-native-vs-flutter), [framework survey](https://hyscaler.com/insights/mobile-app-development-platforms/). These are vendor-flavoured; none tested budget Android or South African conditions.

**Working choice: Flutter**, **conditional on a benchmark spike** (cold start, RAM, APK size, camera + on-device inference latency) on at least two Android Go–class devices vs a minimal Kotlin baseline. If Flutter fails the spike, fall back to Kotlin Multiplatform. → [ADR-0004](../adr/0004-mobile-framework.md)

## Backend core

| Option | Notes |
|---|---|
| **Rust (axum + sqlx)** | Small memory footprint and high throughput → cheap hosting; memory safety for sensitive data; excellent type system for modelling consent rules. Steeper learning curve, smaller contributor pool. |
| **Go** | Simple, fast, easy to learn, great ops story. Weaker type-level modelling. |
| **TypeScript (Node/Bun)** | Largest pool; share types with web. Higher memory, weaker guarantees. |
| **Python (FastAPI)** | Fastest to prototype; shares language with ML. Slower, heavier. |

**Working choice: Rust** for the API/sync core, with the explicit trade-off of a smaller contributor pool. Mitigated by keeping the core small, well documented, and by letting contributors work in Python, TypeScript and Dart for most features. → [ADR-0005](../adr/0005-core-api-rust.md)

## Intelligence layer

- **Python** for agents, retrieval, evaluation, speech and vision pipelines.
- **Provider-agnostic model gateway:** frontier hosted models for hard reasoning *where records permit*; open-weight models for low-resource-language tasks and privacy-sensitive paths; tiny on-device models for the camera.
- **Retrieval-augmented generation over the consented knowledge base** with mandatory citations; no free-form generation of cultural claims.
- **Evaluation harness** as a first-class component.

→ [ADR-0006](../adr/0006-ai-layer-python-provider-agnostic.md)

## Data layer

- **PostgreSQL** (+ **PostGIS** for locations and range/blurring, + **pgvector** for semantic search). One boring, reliable database beats a zoo.
- **SQLite on device**, synced to the server (offline-first). → [ADR-0007](../adr/0007-offline-first-sqlite-sync.md)
- **S3-compatible object storage** for images and audio (with signed URLs, tiered access).
- **Append-only provenance/audit log** so every change is attributable and reversible.

## Web

- **TypeScript + Next.js** for public discovery pages (SEO matters: people search for "umhlonyane uses"), curator dashboards and admin. → [ADR-0003](../adr/0003-polyglot-stack.md)

## Shared contracts

- **OpenAPI** for the REST API, **JSON Schema** for the knowledge model, code-generated clients for Dart, TypeScript and Python. One schema, three languages, zero drift.

## Infra and ops

- Containers (Docker) and a simple deploy target first; avoid premature Kubernetes.
- Infrastructure as code (OpenTofu) once more than one environment exists.
- Observability: OpenTelemetry from day one.
- Host in or near South Africa for latency and data-residency comfort (POPIA considerations). Provider TBD.

## Spikes required before Phase 1 begins

1. **Mobile benchmark** — Flutter vs Kotlin baseline on low-end Android.
2. **Plant-ID accuracy** — candidate APIs and models against a South African test set.
3. **On-device model** — smallest acceptable model size/latency/accuracy.
4. **Sync prototype** — two devices, intermittent connectivity, conflict scenarios.
5. **Speech baseline** — ASR quality for at least isiZulu and Tshivenda.

Each spike gets an issue and a short write-up in `docs/research/spikes/`.
