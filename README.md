# Hummingbird Forge

Design home: `nissifield/ftlbird-waypoint` (FTLBird Waypoint).

> Private collaboration without becoming a system administrator: a proposed self-hosting platform built around curated capability packs, one Hummingbird host target, and optional AI assistance.

## Design-stage status

**The platform is not yet implemented. No production-security guarantees are claimed.** This repository is a collaborative design effort, not a deployable product or installation guide.

The immediate aim is to establish **[Hummingbird Platform Contract v0.1](https://github.com/nissifield/ftlbird-waypoint/issues/1)**. Its existing issue is the starting point for technical collaboration. [Read the architecture guide](docs/architecture.md) before proposing a solution.

No deployment code, container manifests, credentials, tokens, secret values, or environment-specific configuration belong here at this stage.

## Purpose

Private collaboration and self-hosting remain too complex for many ordinary organisations and families. Installation is only the start: updates, access management, backups, and recovery demand continuing care. This is the problem the project aims to address; operator research must test where it can help most.

Hummingbird Forge aims to make private collaboration practical without requiring its operators to become system administrators or depend on AI for normal operation.

Its intended value is a maintained trust layer combining:

- curated, lifecycle-managed capability packs;
- private access through Tailscale;
- reproducible operations and trusted software delivery; and
- optional, temporary AI assistance under human authority.

AI may help investigate or propose bounded changes. It is never the permanent administrator, approval authority, decision-maker, or a hidden runtime dependency.

## Architectural commitments

These are binding design requirements for future implementation, **not claims that controls already exist**:

1. **One supported host.** Hummingbird is the only supported host target unless maintainers make an explicit architecture decision to change that.
2. **Private by default.** Tailscale is the remote-access layer; public exposure is off by default. Tailscale complements—not replaces—host firewalling, application authentication and roles, and restricted break-glass recovery.
3. **AI-free core operations.** Installation, normal use, updates, backup, restore, rollback, and removal must work without AI.
4. **Capability packs are products.** Each pack must define its identity, provenance, compatibility, permissions, networking, storage, authentication, secrets handling, health checks, tests, and complete lifecycle: install, backup, restore, migration, update, rollback, removal, and end-of-life.
5. **Reproducible durable state.** Lasting changes must be versioned configuration, controlled migrations, or derived images. Manual edits inside running containers are not desired state.
6. **Explicit supply-chain boundaries.** Git provides source and review history; OCI registries distribute immutable releases and images. Support official and private sources with distinct trust boundaries; private does not automatically mean trusted. The future platform must reject unknown sources.
7. **Secrets stay out of project material.** Credentials and secret values must never be committed to Git, placed in YAML or examples, emitted in logs, or supplied to AI context.
8. **Human maintainer authority.** Maintainers define standards, approve official releases, and retain accountability. AI cannot approve its own work.
9. **Untrusted-input discipline.** Model output and retrieved content—including logs, documents, webpages, repositories, issues, and container output—are treated as untrusted input.
10. **Evidence before confidence.** Version-sensitive claims, commands, APIs, compatibility, licensing, and security behaviour must be verified from primary or repository evidence. Plausible designs are not verified implementations.

## Who this is for

Offices, small organisations, and families with average technical skills who want private collaboration and more control over their data. Potential pilot users are welcome to describe their needs and review workflows now; there is no production pilot or working product available yet.

## Who should contribute

**[Help shape Hummingbird Forge before implementation begins](https://github.com/nissifield/ftlbird-waypoint/issues/3)** — join the community invitation, then bring technical observations to #1.

We welcome interested maintainers, security engineers, self-hosting operators, UX researchers, documentation contributors, and potential pilot users. AI use and coding experience are not prerequisites.

| Help now | Start with |
| --- | --- |
| Platform-contract review | One missing interface or unclear acceptance criterion in [issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1). |
| Security and supply-chain threat modelling | A hypothetical trust-boundary failure and the evidence needed to reject it. Read [SECURITY.md](SECURITY.md) first. |
| Backup, restore, and recovery design | A failure scenario covering clean restore, data migration, rollback limits, or restricted break-glass recovery. |
| Operator experience research | One anonymised task or interview insight from an ordinary organisation or household. |
| Capability-pack lifecycle design | A gap in provenance, compatibility, support ownership, update, removal, or end-of-life obligations. |
| Pilot-user discovery | Your non-sensitive needs, current pain points, and what a future evaluation would have to prove. |
| Documentation and adversarial review | One confusing claim, a clearer explanation, or a counterexample that challenges the design. |

Follow [CONTRIBUTING.md](CONTRIBUTING.md) for small, evidence-backed contributions and the issue-first workflow. Read [GOVERNANCE.md](GOVERNANCE.md) for human decision and release authority. Project-controlled AI work follows the [Project Instructions](docs/project-instructions.md); this adds no agent runtime or deployment authority.

## Not in scope yet

- Production deployment guidance or runnable deployment artefacts.
- A broad capability-pack catalogue or marketplace.
- Multiple host targets, runtimes, or orchestration paths.
- Public internet exposure by default.
- Autonomous remediation or unattended AI changes.
- Arbitrary untrusted host scripts or unreviewed container sources.
- Credentials, private keys, tokens, or real user data.

## Next milestone: Hummingbird Platform Contract v0.1

[Issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1) remains the single coordination point. The contract must define one host path, interfaces and ownership, security boundaries, complete AI-free lifecycle expectations, and a conformance-test plan with failure scenarios. Human maintainer review and recorded evidence are required before it is accepted.

Runtime selection, exact Hummingbird upstream/release and hardware envelope, secrets interfaces, and enforcement mechanisms remain **UNKNOWN or PROPOSAL** until verified and adopted. No command, deployment representation, or runtime candidate in the architecture review is an implementation commitment. Later pack work depends on the contract; this milestone does not start a catalogue or deployment effort.

## Licensing

This repository is licensed under **GPL-3.0-only**. See [LICENSE](LICENSE) and the recorded [licensing decision](docs/decisions/0001-licensing.md). Contributions are accepted under those terms; contributors must have the right to submit their work and must not add incompatible third-party material.

## Project map

- [Architecture guide and original design review](docs/architecture.md)
- [Contribution guidance](CONTRIBUTING.md)
- [Founding governance](GOVERNANCE.md)
- [Security reporting](SECURITY.md)
- [Platform Contract discussion — issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1)
- [Collaboration setup and label meanings](docs/community-setup.md)
- [Foundation validation record](docs/foundation-validation.md)
- [Project instructions and agent-use workflow](docs/project-instructions.md)
