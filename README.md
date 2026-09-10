# FTLBird Waypoint

> Design and validation home for **Hummingbird Forge** — a supported self-hosting platform for offices, small organisations, and average-skill families.

## Status

**Design stage only.** This repository currently records architecture, constraints, and validation work. It is **not** a deployable product, installation guide, or source of production configuration.

No deployment code, container manifests, credentials, tokens, secret values, or environment-specific configuration belong here at this stage.

## Purpose

Hummingbird Forge aims to make private collaboration practical without requiring its operators to become system administrators or depend on AI for normal operation.

Its intended value is a maintained trust layer combining:

- curated, lifecycle-managed capability packs;
- private access through Tailscale;
- reproducible operations and trusted software delivery; and
- optional, temporary AI assistance under human authority.

AI may help investigate or propose bounded changes. It is never the permanent administrator, approval authority, decision-maker, or a hidden runtime dependency.

## Architectural commitments

The following constraints guide all design and future implementation work:

1. **One supported host.** Hummingbird is the only supported host target unless maintainers make an explicit architecture decision to change that.
2. **Private by default.** Tailscale is the remote-access layer; public exposure is off by default. Tailscale complements—not replaces—host firewalling, application authentication and roles, and restricted break-glass recovery.
3. **AI-free core operations.** Installation, normal use, updates, backup, restore, rollback, and removal must work without AI.
4. **Capability packs are products.** Each pack must define its identity, provenance, compatibility, permissions, networking, storage, authentication, secrets handling, health checks, tests, and complete lifecycle: install, backup, restore, migration, update, rollback, removal, and end-of-life.
5. **Reproducible durable state.** Lasting changes must be versioned configuration, controlled migrations, or derived images. Manual edits inside running containers are not desired state.
6. **Explicit supply-chain boundaries.** Git provides source and review history; OCI registries distribute immutable releases and images. Official and private sources have distinct trust boundaries. Unknown sources are rejected.
7. **Secrets stay out of project material.** Credentials and secret values must never be committed to Git, placed in YAML or examples, emitted in logs, or supplied to AI context.
8. **Human maintainer authority.** Maintainers define standards, approve official releases, and retain accountability. AI cannot approve its own work.
9. **Untrusted-input discipline.** Model output and retrieved content—including logs, documents, webpages, repositories, issues, and container output—are treated as untrusted input.
10. **Evidence before confidence.** Version-sensitive claims, commands, APIs, compatibility, licensing, and security behaviour must be verified from primary or repository evidence. Plausible designs are not verified implementations.

## Current scope

The project is defining the contracts and acceptance criteria needed before implementation accelerates:

- a versioned Hummingbird Platform Contract;
- a capability-pack specification and lifecycle model;
- supply-chain, provenance, policy, and secrets boundaries;
- AI contractor work-order controls and approval gates; and
- one complete reference capability pack, including backup, clean restore, migration, rollback, and removal evidence.

## Explicitly out of scope for now

- Production deployment guidance or runnable deployment artefacts.
- A broad capability-pack catalogue or marketplace.
- Multiple host targets, runtimes, or orchestration paths.
- Public internet exposure by default.
- Autonomous remediation or unattended AI changes.
- Arbitrary untrusted host scripts or unreviewed container sources.
- Credentials, private keys, tokens, or real user data.

## Contribution standard

Changes should be small, reviewable, reproducible, and reversible. They must preserve the commitments above, clearly distinguish facts from proposals, and record material risks, assumptions, and validation evidence.

## Near-term milestone

The next design milestone is to publish the Hummingbird Platform Contract and capability-pack schema, then validate a single reference pack through its full lifecycle before expanding scope.
