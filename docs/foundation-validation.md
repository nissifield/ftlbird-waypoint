# Public foundation validation

**Scope:** documentation and GitHub collaboration foundation, 10 September 2026. This record does not approve a Platform Contract, select a licence or runtime, or certify any production control.

## Inspected evidence

- Public repository `nissifield/ftlbird-waypoint`, ID `1363402122`, default branch `main`.
- Baseline commit `cf3ed943305b40ec4f4b02d37a0c31fe3d9a5e7a`; its recursive tree contained only `README.md`.
- All existing issues (open and closed): one [Platform Contract issue #1](https://github.com/nissifield/ftlbird-waypoint/issues/1), with no comments at inspection. Its title, body, and open state are preserved.
- Supplied architecture review, shared constitution, agent-pack README, validation record, verification and wisdom mandates, and relevant steward and repository-engineer definitions. These are design records, not execution evidence.
- No existing licence or documented licensing choice was found in that scope. The [licensing ADR](decisions/0001-licensing.md) leaves the choice open.

## Compact Build → Attack → Verify → Revise

Built a focused README improvement, contribution/governance/security guidance, four issue templates, an architecture reading guide with the original review preserved, and small licensing/community records. Reused #1; only the missing [licensing issue #2](https://github.com/nissifield/ftlbird-waypoint/issues/2) and [invitation issue #3](https://github.com/nissifield/ftlbird-waypoint/issues/3) are added. No deployment work is included.

| Attack | Resolution and limit |
| --- | --- |
| Overpromising a supported product | README and invitation explicitly say unimplemented, design-stage, and no production-security guarantees. |
| Premature runtime or pack commitments | Removed the initial README's near-term reference-pack build implication. Contract v0.1 is the immediate milestone. The historical review has a prominent status banner. |
| Tailscale or AI security theatre | README preserves firewall, application roles, and recovery separation. Architecture guide states that external AI controls remain unimplemented requirements. |
| Scope expansion | No additional target, runtime selection, pack catalogue, agent runtime, production pilot, or deployment artifact. |
| Unclear contribution paths | README and CONTRIBUTING provide bounded tasks; four templates guide evidence and scope. No AI or coding prerequisite. |
| Maintainer overload | One technical coordination issue, issue-first substantial proposals, no automatic assignments, deadlines, or broad backlog. |
| Licensing/governance ambiguity | No licence or named maintainer is invented. Open licensing decision and explicit human decision/release authority. |
| Public security leakage | Security template is restricted to hypothetical architecture questions; actual concerns use the private-reporting policy. No reporting address is inferred from commit metadata. |

### Held-out counterexample review

A newcomer offers a privileged private pack, wants a local AI to make persistent in-container fixes, and proposes a live family pilot because Tailscale is “secure.” The candidate guidance rejects each inference: private is not trusted, durable state must be versioned, local AI has no special authority, controls are unimplemented, and pilot participation is discovery only. The safe next action is a sanitised contract question, with sensitive concerns routed privately.

This is a bounded adversarial document review by the authoring assistant, not an independent human security audit or a runtime test. Human contract review remains outstanding.

## Deterministic checks and limits

- Checked repository-relative Markdown destinations and heading anchors, plus same-repository absolute file links against the candidate tree.
- Parsed the four issue templates' YAML frontmatter and checked their name, description, and title fields. No uncreated custom labels are required by a template.
- Compared the archived architecture review after its banner with the supplied source; original content is preserved.
- Inspected the full documentation diff and issue drafts. All candidate repository files are Markdown; no deployment code, infrastructure files, container manifests, or secret values were identified. Pattern scanning is a supplementary check, not proof that all possible secrets can be detected.
- Ordinary whitespace checking identifies four retained two-space Markdown line breaks in the original review. With those intentional line breaks allowed, the whitespace check passes.
- Retrieved the five external technical-reference destinations and the GitHub template-documentation destination successfully. This validates reachability, not version-specific platform compatibility.

No production tests, backup/restore trials, AI-isolation checks, policy enforcement tests, human operator interviews, or live GitHub template UI preview were performed. Private reporting availability remains UNKNOWN. [Collaboration setup](community-setup.md) distinguishes documented labels/categories from actual configuration; invitation pinning is unavailable through the exposed tools.

## Reversibility and acceptance

Documentation changes can be reverted through a reviewed Git change. New issues can be edited or closed without replacing #1. This foundation does not accept the Platform Contract or make an official software release.

| Criterion | Verdict | Evidence |
| --- | --- | --- |
| Public purpose clear and truthful | PASS | README pitch, purpose, and audience. |
| Design-stage status unmistakable | PASS | README Design-stage status; architecture guide and review banner. |
| Specific, safe contribution paths | PASS | CONTRIBUTING, four issue templates, SECURITY, invitation. |
| Binding architecture constraints preserved | PASS | README Architectural commitments; governance trust levels; architecture AI boundary. |
| No secrets, deployment code, or unsupported implementation claims added | PASS | File inventory, diff and content review; historical material explicitly framed as design. |
| Licensing position not invented | PASS | Open licensing ADR and decision issue; no licence file. |
| Existing work preserved and duplicate issues avoided | PASS | Baseline tree comparison, preserved review, unchanged #1. |

**Overall: CONDITIONAL PASS for the requested foundation.** Documentation and issue content meet the acceptance bar; custom labels, Discussions/category setup, and invitation pinning are documented rather than configured. These limitations do not prevent design feedback through #1 and the invitation issue.
