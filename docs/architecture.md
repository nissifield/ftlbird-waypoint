# Architecture guide

Start with the [FTLbird Architecture Review](ftlbird-architecture-review.md), dated 9 September 2026, then contribute to [Platform Contract issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1).

## What is established and what is open

**FACT — repository evidence:** the project began with a design-stage README and Platform Contract issue #1. The supplied review calls for controlled design and validation before implementation. Its original text is preserved with a status banner, not silently revised.

**Terminology:** FTLbird names this project; Fedora Hummingbird names the sole proposed host operating-system target.

**DECISION — current project constraints:** Fedora Hummingbird is the sole supported host target; Tailscale is the private remote-access layer, with public exposure off by default. Host firewalling, application authentication/roles, and bounded break-glass recovery remain separate requirements. Every routine lifecycle operation must work without AI. See the complete [binding commitments](../README.md#architectural-commitments).

**PROPOSAL:** the review's layers, runtime candidates, pack format, gateway placement, secrets broker, signing mechanisms, and eventual one-pack MVP are candidates for assessment. Words such as “enforce” and “verify” in its target architecture describe required future behaviour. They are not evidence that any control exists today.

**UNKNOWN:** the exact supported Fedora Hummingbird image reference and release policy, CPU/hardware envelope, selected runtime and representation, verified compatibility, and production enforcement. Contributors must identify primary sources and versions in #1 before a human maintainer adopts these choices.

**RISK:** private applications can still depend on external connectivity and coordination services. Recovery during internet or Tailscale outages must be designed and evaluated without weakening application authentication. Self-hosted data does not imply independence from every external service.

## Review the boundaries

The next milestone must join platform, security, lifecycle, and operator understanding in one versioned contract. Use the review's critical risks, required architecture changes, AI contractor controls, capability-pack model, and acceptance gates as questions to test.

AI contractor controls must be enforced outside the model: a human-readable work order, least context and privilege, redaction, temporary isolation, allowlisted tools and network destinations, read-only production access by default, no long-lived credentials, deterministic validation, a patch and explanation, migration impact, rollback expectations, human approval, audit, and revocation. Local and remote providers must meet the same contract. None of those mechanisms is implemented here.

Capability packs are maintained products. Their future contract must cover identity, version, provenance, licence, support, compatibility, resources, images, storage, network, authentication, secret handling, privileges, health checks, tests, data classification, and the full install-to-end-of-life lifecycle. Git source/review and OCI image/release distribution remain distinct; private sources require explicit trust and policy validation.

## Read the evidence honestly

The supplied shared agent constitution and agent-pack validation record were inspected for this foundation. Their validation concerns prompt definitions and internal consistency only. It does not prove agent isolation, a runtime, a host integration, production policy enforcement, or pack recovery. Those records remain in the supplied project files; no new agent runtime is introduced here.

The current [foundation validation record](foundation-validation.md) has the same narrow distinction: documentation checks cannot prove platform security or operational recovery. Follow [governance](../GOVERNANCE.md) to propose, record, and revise decisions.
