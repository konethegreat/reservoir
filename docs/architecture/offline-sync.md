# Offline-first and sync

*Status: proposed. Needs a sync prototype.*

## Why

Connectivity in rural South Africa is patchy and data is expensive. Elders recording knowledge may be in places with no signal for days. The phone must be a complete, local-first application.

## Approach

- **On device:** SQLite is the working database. The UI reads and writes locally; the network is an optimisation.
- **Server:** PostgreSQL is the system of record.
- **Sync:** a pull/push protocol over HTTPS, scoped to what the principal may see:
  - **Pull** — server sends changes since a cursor for: all `public` entries the user subscribes to (by region/language/plant set), plus `community` content the user is entitled to.
  - **Push** — device sends a queue of local mutations (new claims, consents, media), each with an idempotency key.
- **Media** — uploaded in resumable chunks, opportunistically on Wi-Fi by default; audio compressed (Opus) before upload.
- **Selective download** — "language packs" and "region packs" so users choose what to store.

## Conflict handling

Claims are **append-only and immutable**; edits create a new claim that `supersedes` the old one. That removes most conflicts by construction.

Remaining conflict classes:

| Class | Strategy |
|---|---|
| Two edits to the same claim | Both kept as competing versions; reviewer chooses; never silently last-write-wins |
| Consent tightened on one device, loosened on another | **Most restrictive wins** until a human resolves |
| Contributor revokes while another device pushes | Revocation wins; push is rejected and tombstoned |
| Entry merge/duplicate | Handled server-side by curators, with redirect records |

No CRDT is needed for claim bodies; consent fields use a "restrictive-monotonic" merge rule.

## Security on device

- Restricted tiers encrypted at rest with a key held in the OS keystore; `sacred` content is only synced to devices of its holders and never cached in shared locations.
- Remote wipe of cached restricted content on revocation (best effort; documented honestly).
- Photos have EXIF stripped before leaving the device unless the user opts in.

## Size and performance budgets (initial targets, to be validated)

| Item | Target |
|---|---|
| App install size | < 50 MB |
| Core knowledge pack (names + key claims for top species, one language) | < 20 MB |
| On-device ID model | < 25 MB |
| Cold start on a 2 GB Android Go phone | < 3 s |
| Data usage for typical weekly use | < 20 MB |

## Technology candidates

- **Drift** (SQLite for Dart) with a custom sync engine, *or* an off-the-shelf sync layer (e.g. PowerSync, ElectricSQL) — evaluate against our consent-aware model. Off-the-shelf engines often assume row-level permissions that map awkwardly onto per-claim consent; prototype before adopting. → [ADR-0007](../adr/0007-offline-first-sqlite-sync.md)

## Open questions

- Can we push sync-time policy evaluation into SQL (row-level security) efficiently enough?
- Peer-to-peer (Bluetooth/Wi-Fi Direct) sync for places with no connectivity at all?
- How to handle shared family devices?
