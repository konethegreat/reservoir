# Legal and ethics

> **This page is research, not legal advice.** A South African lawyer with IP and indigenous-knowledge experience must review the consent and licensing design before launch. That review is a Phase 0 milestone.

## Frameworks that apply

### Protection, Promotion, Development and Management of Indigenous Knowledge Act, 2019

Establishes protection for indigenous knowledge held by indigenous communities, including knowledge of natural resources, with provisions for registration, cataloguing, documentation and recording, and access and benefit-sharing. Draft regulations (June 2026 report) would introduce **biocultural community protocols** and mandatory prior-informed-consent steps for third parties **(verify against the Government Gazette; the commenting period reportedly closed 3 August 2026)**. See [overview](https://leap.unep.org/en/countries/za/national-legislation/protection-promotion-development-and-management-indigenous) and [draft-regulation commentary](https://acts.co.za/news/blog/2026/06/indigenous-knowledge-draft-regulations-comment).

**Implication:** Reservoir may itself be a "third party" handling indigenous knowledge. We must design for registration/recordal interoperability, community protocols, and benefit-sharing — and seek the Department's guidance early.

### Biodiversity and bioprospecting law (NEMBA and BABS regulations)

The National Environmental Management: Biodiversity Act regulates bioprospecting and benefit-sharing for indigenous biological resources, including associated traditional knowledge. **Reservoir is not a bioprospecting tool**, but its dataset could be misused as one; terms of use and API access policies must address this.

### POPIA (Protection of Personal Information Act, 2013)

Contributor details, voices, photos and locations are personal information. Requirements: lawful basis, purpose limitation, minimisation, security safeguards, data-subject rights, and care with children's data and special personal information. Voice recordings can be identifying biometric-adjacent data **(verify classification)**.

### Nagoya Protocol and CBD

South Africa is a party. Relevant to access and benefit-sharing for genetic resources and associated traditional knowledge.

### Medicines and consumer law

Medicines regulation (Medicines and Related Substances Act) and consumer protection law constrain health claims. The **Traditional Health Practitioners Act** frames practitioner recognition. Reservoir must not make therapeutic claims or promote unregistered products.

### Copyright and database rights

Published ethnobotanical literature and databases carry copyright and licence terms ([data sources](data-sources.md)).

## Ethical frameworks we adopt

- **[CARE Principles for Indigenous Data Governance](https://www.gida-global.org/care)** — Collective benefit, Authority to control, Responsibility, Ethics.
- **[Local Contexts TK and Biocultural Labels](https://localcontexts.org/)** — community-issued, machine-readable governance signals. These are not legal instruments by themselves; they express community protocols. Integration approach: store labels as metadata per record and sync with the Local Contexts Hub where possible **(verify API)**.
- **FAIR** for the open parts of the data — but explicitly *subordinate* to CARE for community knowledge.
- **Free, prior and informed consent (FPIC)** as the standard for community knowledge.
- **The Nagoya/UNDRIP spirit**: communities' rights to maintain, control, protect and develop their cultural heritage.

## Design commitments flowing from this

1. Consent is **per claim**, **revocable**, and **versioned**. See [knowledge sovereignty](../architecture/knowledge-sovereignty.md).
2. A community can **withdraw** knowledge; withdrawal propagates to caches, derived datasets and (where feasible) AI indexes. Training data once used in a model cannot be un-learned — hence `training_allowed` is opt-in and rare.
3. **Sacred/restricted knowledge** is never exposed to AI services outside community-controlled infrastructure, never indexed in public search.
4. **Benefit-sharing**: Reservoir is non-commercial, but any future revenue (grants, partnerships) must have a published benefit-sharing policy returning value to contributing communities.
5. **Children's data**: minimal collection; no profiling; age-appropriate consent.
6. **Takedown within days** of a credible cultural-sensitivity report.
7. **Transparency**: public documentation of what AI does with data.

## Risks and mitigations

| Risk | Mitigation |
|---|---|
| Biopiracy — commercial actors mine the dataset | Tiered access; API terms prohibiting bioprospecting use; rate-limits; no bulk export of restricted tiers; benefit-sharing policy |
| Misattribution or wrong community credit | Contributor-declared community + custodian review; edit history |
| Exposure of sacred knowledge | Default restrictive tiers; custodian veto; no AI on sacred tier |
| Poisoning from misidentification | Safety model; confidence thresholds; look-alike alerts; prominent disclaimer |
| Over-harvesting | Location blurring for sensitive species; sustainable-harvest guidance |
| Data breach | Minimisation; encryption; security policy; audit log |
| Model memorisation of private data | `ai_use` defaults to `none`; no training on non-consented records; red-team tests |
| Cultural flattening by AI | Per-language evaluation by custodians; human review of translations |

## Open questions for counsel and communities

1. Is a community-contributed record a "recordal" under the Act, and do we need to register Reservoir as a repository?
2. Who can legitimately consent on behalf of a community? What is the verification model?
3. What licence terms (if any) should accompany *public-tier* community knowledge?
4. How should the app handle knowledge that is public in the literature but sacred to a community today?
5. What entity should hold the data long-term (trust, NPC, university)?
