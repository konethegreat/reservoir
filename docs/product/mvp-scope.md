# MVP scope (Phase 1 — "Seed")

*Status: proposed. The MVP is the smallest thing that proves the core promise: **point a camera at a plant and learn something true, in your language, safely.***

## In scope

1. **Plant identification** — photo → ranked candidates with honest confidence and look-alike warnings (server-assisted first).
2. **Species pages** for a curated starter set (~300 culturally and medicinally relevant species), seeded from open taxonomy with every field sourced.
3. **Names in ≥ 3 South African languages** with attribution (candidates: isiZulu, isiXhosa, Tshivenda — to be confirmed with custodians).
4. **Traditional use claims** — only sourced and safety-reviewed; shown as *"traditionally used by…"*.
5. **Contribute** — add a name, a use, a recipe or a note, with a plain-language consent step (visibility, attribution, AI-use).
6. **Offline use** for downloaded packs; sync when online.
7. **Safety model v1** — toxicity/look-alike warnings, location blurring, disclaimers.
8. **Basic review queue** for curators and safety reviewers (web).
9. **Localised UI** in the MVP languages and English.

## Explicitly out of scope for MVP

- Open-ended AI chat (launch with retrieval-only "ask about this plant" or none)
- Audio capture and ASR (Phase 2)
- iOS and web consumer app
- Social features, comments, feeds
- Sacred/custodian tiers beyond basic support (design for them; limit launch content to `public` and `community`)
- Monetisation of any kind

## Success criteria

- Top-5 identification accuracy on the SA evaluation set at or above an agreed threshold, with calibrated confidence.
- 100 % of published claims have a source and a consent record.
- Zero un-reviewed toxic-species use claims published publicly.
- Core flows usable offline on a 2 GB Android Go device within the performance budgets.
- At least 3 language custodians have reviewed their language's UI and glossary.
- Qualitative: knowledge holders testing the contribute flow say it feels respectful and in their control.

## Key risks

| Risk | Mitigation |
|---|---|
| ID accuracy too low on SA flora | Spike first; narrow to a curated species set; abstain more |
| Not enough quality community content at launch | Seed from published/open sources + partner programmes; invite holders early |
| Consent UX too complex | Co-design with holders; voice-guided consent |
| Funding | Early grants/partnerships; keep infra cheap |
| Legal uncertainty | Counsel review before accepting community content |
