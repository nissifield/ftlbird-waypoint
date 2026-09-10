> **Historical design review, 9 September 2026.** The original supplied review follows unchanged. Its ratings, recommendations, illustrative schema, control flows, and MVP gates are design material, not implemented controls or deployment instructions. Runtime examples are unadopted candidates. Technical references have not been revalidated for platform compatibility in this documentation task. The current scope is Platform Contract v0.1; see the [architecture guide](architecture.md).

# Hummingbird Forge Architecture Review

**Document status:** Design review  
**Review perspective:** Senior AI and platform architecture  
**Date:** 9 September 2026  
**Proposed target:** Hummingbird only  
**Primary audience:** Offices, small businesses, community organisations, and families with average technical skills

## 1. Executive Summary

### Verdict

**Proceed into a controlled design and validation phase. Do not begin building a broad capability-pack catalogue yet.**

The concept is technically credible and has a coherent product identity:

> Hummingbird Forge is a single-target self-hosting platform that gives ordinary organisations private collaboration services while using AI only as temporary, task-scoped technical assistance.

The architecture is strongest where it deliberately limits complexity:

- One supported host platform: Hummingbird.
- One supported private connectivity layer: Tailscale.
- Curated capability packs rather than arbitrary container templates.
- Human-approved, auditable changes.
- Optional AI assistance rather than operational dependence on AI.
- Support for official, community, and privately controlled sources.

The architecture is not yet implementation-ready. Its key contracts, security boundaries, lifecycle model, and maintainer responsibilities must be specified before code or pack development accelerates.

### Assessment

| Area | Rating | Assessment |
| --- | ---: | --- |
| Product concept | 8/10 | Distinct, understandable, and relevant to a genuine self-hosting problem |
| Architectural direction | 7/10 | The major components fit together coherently |
| Security design | 5/10 | Good principles, but enforcement boundaries remain underspecified |
| Implementation readiness | 4/10 | Platform and pack contracts have not yet been defined |
| Scope control | 7/10 | Supporting one target is the correct decision |
| Long-term maintainability | 5/10 | Maintainer workload may become the principal constraint |

The greatest architectural risk is not the selection of an LLM. It is sustaining a trusted, recoverable application lifecycle across installation, configuration, upgrades, migration, backup, restoration, rollback, and eventual retirement.

## 2. Product Intent

Hummingbird Forge is intended for people who want the outcomes normally associated with managed cloud services without surrendering routine control of their applications and data.

It should allow a household or small organisation to obtain capabilities such as:

- Shared files and documents.
- Team or household communication.
- Shared calendars and contacts.
- Internal knowledge management.
- Password or secrets management.
- Backups and disaster recovery.
- Optional private document search and AI assistance.

Users should not need to become Linux, container, networking, or AI specialists. The platform should absorb infrastructure complexity while preserving understandable ownership and control.

The defining principle is:

> The applications perform the everyday work. AI is engaged temporarily when specialist technical assistance is required.

## 3. Confirmed Design Decisions

### 3.1 One supported target

Hummingbird is the only supported host target. This is a positive constraint because it permits maintainers to test one operating-system baseline, container runtime, filesystem layout, firewall model, secret-management interface, update path, and recovery procedure.

The target must nevertheless be defined as a versioned platform contract. “Fedora with scripts” is not a sufficiently stable target definition.

### 3.2 Tailscale as the private access layer

Tailscale is the standard remote connectivity mechanism. Services should normally remain unavailable from the public internet and be presented only to approved users and devices through the tailnet.

Tailscale grants can express access using users, groups, devices, destinations, protocols, ports, and supported application capabilities. Hummingbird should generate and validate policy proposals appropriate to each installed capability pack.

Tailscale is not the complete security boundary. Host firewall policy, application authentication, application-level roles, and local recovery controls remain necessary.

The product description must also be precise: applications and their data are self-hosted, while Tailscale introduces an external networking and coordination dependency.

### 3.3 Capability packs

The distributable unit is a **capability pack**, not merely a container image or YAML template. A capability pack represents a complete, maintained operational capability, including installation, configuration, security, monitoring, backup, restoration, migration, updating, rollback, and removal.

