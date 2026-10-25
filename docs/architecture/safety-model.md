# Safety model

*Status: proposed. Requires review by a qualified botanist/pharmacologist/toxicologist before Phase 1 ships.*

## Why safety is a first-class design topic

1. **Mis-identification can poison.** Many edible and medicinal plants have toxic look-alikes.
2. **Traditional use is not medical advice.** Dose, preparation, interactions with medication and contraindications matter and are rarely documented.
3. **Over-collection can destroy species.** Publishing locations of threatened medicinal plants invites stripping.
4. **AI hallucination is most dangerous exactly here.**

## Rules

### R1 — Honest identification

- Always show top-k candidates with calibrated confidence, never a single confident answer from a weak match.
- Below a confidence threshold: *"We can't identify this reliably."* Offer re-capture guidance (leaf, flower, bark, whole plant).
- **Never say "safe to eat/use".** At most: *"Reported as traditionally eaten. Do not eat anything you haven't confirmed with an expert."*

### R2 — Toxicity and look-alikes are loud

- Each plant has `toxicity_level` (`none_known` | `caution` | `toxic` | `deadly`) and `lookalikes[]` with distinguishing features.
- Toxic/deadly warnings are shown **before** use information, not after.
- Known dangerous look-alike pairs trigger an extra confirmation step.

### R3 — No medical advice

- Use-claims are shown as *"Traditionally used by [community/source] for…"* — never as treatment.
- Persistent, readable disclaimer on medicinal content; link to seeking qualified/registered health care; emergency guidance (poison centre contact — to be verified with relevant bodies).
- No dosage generation by AI. Dosage appears only as an attributed, safety-reviewed claim, and we default to not showing it until reviewed.
- No product sales, no health-condition-targeted recommendations to individuals.

### R4 — Conservation first

- `harvest_sensitive` species: public location is generalised to a coarse region (e.g. quarter-degree grid or district); precise location is private to the contributor and never leaves their device unless consented.
- Photos' EXIF GPS is stripped on upload by default.
- Species with protected status display sustainable-use guidance and legal notes.

### R5 — Claims pass a safety gate

- Claim states: `unreviewed` → `reviewed` → `flagged`. Medicinal and food-preparation claims on plants with `toxicity_level ≥ caution` **cannot be published to `public`** until `reviewed` by a qualified reviewer.
- AI-generated or AI-assisted claims are always labelled and always enter as `unreviewed`.

### R6 — Children and vulnerable users

- Strong guidance for children: never taste/pick unknown plants; adult supervision cues.
- Pregnancy and medication-interaction warnings where documented.

## AI-specific safety

- **Retrieval-grounded only.** The assistant answers solely from approved claims; if none support an answer, it says so.
- **Citation required.** Every sentence about uses/safety links to a claim.
- **Refusal behaviours:** won't give dosages, won't diagnose, won't advise stopping medication, won't suggest combining plants.
- **Evaluation suite** of adversarial prompts (poisonous plants described as edible, dosage requests, "is this safe for my baby?") run in CI against any prompt/model change. See [AI agents](ai-agents.md#evaluation).
- **Prompt-injection hygiene:** user-contributed text is data, never instructions.

## Operational safety

- A **safety review queue** staffed by qualified volunteers.
- A **fast-path "flag this"** on every claim; flagged claims are hidden pending review for toxicity-related flags.
- **Incident process:** if harm is reported, claim hidden, root cause analysed, public post-mortem.
- **Partnerships to pursue:** SANBI, university pharmacology/ethnobotany departments, poison information centres.

## Open questions

- Authoritative, openly licensed toxicity data for South African flora?
- How to calibrate confidence honestly across wildly different species frequencies?
- What liability exposure exists for a free educational app, and what disclaimers/structures mitigate it? (Counsel.)
