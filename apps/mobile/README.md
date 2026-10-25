# apps/mobile

Offline-first mobile app (Android first). **Not started** — blocked on the mobile benchmark spike ([ADR-0004](../../docs/adr/0004-mobile-framework.md)).

Planned: Flutter · Drift/SQLite · LiteRT on-device model · Opus audio capture · generated API client from [`packages/schemas`](../../packages/schemas).

Budgets (to validate): install < 50 MB · cold start < 3 s on a 2 GB device · weekly data < 20 MB. See [offline-sync](../../docs/architecture/offline-sync.md).
