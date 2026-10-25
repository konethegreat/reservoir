# Licensing

*Status: proposed — see [ADR-0009](../adr/0009-licensing.md). Not legal advice; counsel review pending.*

| What | Licence | Notes |
|---|---|---|
| **Source code** (`apps/`, `services/`, `packages/`) | [Apache-2.0](https://github.com/konethegreat/reservoir/blob/main/LICENSE) | Contributions certified under the DCO |
| **Documentation** (`docs/`, top-level `*.md`) | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | Attribute "Reservoir contributors" |
| **Open reference data** we curate (taxonomy links, safety flags) | CC0 or CC BY, subject to upstream licences | Each dataset carries its own manifest |
| **Community knowledge** (claims, audio, images contributed by people) | **Not blanket-licensed** | Governed per record by consent (`redistribution`, `ai_use`, TK Labels) |
| **Name & logo** ("Reservoir") | Trademark policy to be written | So forks cannot impersonate the community project |

## What "open source" means here — and doesn't

Opening the *code* lets anyone build on the platform, audit the consent logic, and run their own instance. It does **not** open anyone's heritage. A fork of the code does not receive community knowledge, and our API terms will prohibit using the platform for bioprospecting or for extracting restricted tiers.

## Contribution agreements

- **Code:** Developer Certificate of Origin (`git commit -s`).
- **Knowledge:** a plain-language *Knowledge Contribution Agreement* explaining exactly what the contributor is granting and retaining — to be co-drafted with counsel and community representatives, and available in all supported languages. Contributors keep ownership; Reservoir receives only the licence needed to host and present the knowledge according to the chosen consent.

## Third-party data

See [data sources](../research/data-sources.md). Every imported dataset carries its licence in a manifest, and incompatible licences are kept in separate partitions.
