# Contributing to Reservoir

Thank you for helping preserve living culture. Reservoir needs many kinds of contributors — **you do not need to write code to make a real difference.**

By participating you agree to our [Code of Conduct](CODE_OF_CONDUCT.md).

## Ways to contribute

| If you are… | You can… | Start here |
|---|---|---|
| A knowledge holder, elder, healer, cook, craftsperson | Advise on how knowledge should be captured and protected; later, contribute through the app | [Discussions → Knowledge holders](https://github.com/konethegreat/reservoir/discussions) |
| A speaker of a South African language | Review terminology, glossary, UI strings; become a language custodian | [`docs/community/language-custodians.md`](docs/community/language-custodians.md) |
| A botanist / ethnobotanist / pharmacist | Review species data and safety notes | [Issues → `area: safety`](https://github.com/konethegreat/reservoir/labels/area%3A%20safety) |
| A lawyer / IP / data-protection specialist | Review the consent and licensing model | [`docs/research/legal-and-ethics.md`](docs/research/legal-and-ethics.md) |
| A developer / ML engineer / designer | Build, spike, review | [Good first issues](https://github.com/konethegreat/reservoir/labels/good%20first%20issue) |
| A writer / researcher | Improve docs, verify citations | Any file in [`docs/`](docs/) |

## Ground rules specific to this project

1. **Never add cultural or medicinal claims without a source.** Every claim must cite a published source, a named contributor, or a community. "I read it somewhere" is not a source.
2. **Never copy sacred, restricted or community-held knowledge into this repository** (issues, PRs, discussions, test fixtures) without that community's explicit consent. When unsure, ask first and share nothing.
3. **No medical advice.** Documentation and UI copy describe *traditional use*, not treatment.
4. **Respect licences.** Don't paste content from sources whose licence doesn't allow redistribution. See [`docs/research/data-sources.md`](docs/research/data-sources.md).
5. **Don't train on, or send to third-party AI services, any record whose `ai_use` is not permitted.** (See the data model.)

## Development workflow

1. **Discuss first** for anything non-trivial: open an issue or a Discussion.
2. **Fork**, then branch from `main`: `feat/…`, `fix/…`, `docs/…`.
3. Keep PRs **small and focused**. One concern per PR.
4. Use [Conventional Commits](https://www.conventionalcommits.org/): `feat(api): add species endpoint`.
5. Fill in the PR template. Link the issue it closes.
6. CI must pass. A maintainer (see [`GOVERNANCE.md`](GOVERNANCE.md)) reviews; changes touching consent, privacy or safety need a second reviewer.
7. **Architectural changes need an ADR** — copy [`docs/adr/0000-template.md`](docs/adr/0000-template.md).

### Documentation conventions

- Markdown, one sentence per concept, no trailing whitespace; `markdownlint` runs in CI.
- Prefer relative links. Link-checking runs in CI.
- Use South African English spelling (colour, programme, organisation).
- Use each language's own orthography and names (isiZulu, not "Zulu language", in running text where practical).

### Code conventions (once code lands)

Each app/service documents its own setup in its `README.md`. General expectations: tests with every behavioural change, no secrets in the repo, no new dependency without a note about its licence and maintenance health.

## Reporting problems

- **Security vulnerability?** Use private reporting — see [`SECURITY.md`](SECURITY.md). Do not open a public issue.
- **Cultural-sensitivity concern** (content that should be removed, restricted or re-attributed)? Open an issue using the *Cultural sensitivity / takedown* template — or report privately if the content itself is sensitive. We treat these as the highest priority.
- **Bug / feature / question?** Use the issue templates.

## AI-assisted contributions

AI tools are welcome in this project — it is part of what we are building. If you used one substantially, say so in the PR. You remain responsible for correctness, licensing and cultural appropriateness of what you submit. See [`CLAUDE.md`](CLAUDE.md) for guidance given to AI coding agents working in this repo.

## Licensing of contributions

Code contributions are licensed under [Apache-2.0](LICENSE). By opening a PR you certify the [Developer Certificate of Origin](https://developercertificate.org/) — sign off commits with `git commit -s`. Community **knowledge** contributions are governed by a separate agreement; see [`docs/legal/licensing.md`](docs/legal/licensing.md).
