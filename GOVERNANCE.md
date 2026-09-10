# Founding governance

**Phase: collaborative design and validation.** No production platform or official capability-pack release exists yet. These rules describe project responsibilities and intended trust policy; they do not claim automated enforcement.

## Maintainer responsibility and authority

Human maintainers steward the project's purpose, binding constraints, Platform Contract, contribution review, roadmap, security handling, and eventual official releases. They record decisions, unresolved objections, accepted scope, and evidence gaps. Release signing, compatibility support, incident handling, and retirement obligations must be defined and resourced before a release is promised.

This document does not appoint people, create an organisation, or establish a legal structure. Repository permissions alone are not a published maintainer roster. Maintainer appointments and authority changes must be recorded explicitly by the repository owner or existing authorised human maintainers.

AI can prepare proposals and evidence. It is never a permanent administrator, decision-maker, runtime dependency, hidden control plane, or approval authority. AI cannot approve its own work. Human approval of a design is distinct from authorisation to change production.

## How decisions are made

1. Propose substantial changes in an existing relevant issue, starting with [Platform Contract #1](https://github.com/nissifield/ftlbird-waypoint/issues/1), or a focused new issue when needed.
2. State the problem, facts and sources, assumptions, alternatives, risks, maintainer burden, and a falsifiable acceptance bar.
3. Invite review from the affected technical and operator perspectives. Preserve objections and distinguish missing evidence from disagreement.
4. A human maintainer records the outcome and rationale: accepted, needs revision, deferred, or rejected. Significant choices become versioned architecture decision records linked to their review and named human decision-maker.
5. Revisions link to the prior decision, explain new evidence and compatibility/recovery consequences, and require fresh human review. Never silently overwrite decision history.

The [README commitments](README.md#architectural-commitments) bind current work. Expanding beyond Fedora Hummingbird or changing another binding constraint requires an explicit human architecture decision; no such expansion is authorised here. Contributors may challenge a decision without assuming it has changed.

## Intended source trust levels

These are design requirements for future releases, not certifications currently issued by the project.

| Level | Meaning | Required treatment |
| --- | --- | --- |
| OFFICIAL | Maintainer-reviewed, tested, signed, and maintained against the official contract. | Verify provenance, compatibility and policy, then obtain the required operator review. |
| APPROVED-PRIVATE | Explicitly owner-trusted private content that passes applicable policy validation. | Validate independently; private ownership does not confer official support or automatic trust. |
| COMMUNITY | Third-party content without official maintainer support. | Warn, require elevated review, and apply policy checks. |
| UNKNOWN | Unverified source or unresolved provenance. | Reject. |

Git holds source and review history; OCI registries distribute images and immutable releases. Source privacy, artifact identity, signature validity, requested privileges, and support responsibility are separate concerns. The Platform Contract must define how these checks fail closed; prose is not enforcement.

## Capacity and accountability

Prioritise the Platform Contract before a pack catalogue. Before accepting future release obligations, identify a responsible human, support scope, lifecycle evidence, and an end-of-life path. Do not promise support dates or incident response times without capacity. Maintainers can narrow, defer, or retire proposed work with a recorded explanation.

The [licensing decision](docs/decisions/0001-licensing.md) remains open. Nothing here selects a licence, contributor agreement, legal entity, or trademark policy. [Contribution guidance](CONTRIBUTING.md) and [security reporting](SECURITY.md) define the current public entry points.
