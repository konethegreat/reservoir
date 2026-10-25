# Landscape and prior art

*Status: initial survey, October 2026. Items marked **(verify)** come from secondary sources and need checking against primary documentation before we depend on them.*

Reservoir sits at the intersection of four fields. Nothing existing covers all four for South Africa.

| Field | Existing work | What it does well | The gap Reservoir fills |
|---|---|---|---|
| **Plant identification** | [Pl@ntNet](https://plantnet.org/), [iNaturalist](https://www.inaturalist.org/) / Seek, Google Lens, commercial apps (PictureThis etc.) | Good global image-based ID; large crowd-sourced datasets | Cultural, medicinal and culinary knowledge in *local languages*, attributed to *communities*; free with no paywall; offline for SA hardware |
| **South African botany** | [SANBI National Plant Checklist](https://www.sanbi.org/biodiversity/foundations/biosystematics-collections/plant-checklist/), e-Flora / PlantZAfrica, GBIF | Authoritative taxonomy and distribution | Consumer-friendly, indigenous names and uses, safety and community layer |
| **Indigenous data governance** | [Mukurtu CMS](https://mukurtu.org/), [Local Contexts](https://localcontexts.org/) TK/BC Labels, [CARE Principles](https://www.gida-global.org/care) | Right ideas about authority and protocols; proven in archives | Not designed for a mass-market, offline mobile app with AI in the loop |
| **African-language AI** | [Masakhane](https://www.masakhane.io/), [Lelapa AI](https://lelapa.ai/) (InkubaLM, Vulavula), [SADiLaR](https://www.sadilar.org/), Mozilla Common Voice | Corpora, models and a research community | A *domain* (plants, practice, oral culture) with real use cases and a flow of consented speech/text data |

## Closest comparisons

### Pl@ntNet

Open, non-profit, scientific; free API tier (reported 500 identifications/day) with attribution requirements and restrictions on multiple free accounts; paid tiers beyond that **(verify at [my.plantnet.org](https://my.plantnet.org/pricing))**. Strong candidate as an *ID provider*, but dependence on a third party for our core feature is a risk — see [plant identification](../architecture/plant-identification.md).

### iNaturalist

A huge community-observation dataset; observations are licensed per-observer (CC0, CC BY, CC BY-NC, or all rights reserved) and the API is meant for application development, not bulk scraping **(verify current terms)**. Excellent for *validation data* and range information; licensing of images for ML training must be handled carefully ([data sources](data-sources.md)).

### Mukurtu CMS

The most important prior art for *how* to treat Indigenous knowledge: community-defined protocols, cultural protocols per item, TK Label support **(verify)**. Reservoir borrows its thinking and aims to interoperate where possible, but needs mobile-first, offline and AI-integrated capabilities Mukurtu is not built for.

### South African government work

The Indigenous Knowledge Systems policy (2004) and the [Protection, Promotion, Development and Management of Indigenous Knowledge Act, 2019](https://leap.unep.org/en/countries/za/national-legislation/protection-promotion-development-and-management-indigenous) establish recording, registration and protection regimes, and draft regulations introducing "biocultural community protocols" were published for comment in 2026 **(verify against the Government Gazette)**. Reservoir must be designed to *work with* these regimes — see [legal and ethics](legal-and-ethics.md).

## What we learn from existing apps

- **Free tiers are generous but the best features are paywalled** in commercial plant apps; Reservoir's differentiator is *no paywall on knowledge*.
- **Identification alone is not enough** — retention comes from meaning and story (what is this to *my* people?).
- **Crowd-sourced quality needs trust tiers and review**, not a free-for-all.
- **Language support is usually machine-translated** and often poor for Bantu languages; native review is essential.

## Open research questions

1. How accurate are off-the-shelf plant-ID models on South African flora (fynbos, bushveld, grassland, succulent Karoo)? Where do they fail?
2. How should "consent" work for knowledge held collectively and historically (no single author)?
3. What is the minimal viable on-device model that works on a 2 GB Android Go phone?
4. What speech/ASR quality is achievable for Tshivenda, Xitsonga, siSwati and isiNdebele?
5. How do we fund moderation, language custodianship and server costs for a permanently free app?

Track these as issues labelled `area: research`.