### 3.4 AI as an ad hoc external contractor

AI is not a permanent administrator and should not be embedded as hidden operational glue. It is selected for a defined work order, given limited context and permissions, asked to produce a proposed result, and disconnected when the work order closes.

The same contractor interface may route tasks to:

- A local LLM.
- An organisation-controlled private model.
- OpenAI models.
- Anthropic Claude models.
- Kimi models.
- Future approved providers.

Provider choice must not change the surrounding security contract.

### 3.5 Project maintainers retain authority

Project maintainers define standards, review official releases, maintain compatibility, respond to vulnerabilities, and approve changes to the supported platform. AI may prepare maintainer work but does not become the accountable release authority.

## 4. Target Architecture

| Layer | Primary responsibility |
| --- | --- |
| User experience | Install, configure, update, restore, inspect status, and request assistance |
| Pack manager | Validate, install, update, roll back, remove, and report on capability packs |
| Policy engine | Enforce repository trust, container privileges, network exposure, AI permissions, and approval requirements |
| Container runtime | Run services through one Hummingbird-supported mechanism |
| Private access | Combine Tailscale, host firewall policy, service presentation, and application authentication |
| Software supply chain | Retrieve source and artifacts from Git and OCI-compatible public or private services |
| Secrets broker | Supply narrowly scoped credentials without placing secrets in Git, YAML, logs, or AI context |
| AI Contractor Gateway | Create work orders, select providers, control tools and context, and collect proposed changes |
| Validation pipeline | Apply schema validation, policy checks, security checks, health tests, and restoration tests |
| Operations | Provide logging, monitoring, backup, recovery, migration, audit history, and lifecycle reporting |

### Recommended control flow

1. The operator chooses a capability or defines a maintenance task.
2. Hummingbird resolves the approved source and immutable pack version.
3. The policy engine validates provenance, permissions, network exposure, storage requirements, and compatibility.
4. Secrets are resolved through the secrets broker without entering the pack source.
5. The pack manager prepares a proposed deployment plan.
6. The operator reviews material changes.
7. Hummingbird deploys through the supported container runtime.
8. Health, backup, and access-control checks run.
9. The deployment is committed to the local desired-state record.
10. Failure triggers rollback or a clearly defined recovery state.

## 5. Critical Risks

| Risk | Severity | Architectural response |
| --- | --- | --- |
| Undefined Hummingbird platform contract | Critical | Publish a versioned platform contract before defining the pack ecosystem |
| AI modifying running containers directly | Critical | Allow inspection, but require durable changes to become declarative configuration or derived images |
| Untrusted private or community content | Critical | Require source trust levels, schema validation, digest pinning, signatures, and privilege inspection |
| Secret exposure to repositories or AI providers | Critical | Use a secrets broker, redaction, scoped credentials, and provider-independent context controls |
| Failed upgrades or unrecoverable data | Critical | Make tested backup, restoration, migration, and rollback mandatory pack capabilities |
| Treating Tailscale as the only security control | High | Retain host firewall policy, application authentication, role enforcement, and break-glass access |
| Prompt injection through logs, documents, or repositories | High | Treat all retrieved content as untrusted data and constrain the AI tool boundary |
| Maintainer overload | High | Start with one pack and impose lifecycle and support requirements before expansion |
| Hidden AI dependency | High | Require every official pack to pass normal lifecycle tests without AI |
| Unsupported hardware proliferation | High | Define one initial CPU architecture and a narrow tested hardware envelope |
| Repository and registry confusion | Medium | Specify Git source handling separately from OCI artifact and image distribution |
| Provider-specific AI behaviour | Medium | Use one work-order and validation contract across all model providers |
| Internet or Tailscale outage | Medium | Provide documented local operation and restricted break-glass recovery |
| Licensing and trademark violations | Medium | Review redistribution, image, plugin, and branding rights for every official pack |

## 6. Required Architecture Changes

### 6.1 Prohibit unmanaged mutation inside containers

AI and human administrators should not make lasting changes by editing a running container. Such changes create configuration drift, disappear when the container is replaced, and cannot be reliably reviewed or restored.

