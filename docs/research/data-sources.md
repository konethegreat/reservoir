# Data sources and licences

*Status: initial survey, October 2026. **Always confirm current licence and terms before ingesting.***

Rule of thumb: **taxonomy and facts about species may come from open datasets; traditional knowledge comes only from consenting people/communities or from published sources whose licence and ethics permit reuse.** Just because something is online does not mean it is ours to ingest.

## Candidate sources

| Source | What it gives | Licence / terms notes | Status |
|---|---|---|---|
| [SANBI National Plant Checklist](https://www.sanbi.org/biodiversity/foundations/biosystematics-collections/plant-checklist/) | ~21.5k South African plant taxa (indigenous, endemic, naturalised); annual release; 2025 version on Zenodo | Confirm dataset licence on the Zenodo record | Primary taxonomic backbone |
| e-Flora of South Africa / PlantZAfrica | Descriptions for ~22k taxa | **(verify)** reuse terms with SANBI | Candidate; likely needs permission |
| [GBIF](https://www.gbif.org/) | Occurrence records, species backbone | Per-dataset licences (CC0, CC BY, CC BY-NC) | Range and phenology; respect licences |
| [iNaturalist](https://www.inaturalist.org/) | Observations + photos | Per-observer licences incl. **CC BY-NC and all rights reserved**; API for apps, not bulk scraping **(verify)** | Validation and ranges; ML training use needs care |
| [Pl@ntNet](https://plantnet.org/) API | Image identification | Free tier (reported 500/day), attribution required; non-profit terms available on request **(verify)** | Candidate ID provider |
| [Wikidata](https://www.wikidata.org/) / Wikipedia | Names, identifiers, links | CC0 / CC BY-SA | Identifier linking |
| [Mozilla Common Voice](https://commonvoice.mozilla.org/) | Open speech data | CC0 for many datasets | ASR research and baselines |
| [SADiLaR](https://www.sadilar.org/) catalogue | Text, speech, annotation resources | Varies per resource; many free for research | Language research |
| Published ethnobotany literature | Documented traditional uses | Copyright applies to text; facts are not copyrightable but community interests still matter | Cite, never copy wholesale |
| Community contributions | The heart of the project | Governed by per-record consent and agreement | Core |

## Ingestion rules

1. **Record the licence and source URL on every imported row.**
2. **Never ingest CC BY-NC data into a dataset or model that will be redistributed or used commercially** without checking compatibility; keep it in a separate, labelled partition.
3. **Do not scrape.** Use official APIs/bulk exports; respect rate limits and terms.
4. **Published ethnobotanical claims are "documented, not endorsed".** They enter as claims attributed to the publication, with a safety review status of `unreviewed` until a qualified reviewer signs off.
5. **No ingestion of community knowledge from archives without the originating community's involvement.** Even where an archive permits, we ask.

## Data we generate

- **Species and claim records** — governed by their contributors' consent.
- **Open reference data** (taxonomy, safety flags, our own curation) — intended for open licence ([licensing](../legal/licensing.md)).
- **Language data** (audio, text) — only released as datasets for records with `ai_use = training_allowed`, with community approval.

## Gaps to research

- Exact licence on the SANBI checklist and e-Flora
- Voucher/herbarium data integration (SANBI collections)
- Toxicology databases for safety flags (authoritative and open?)
- South African Poison Information Centre data-sharing possibilities
