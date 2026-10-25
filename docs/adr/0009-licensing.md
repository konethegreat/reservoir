# ADR-0009: Licensing

- **Status:** Proposed
- **Date:** 2026-10-25
- **Deciders:** @konethegreat

## Context

The project is public and open source, but "open" must not extend to other people's cultural heritage. We need a licensing approach that keeps the **code** broadly usable, the **documentation** shareable, and the **knowledge** under community control.

## Options considered

For code: MIT (simplest), **Apache-2.0** (patent grant, explicit contribution terms), AGPL-3.0 (strong copyleft against closed SaaS forks), GPL-3.0.

For docs: CC BY 4.0, CC BY-SA 4.0.

For knowledge: blanket CC licence (inappropriate), per-record terms.

## Decision

- **Code:** Apache-2.0. Maximises adoption (including by SA universities, government, NGOs) and gives contributors patent protection. *Open point:* an AGPL core would deter closed commercial forks that could exploit the data pipeline — raise as a Discussion before the first release.
- **Documentation:** CC BY 4.0.
- **Community knowledge:** **no blanket licence.** Governed per record by the consent's `redistribution` field and the contributor/community agreement. Public-tier data may be offered under a community-chosen licence (e.g. CC BY-NC-SA) plus TK Labels.
- **Open reference data** (taxonomy, safety flags we curate): CC0 or CC BY, subject to upstream licences.
- **Contributions:** DCO sign-off for code; a separate, plain-language Knowledge Contribution Agreement (to be drafted with counsel) for knowledge.
- **Trademark:** the name "Reservoir" and logo to be governed so forks can't impersonate the community project.

## Consequences

- ✅ Clear separation between what is free to reuse and what is not.
- ❌ Requires legal drafting (agreement, terms of use, API terms prohibiting bioprospecting uses).

## Validation

Legal review in Phase 0; revisit code licence before first release.