The governing rule should be:

> AI may inspect a running workload for diagnosis, but every durable change must be represented as versioned configuration, a controlled data migration, or a new derived image.

Emergency repair sessions may be supported, but they must be temporary, logged, explicitly authorised, and followed by reconciliation into the desired-state repository.

### 6.2 Separate Git sources from OCI distribution

Hummingbird must distinguish between:

- **Git repositories:** source configuration, pack definitions, documentation, customisation, and review history.
- **OCI registries:** immutable released pack artifacts and container images.

Recommended release model:

1. Maintain pack source in Git.
2. Build and test through a controlled release pipeline.
3. Publish an immutable pack release and associated images to an OCI-compatible registry.
4. Pin production references by digest.
5. Verify release signatures and provenance before installation.

Private Git repositories and private OCI registries should both be supported, but their credentials must remain outside YAML and Git history.

### 6.3 Publish the Hummingbird Platform Contract

`Hummingbird Platform Contract v0.1` should define:

- Supported Hummingbird release and upgrade policy.
- Supported CPU architecture and hardware envelope.
- Container runtime and version policy.
- Supported deployment representation.
- Required host and persistent-data paths.
- Container network and service-presentation model.
- Tailscale integration boundary.
- Host firewall behaviour.
- Secrets interface.
- Logging and metrics interfaces.
- Health-check requirements.
- Backup and restoration interfaces.
- Update, migration, rollback, and removal behaviour.
- Local recovery and break-glass procedures.

Podman with systemd Quadlet is a strong candidate for a Fedora-based platform because Quadlet integrates container, image, network, pod, and volume definitions with systemd. This is an architectural recommendation, not a confirmed Hummingbird implementation decision.

A user-friendly `pack.yaml` may remain the authoring format while Hummingbird translates validated pack intent into the selected runtime representation.

### 6.4 Introduce a policy engine

The pack manager should not install whatever a pack requests. A separate policy layer should evaluate:

- Source trust level.
- Pack signature and digest.
- Requested container privileges.
- Host mounts and writable paths.
- Device access.
- Network exposure.
- Secret requests.
- AI permissions.
- Compatibility with the installed Hummingbird version.
- Required operator approvals.

Unsafe or unsupported requests should fail closed with an understandable explanation.

### 6.5 Make AI optional by construction

Every official pack must be installable, usable, updated, backed up, restored, rolled back, and removed without invoking an LLM.

AI may improve customisation and advanced diagnosis, but it must not become a hidden prerequisite for routine operation.

## 7. Capability-Pack Model

### Proposed structure

```text
capability-pack/
├── pack.yaml
├── schema/
├── runtime/
├── configuration/
├── networking/
│   └── tailscale/
├── secrets/
├── health-checks/
├── backups/
├── migrations/
├── tests/
├── documentation/
└── ai-contract/
```

### Required metadata

Each pack should declare:

- Pack identifier, version, publisher, and schema version.
- Compatible Hummingbird versions.
- Required CPU, memory, storage, and architecture.
- Container images pinned to immutable digests.
- Persistent-data paths and ownership.
- Required networks, ports, and service names.
- Proposed Tailscale groups, tags, services, and grants.
- Application authentication requirements.
- Secrets and their permitted consumers.
- Requested host capabilities and privileges.
- Health and readiness checks.
- Backup scope, schedule guidance, and restoration procedure.
- Upgrade, migration, rollback, and removal procedures.
- Data classification and external-service dependencies.
- AI assistance policy and permitted context.
- Licensing, support status, and upstream project details.

### Source trust levels

| Level | Definition | Default treatment |
| --- | --- | --- |
| Official | Reviewed, tested, signed, and maintained by Hummingbird Forge maintainers | Installable after normal plan review |
| Approved private | Controlled by an organisation and explicitly trusted by its owner | Installable after validation against local policy |
| Community | Published by a third party without official support | Require warnings, elevated review, and policy checks |
| Unknown | Unverified source or unresolved provenance | Reject by default |

A source being private does not make it trustworthy. Trust must be granted deliberately and enforced technically.

## 8. Tailscale Security Model

