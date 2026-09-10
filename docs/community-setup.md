# Collaboration setup

## Current setup and limits

Repository inspection on 10 September 2026 confirmed public `nissifield/ftlbird-waypoint`, default branch `main`, Issues enabled, Discussions disabled, and the existing [Platform Contract issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1). This foundation adds four Markdown issue templates and public contribution, governance, and security guidance.

The available connector supports repository-content and issue writes. It exposes no label-creation, issue-pinning, Discussions-management, or private-reporting-settings operation. A GitHub CLI was not available in this workspace. The items below are documented setup, not claims of completed configuration. Private vulnerability reporting availability is UNKNOWN; follow [SECURITY.md](../SECURITY.md).

## Label definitions for maintainer setup

Create only missing labels; preserve useful existing labels. Apply a status and the most relevant area, rather than labelling every issue with every area. Templates currently avoid relying on custom labels that have not been created.

| Label | Meaning |
| --- | --- |
| `status: design` | Design or validation work; no deployment authority. |
| `area: platform-contract` | Single supported host contract and its interfaces. |
| `area: security` | Public, hypothetical security architecture and supply-chain review only. |
| `area: lifecycle` | Install, update, backup, clean restore, migration, rollback, removal, and end-of-life. |
| `area: operator-experience` | Operator research, understandable workflows, and pilot-user discovery. |
| `area: ai-controls` | Optional AI work orders, isolation, validation, audit, and human authority. |
| `help wanted` | A scoped contribution is welcome; acceptance criteria are clear. |
| `good first contribution` | Small, bounded design or documentation work with a clear starting point. |
| `needs evidence` | A material claim lacks sufficient verification. |
| `decision needed` | A human maintainer choice is required. |

Suggested initial application: #1 gets `status: design`, `area: platform-contract`, and `help wanted`; the licensing decision gets `status: design` and `decision needed`. Do not label the entire Platform Contract a first contribution; its small review tasks are suitable entry points.

## Invitation and Discussions

The foundation uses one community invitation issue titled **[Help shape FTLbird before implementation begins — #3](https://github.com/nissifield/ftlbird-waypoint/issues/3)**. A maintainer can pin that issue when the repository interface permits. Pinning is not completed by this change.

Discussions remain disabled. Do not create a parallel forum merely to duplicate #1. If maintainers later enable Discussions and can moderate them, the proposed categories are:

| Category | Purpose |
| --- | --- |
| Announcements | Maintainer status and decision notices. |
| Design discussion | Exploratory questions that link adopted work back to issues. |
| Operator research | Anonymised needs and workflow feedback. |
| Security architecture | Hypothetical design questions only; never sensitive reports. |
| Show and tell / related projects | Relevant approaches and lessons without endorsement claims. |

These categories are proposals, not created categories. Keep issue #1 as the Platform Contract's coordination record even if a forum is added.

The templates follow [GitHub's documented Markdown frontmatter and template workflow](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository). Metadata parsing and content inspection do not replace a live UI preview.
