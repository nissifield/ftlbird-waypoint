---
name: "Security or threat-model review"
about: "Discuss generic hypothetical design threats; never report sensitive findings here."
title: "[Threat model] "
---

Read [CONTRIBUTING.md](https://github.com/nissifield/ftlbird-waypoint/blob/main/CONTRIBUTING.md) and preserve the [binding commitments](https://github.com/nissifield/ftlbird-waypoint/blob/main/README.md#architectural-commitments). This is design-stage only; do not submit deployment work, secrets, production logs, or personal data. For a security concern, use [SECURITY.md](https://github.com/nissifield/ftlbird-waypoint/blob/main/SECURITY.md) and keep the details private.

**This is a public template, not a vulnerability-reporting channel.** Stop if your concern involves a real sensitive finding. Use SECURITY.md as linked above to request private reporting.

## Hypothetical architecture question

Describe the asset, assumed attacker, and trust boundary without identifying a real vulnerable system.

## Evidence and assumptions

Separate FACT and primary sources, ASSUMPTION, PROPOSAL, UNKNOWN, and RISK. Do not include exploit details or confidential evidence.

## Proposed control and rejection test

What should be denied, by which boundary, and how could a future test falsify the control? Do not equate Tailscale with application authentication, a private source with trusted content, or an AI prompt with enforcement.

## Trade-offs and open decision

Describe operator/recovery impact, supply-chain implications, residual risk, and maintainer effort. Link the related contract issue.