Tailscale should run at the Hummingbird host layer for the first supported architecture. Capability-pack containers remain on private container networks, while an approved gateway presents selected services to the tailnet.

Recommended controls:

- No default public internet exposure.
- Tailscale grants generated from pack requirements and operator roles.
- Narrow destination-port access.
- Separate owner, administrator, staff, contractor, adult, child, and guest roles where appropriate.
- Application authentication retained behind the network boundary.
- Host firewall restrictions for LAN, WAN, and container interfaces.
- Tailscale Funnel disabled unless a future pack explicitly requires and safely supports public exposure.
- Restricted local recovery path for internet or account outages.
- Policy changes retained as auditable desired state.

Tailscale application capabilities must not be assumed to work with arbitrary third-party applications. The application must implement the corresponding capability semantics. For most initial packs, Tailscale should control network reachability while the application controls its own users and roles.

## 9. AI Contractor Control Model

### Contractor principles

The AI Contractor Gateway must treat model output as untrusted and provider behaviour as non-deterministic. It should grant only the minimum information and tools needed for the approved task.

The gateway must enforce:

1. A human-readable work order.
2. Explicitly permitted context.
3. Secret and personal-data redaction.
4. A temporary isolated workspace.
5. A restricted tool allowlist.
6. Read-only production access by default.
7. No direct access to long-lived credentials.
8. Deterministic validation of proposed changes.
9. A patch, explanation, test result, and rollback plan.
10. Human approval before production deployment.
11. Complete audit history.
12. Revocation of temporary access when the work order closes.

### Proposed work-order format

```yaml
apiVersion: hummingbird-forge/v1alpha1
kind: AIWorkOrder
metadata:
  name: upgrade-document-service
spec:
  objective: Upgrade the document service to an approved release
  providerClass: local-or-approved-remote
  allowedContext:
    - pack-configuration
    - redacted-service-logs
    - upstream-documentation
  deniedContext:
    - secret-values
    - unrelated-user-data
  permissions:
    filesystem: temporary-workspace-only
    productionRead: approved-and-audited
    productionWrite: false
    network: allowlisted-destinations
  requiredOutputs:
    - proposed-patch
    - plain-language-explanation
    - validation-results
    - migration-plan
    - rollback-plan
  approval:
    required: true
    approverRole: owner-or-maintainer
```

This is an illustrative design schema, not final configuration syntax.

### Prompt-injection boundary

Logs, documents, web pages, issue reports, repositories, comments, and container output must all be treated as potentially hostile data. Instructions discovered inside that content must not expand the work order or grant additional permissions.

The system prompt, work order, policy decision, and tool permissions must be controlled outside the model and enforced independently of model output.

## 10. Maintainer Governance

Maintainers are responsible for:

- Defining the Hummingbird Platform Contract.
- Versioning the capability-pack schema.
- Reviewing and signing official releases.
- Testing installation, update, migration, restoration, rollback, and removal.
- Monitoring upstream releases and vulnerabilities.
- Publishing compatibility and end-of-life information.
- Reviewing security-sensitive changes.
- Maintaining provider adapters for the AI Contractor Gateway.
- Deciding whether AI-generated contributions enter official releases.
- Providing incident and recovery guidance.

Every official pack creates a continuing support obligation. The project should establish acceptance criteria and a retirement process before expanding the catalogue.

## 11. Recommended MVP

The MVP should contain one complete **Private Collaboration Pack** and should prove the platform model rather than application breadth.

### MVP scope

- One Hummingbird version.
- One CPU architecture.
- One tested hardware class or narrow hardware envelope.
- One supported container-runtime model.
- Tailscale-only remote access.
- Host firewall enforcement.
- One official Git and OCI source.
- One private Git source.
- One private OCI registry.
- Secrets-broker integration.
- Pack schema and policy validation.
- Installation, updating, backup, restoration, rollback, and removal.
- Optional local and remote AI contractor paths.
- Human approval for every AI-proposed production change.

### Explicit exclusions

- Multiple Linux distributions.
- Kubernetes clusters unless selected as the single Hummingbird runtime model.
- Public marketplace scale.
- Autonomous production remediation.
- Unattended AI changes.
- Arbitrary host scripts from untrusted packs.
- Multiple networking products.
- Support for every hardware architecture.

