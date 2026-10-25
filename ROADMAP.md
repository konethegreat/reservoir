# Roadmap

Reservoir is in **Phase 0**. Phases are ordered by dependency, not by date — we publish milestones on the [GitHub milestones page](https://github.com/konethegreat/reservoir/milestones) as capacity becomes clear.

## Phase 0 — Foundation *(current)*

Goal: a project other people can trust and join.

- [x] Vision, principles, research landscape
- [x] Proposed architecture and ADRs
- [x] Governance, licensing approach, code of conduct, security policy
- [ ] Validate the stack with spikes (mobile benchmark on 2–3 GB Android phones, plant-ID accuracy on South African flora)
- [ ] Legal review of consent model against the Indigenous Knowledge Act and POPIA
- [ ] Recruit first language custodians and a botanical/safety advisor
- [ ] Choose project name/domain/email, and set up funding channels

## Phase 1 — Seed *(MVP)*

Goal: point a camera at a plant and learn something true.

- Plant identification (server-assisted first, on-device model second)
- Species pages seeded from open data (SANBI National Plant Checklist, GBIF), every field carrying its source
- Names in ≥ 3 South African languages, contributed and attributed
- Contribution flow: add a name, a use, a recipe — with provenance and consent
- Safety model v1: toxic/look-alike warnings, conservation-sensitive location blurring
- Offline-first mobile app (Android first)

## Phase 2 — Voices

Goal: capture living language, not just text.

- Audio recording and playback for names, words, proverbs, songs
- Speech-to-text experiments for low-resource languages (with community opt-in)
- Language custodian tools: glossary, review queues, dialect tagging
- Expand to ≥ 6 languages

## Phase 3 — Agents

Goal: the native AI fleet, always under human authority.

- Elicitation agent (interview-style capture), Librarian, Verifier, Translator, Consent Guardian
- Retrieval-augmented answers with citations — no un-sourced claims
- Review queues and trust tiers for contributions
- Evaluation suite: safety, hallucination, cultural-appropriateness

## Phase 4 — Commons

Goal: sustainable, community-governed, nationwide.

- All official languages incl. SASL; Khoi and San language partnerships
- Community Knowledge Councils and Local Contexts (TK) Label integration
- iOS, web portal, public API for researchers and educators
- Institutional partnerships (universities, SANBI, SADiLaR, museums, archives)
- Governance transition to a non-profit / trust structure

## How this changes

Open a [Discussion](https://github.com/konethegreat/reservoir/discussions) or a [feature request](https://github.com/konethegreat/reservoir/issues/new/choose). Significant changes are recorded in [`docs/adr/`](docs/adr/).
