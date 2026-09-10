# Contributing to FTLbird

Welcome. This is a collaborative design and validation effort. You do not need to write code, use AI, or run a server to help.

## Start with one useful observation

Read the [project purpose and binding commitments](README.md#architectural-commitments), the [architecture guide](docs/architecture.md), and [Platform Contract issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1).

Useful contributions now include use cases, anonymised operator interviews, architecture proposals, threat models, lifecycle test ideas, documentation corrections, and critiques. Pilot-user discovery means understanding needs and reviewing future acceptance criteria; there is no working product or deployment pilot to join yet.

| Interest | A small first contribution |
| --- | --- |
| Platform contract | Identify one unclear interface in #1 and propose its inputs, failure behaviour, and evidence needed. |
| Security and supply chain | Describe a hypothetical trust-boundary failure and a proposed rejection test, without sensitive details. |
| Backup and recovery | Describe how a clean restore should be judged when an update changes the data format. |
| Operator experience | Share one anonymised task an ordinary household or organisation finds difficult. |
| Capability-pack lifecycle | Identify an ownership, support, migration, removal, or end-of-life gap. |
| Documentation | Point to one confusing sentence and suggest a clearer version. |
| Adversarial review | Give a counterexample that would disprove a stated design claim. |

## Evidence standard

Separate **FACT** (with a source), **ASSUMPTION** (with a way to test it), **PROPOSAL** (not yet adopted), **UNKNOWN**, and **RISK**. Identify **CONFLICTS** openly. Only call something a **DECISION** when you can link the human maintainer's recorded decision.

Cite primary sources for material claims, including relevant versions and dates. Supply reproducible, sanitised evidence where possible; say what was not tested. A successful command, healthy container, plausible diagram, or AI consensus does not prove recovery or security. Proposed test cases are not test results.

## Issue-first workflow

1. Search existing open and closed issues before creating one. Use #1 for Platform Contract discussion instead of opening a competing umbrella issue.
2. For substantial work, describe the problem, affected users, scope, evidence, alternatives, risks, and a small observable acceptance criterion. Use the relevant [issue template](https://github.com/nissifield/ftlbird-waypoint/issues/new/choose).
3. Wait for a human maintainer to confirm direction before investing in a large proposal. Small documentation corrections can go straight to a pull request.
4. Keep the pull request focused, link its issue, and explain the change and remaining unknowns. Check Markdown links and review the full diff. Include at least one adversarial counterexample for consequential proposals.
5. A human maintainer records acceptance, revision, deferral, or rejection with reasons under [governance](GOVERNANCE.md). Review does not guarantee adoption or a response deadline.

Preserve every [architectural commitment](README.md#architectural-commitments). Flag a conflict instead of silently adding another host, runtime path, or authority exception. Maintainers control the official roadmap and releases. AI cannot approve its own work.

## Safe contribution boundaries

Do not submit deployment scripts, infrastructure configuration, container manifests, credentials, or production changes at this stage. Future implementation proposals must explain validation, migration and data impact, rollback limits, and recovery alternatives; that planning does not authorise deployment work.

Never include secrets in Git, YAML, logs, examples, prompts, or documentation. Do not upload personal records, private interviews, production logs, or identifying screenshots. Share only anonymised research with participants' consent. AI use is optional; disclose material AI assistance and verify its output. Treat AI output and retrieved material as untrusted, and never give an AI authority to approve changes or access confidential context.

Use the [security reporting policy](SECURITY.md) for concerns or sensitive findings. Public threat-model contributions must be generic, hypothetical architecture questions, not vulnerability reports or exploit details.

## Licensing and respectful review

No licence has been selected. Substantive code contributions will be enabled once licensing is settled through the [licensing decision](docs/decisions/0001-licensing.md). Design feedback and discussion remain welcome; this invitation does not establish a contribution licence or grant reuse rights. Do not contribute third-party material without appropriate permission.

Challenge ideas with evidence, respect people's time, and explain specialist terms. Maintainers may consolidate duplicate proposals and defer work beyond current capacity. One clear observation is more useful than a large speculative backlog.