## 12. MVP Acceptance Gates

The MVP is not complete until all of the following have been demonstrated.

### Platform and lifecycle

- [ ] A clean Hummingbird system can install the pack without AI.
- [ ] The application remains usable during ordinary operation without AI.
- [ ] Configuration is reproducible from declared desired state.
- [ ] Persistent data survives container replacement.
- [ ] A failed update rolls back to a known working version.
- [ ] The complete service can be restored onto a clean Hummingbird system.
- [ ] Pack removal preserves or deliberately disposes of data according to operator choice.

### Network and identity

- [ ] Approved Tailscale users can reach only their authorised services and ports.
- [ ] An unauthorised tailnet user or device is denied.
- [ ] Services are not unintentionally exposed on WAN or LAN interfaces.
- [ ] Application-level roles remain effective behind Tailscale.
- [ ] A restricted break-glass recovery procedure works without normal remote access.

### Supply chain and private sources

- [ ] The official pack is retrieved and verified as an immutable release.
- [ ] A private Git source can be used without storing credentials in the repository.
- [ ] A private OCI image can be pulled without exposing registry credentials.
- [ ] An unsigned, malformed, incompatible, or policy-violating pack is rejected.
- [ ] Requested privileges, mounts, ports, and secrets are shown before approval.

### AI contractor

- [ ] A local model and one remote model can use the same work-order interface.
- [ ] The model receives only the context permitted by the work order.
- [ ] Secret values are unavailable to the model.
- [ ] The model cannot write directly to production.
- [ ] AI output is converted into a reviewable patch.
- [ ] Deterministic checks reject unsafe or invalid proposed changes.
- [ ] Human approval is required before deployment.
- [ ] Temporary tools, context, and access are revoked when the task ends.
- [ ] A complete audit record identifies the task, provider, inputs disclosed, outputs, approval, and deployed change.

### Maintainer operations

- [ ] Maintainers can reproduce the release pipeline.
- [ ] Installation, upgrade, restoration, and rollback tests run automatically.
- [ ] Compatibility and end-of-life metadata are visible to operators.
- [ ] A documented process exists for urgent security updates.

## 13. Recommended Work Sequence

1. Publish `Hummingbird Platform Contract v0.1`.
2. Define the threat model and trust boundaries.
3. Define `Capability Pack Specification v0.1` and its machine-validatable schema.
4. Define repository trust, signing, and secrets policies.
5. Define the Tailscale and host-firewall integration contract.
6. Define `AI Work Order v0.1` and the Contractor Gateway boundary.
7. Build one minimal reference pack.
8. Prove backup and clean-system restoration before adding substantial features.
9. Add private Git and private OCI source support.
10. Add one local and one remote AI provider adapter.
11. Run the complete acceptance-gate suite.
12. Review maintainer workload before approving a second official pack.

## 14. Final Architectural Position

Hummingbird Forge is worth pursuing. Its defensible value does not come from YAML, containers, Tailscale, or access to multiple LLM providers in isolation.

Its value is the maintained trust layer joining them:

> Hummingbird Forge turns self-hosting into a supported product by combining curated capability packs, safe private access, reproducible operations, trusted software delivery, and temporary AI expertise under human authority.

The project should define its platform contract, capability-pack specification, trust model, and recovery model before selecting or integrating a broad set of applications.

## 15. Technical References

- [Tailscale Grants](https://tailscale.com/docs/features/access-control/grants)
- [Tailscale access control](https://tailscale.com/docs/features/access-control/acls)
- [Podman Quadlet systemd unit documentation](https://docs.podman.io/en/latest/markdown/podman-systemd.unit.5.html)
- [OCI Distribution Specification](https://github.com/opencontainers/distribution-spec)
- [Sigstore Cosign signature verification](https://docs.sigstore.dev/cosign/verifying/verify/)

---

This review distinguishes established platform behaviour documented by the referenced projects from proposed Hummingbird Forge design decisions. Product names, schemas, trust levels, and control flows described here remain design proposals until formally adopted and implemented.
