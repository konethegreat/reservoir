# Languages

*Status: initial survey, October 2026. Resource-availability findings come from the sources linked below; **(verify)** marks items to confirm.*

## Scope

South Africa recognises **12 official languages** — English, Afrikaans, isiZulu, isiXhosa, isiNdebele, Sesotho, Sesotho sa Leboa (Sepedi), Setswana, siSwati, Tshivenda, Xitsonga, and South African Sign Language (official since 2023) — plus the Khoi, Nama and San languages recognised in the Constitution (e.g. Khoekhoegowab, N|uu, ǃXun). Reservoir aims to cover all, in phases.

## Principle: languages are not translations

Plant names, kinship terms, ritual vocabulary and proverbs often have **no equivalent** in English. The data model stores names *per language as primary entries* (with orthography, dialect, audio and contributor), not as translations of an English field. See [data model](../architecture/data-model.md).

## Technology availability (what we found)

| Language | Notes from initial survey |
|---|---|
| **isiZulu, isiXhosa** | Supported by Lelapa AI's InkubaLM; Nguni morphological analysers/taggers from NWU/SADiLaR; covered by Sunbird's 51-language Whisper adaptation |
| **Afrikaans** | Best resourced of the group; Common Voice Scripted Speech 25.0 includes an Afrikaans dataset; Whisper trained on ~4 hours |
| **Setswana** | Common Voice 25.0 has a small Setswana dataset (~5 h, 17 speakers); covered by Sunbird Whisper adaptation |
| **Sesotho** | SADiLaR morphological annotations exist; NLP/ASR coverage appears thinner |
| **isiNdebele, siSwati** | Some NWU/SADiLaR annotation work for the Nguni languages; otherwise sparse **(verify)** |
| **Sepedi, Tshivenda, Xitsonga** | Appear least covered in the sources surveyed — **priority for data collection and for avoiding over-reliance on generic models** **(verify)** |
| **SASL** | Separate modality; requires video/sign-recognition research and Deaf community leadership |
| **Khoi & San languages** | Very small speaker populations, some critically endangered; require community-led, non-extractive approaches |

Key external resources:

- [SADiLaR](https://www.sadilar.org/) — national digital language resource centre; catalogue freely available for research
- [Masakhane](https://www.masakhane.io/) — grassroots African NLP research community
- [Lelapa AI](https://lelapa.ai/) — InkubaLM (0.4B, isiZulu/isiXhosa/Swahili/Yoruba/Hausa) and Vulavula speech/text services
- [MzansiText and MzansiLM](https://arxiv.org/pdf/2603.20732) — open corpus and decoder-only model for South African languages (2026)
- [Mozilla Common Voice](https://commonvoice.mozilla.org/) — open speech datasets (coverage varies by language and release)
- [Sunbird AI Whisper adaptation](https://salt.sunbird.ai/models/asr-whisper-51-african-languages/) — ASR for 51 African languages incl. Afrikaans, Tswana, Xhosa, Zulu

## Implications

1. **We cannot assume a single multilingual LLM handles all languages well.** The AI layer is provider-agnostic with per-language routing and evaluation ([ADR-0006](../adr/0006-ai-layer-python-provider-agnostic.md)).
2. **Reservoir can be a data *source* as well as a consumer.** With consent, recorded names, words and phrases can become an open, ethically-collected dataset for language technology — but only for records marked `training_allowed`.
3. **Every language needs a human custodian.** No language ships as "supported" without a native-speaker reviewer ([language custodians](../community/language-custodians.md)).
4. **UI localisation is a design constraint from day one** — string externalisation, text expansion, right orthography, fonts that render clicks (ǃ ǀ ǁ ǂ) and tone/diacritic marks correctly.
5. **Audio matters.** For many users and for oral cultures, speaking is primary and typing is a barrier.

## Evaluation

Before declaring a language "supported" we require: a UI translation reviewed by a custodian, a minimum glossary of reviewed plant names, and an AI-quality evaluation set (see [AI agents](../architecture/ai-agents.md#evaluation)).
