# Repository presentation rationale

**Status: design-stage documentation.** This page explains the public presentation of Hummingbird Forge. It does not create a platform, configure GitHub, establish enforcement, select a licence, or make a security claim.

## Purpose

The README is a two-minute landing page for two audiences:

- a non-specialist who needs to understand the intended outcome and current limits; and
- a prospective contributor who needs one small, safe, evidence-led starting action.

The page leads with a status banner, one-sentence promise, plain-language "What it is / What it is not / Why this matters" framing, and a short call to [Platform Contract issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1) and [community invitation issue #3](https://github.com/nissifield/ftlbird-waypoint/issues/3). Issue #1 remains the sole technical coordination point; the invitation does not create a second umbrella track.

## Visual system and truth labels

The README uses GitHub-native Mermaid diagrams rather than hosted images or proprietary source files. Every diagram is preceded by a concise text summary and includes literal labels, rather than colour-only cues:

| Label | Meaning |
| --- | --- |
| **BINDING** | A future implementation requirement adopted by the project. It is not evidence that a control exists. |
| **PROPOSAL / UNKNOWN** | A choice or fact not yet adopted or verified; the architecture guide and issue #1 are the decision workspace. |
| **NOT-YET-IMPLEMENTED** | A future control, workflow, validation mechanism, or enforcement point that this repository does not claim to provide. |

The diagrams use simple shapes, directional arrows, text labels, and adjacent prose. They avoid colour, logos, external images, tracking, and hover-only meaning so they remain readable in GitHub light and dark themes and when rendered without colour. The labels and summaries are the accessible textual alternative; Mermaid labels intentionally state the actor, boundary, and status.

The diagrams show relationships, not an implementation topology. In particular, they do not imply that Tailscale, firewalling, application identity, provenance checks, lifecycle workflows, AI controls, or recovery mechanisms are installed or tested.

## Navigation and source of truth

The README project map uses repository-relative links for stable documents and canonical GitHub links for the three public issues/PRs. It intentionally keeps platform-contract work in [issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1) and directs broad participation to [issue #3](https://github.com/nissifield/ftlbird-waypoint/issues/3).

For decisions, the human-reviewed default branch is canonical. Issue discussion and an unmerged pull request can record intent or a proposed change, but do not supersede the default branch. This rule matters for the current licensing conflict:

- `main` has no `LICENSE` file and its licensing record says no licence has been selected.
- [Issue #2](https://github.com/nissifield/ftlbird-waypoint/issues/2) records a GPL-3.0-only direction.
- Draft [PR #4](https://github.com/nissifield/ftlbird-waypoint/pull/4) proposes the GPL-3.0-only implementation.

This presentation therefore flags the conflict instead of selecting a result. A human maintainer must review and merge or reject PR #4; then the README and contribution wording should be updated in the same reviewed change if necessary.

## Design-only boundary

The presentation intentionally contains no deployment instructions, manifests, container definitions, infrastructure configuration, credentials, production endpoint, runtime selection, or production-security promise. It describes acceptance bars and evidence gaps only. The lifecycle diagram is especially explicit that install through end-of-life must be AI-free *if implemented*; it is not a working workflow.

## Maintenance rule

When a human-reviewed decision changes a status, update the relevant README label, the architecture guide, and this rationale in one focused change. Preserve issue #1 as the technical coordination point and state whether any visual is a requirement, proposal/unknown, or not-yet-implemented control.
