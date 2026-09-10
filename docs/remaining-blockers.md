# Remaining blockers and maintainer actions

**Status:** Current design-stage register. This document records open work and evidence gaps; it does not claim configuration, implementation, security certification, or release authority.

## Immediate governance blockers

| ID | Blocker | Why it matters | Required owner/action | Evidence to clear |
| --- | --- | --- | --- | --- |
| B-01 | [PR #4](https://github.com/nissifield/ftlbird-waypoint/pull/4) remains a draft. | GPL-3.0-only terms and project agent-use instructions are not effective on `main` until a human merges the reviewed change. | Repository owner / human maintainer: review scope, licensing wording, and agent boundaries; then merge or request revision. | Merged PR; default branch contains `LICENSE`, licensing decision, and project instructions. |
| B-02 | Private vulnerability reporting is unconfirmed; no alternate private contact is published. | A reporter with a real sensitive concern has no verified private route. Public issues are unsuitable for technical details. | Repository owner: enable GitHub private vulnerability reporting or publish and monitor a private contact; test the submission path without sensitive content. | A tested, documented private reporting route and a responsible human handling it. |
| B-03 | The documented repository labels are not configured. | Triage, ownership, and evidence gaps are harder to find; issue templates deliberately do not depend on unavailable labels. | Repository owner: create the labels in [community setup](community-setup.md) and apply the initial labels to issues #1–#3. | Labels visible in GitHub; #1 has `status: design`, `area: platform-contract`, and `help wanted`; #2 has `status: design` and `decision needed`. |
| B-04 | HF-09’s prompt is reconstructed, not recovered from an original source. | Its independence boundary is important for consequential review; source fidelity remains unverified. | Human maintainer: review/accept, revise, or replace the reconstructed HF-09 prompt before release-critical reliance. | Recorded maintainer decision and the approved prompt source. |

## Design gates before implementation

| ID | Gate | Current state | Exit evidence |
| --- | --- | --- | --- |
| D-01 | [Hummingbird Platform Contract v0.1 — issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1) | Open; no contract draft is accepted. | One supported host path; owned interfaces and failure behaviour; lifecycle/compatibility matrix; conformance and held-out failure tests; human review verdicts. |
| D-02 | Platform identity and enforcement choices | **UNKNOWN / PROPOSAL.** Exact Hummingbird upstream/release, hardware envelope, runtime/representation, secrets interface, and enforcement mechanisms are not adopted. | Primary-source evidence, alternatives analysis where consequential, recorded human decisions, and contract updates. |
| D-03 | Recoverability and operator evidence | Unbuilt and untested. | AI-free install, update, backup, clean restore, migration, rollback, removal, outage, and restricted break-glass evidence understandable to average-skill operators. |
| D-04 | Supply-chain and AI contractor enforcement | Requirements are documented; no runtime enforcement exists. | Policy, provenance, secret-redaction, isolation, approval, audit, and revocation mechanisms with deterministic and adversarial validation. |

## Authority boundaries

- AI may draft, inspect, test, and report evidence within an approved scope. It cannot accept risk, approve its own work, merge a reviewed decision, enable security settings, publish commitments, or treat documentation as enforcement.
- This repository remains design-stage only. These blockers do not authorise deployment, production access, credential use, or collection of real user data.
- If a blocker involves a sensitive security report, use the current [security policy](../SECURITY.md); do not place technical details in an issue or this document.

## Review cadence

Review this register whenever a human maintainer merges a governance change, makes a Platform Contract decision, configures a GitHub control, or closes an acceptance criterion. Preserve closed items with their evidence rather than deleting history.
