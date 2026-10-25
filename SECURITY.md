# Security Policy

## Supported versions

Reservoir is pre-alpha; there are no released versions yet. Security reports are nevertheless welcome and taken seriously — especially anything touching **consent, visibility controls, personal information, or exposure of restricted cultural knowledge**.

## Reporting a vulnerability

**Please do not open a public issue.**

Use GitHub's private reporting: go to the **Security** tab → **Report a vulnerability** ([direct link](https://github.com/konethegreat/reservoir/security/advisories/new)).

Please include: what you found, steps to reproduce, the potential impact, and any suggested fix.

## What to expect

- Acknowledgement within **5 working days**.
- An initial assessment and plan within **14 days**.
- Credit in the advisory if you want it.

## Scope

In scope: this repository's code, configuration and workflows; any deployed Reservoir service once it exists.

Particularly important to us:

- Leaks of records marked restricted, community-only or sacred
- Leaks of precise locations of harvest-sensitive or endangered species
- Bypass of consent, attribution or `ai_use` controls
- Exposure of contributor personal information (POPIA)
- Prompt-injection or data-exfiltration paths in the AI agents

Out of scope: social engineering of maintainers, denial-of-service through volumetric traffic, findings from automated scanners without a demonstrated impact.

## Safe harbour

Good-faith research that respects user privacy and does not degrade the service will not be pursued.
