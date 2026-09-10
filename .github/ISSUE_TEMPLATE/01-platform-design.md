---
name: "Platform or design proposal"
about: "Propose a focused interface or architecture improvement."
title: "[Design] "
---

Read [CONTRIBUTING.md](https://github.com/nissifield/ftlbird-waypoint/blob/main/CONTRIBUTING.md) and preserve the [binding commitments](https://github.com/nissifield/ftlbird-waypoint/blob/main/README.md#architectural-commitments). This is design-stage only; do not submit deployment work, secrets, production logs, or personal data. For a security concern, use [SECURITY.md](https://github.com/nissifield/ftlbird-waypoint/blob/main/SECURITY.md) and keep the details private.

Start with [Platform Contract #1](https://github.com/nissifield/ftlbird-waypoint/issues/1). Add your comment there if it fits; do not create another Platform Contract umbrella issue.

## Problem and affected users

What needs to improve, and which existing issue or contract interface does this relate to?

## Evidence and proposal

Separate FACT with sources/versions, ASSUMPTION with a test, PROPOSAL, UNKNOWN, and RISK.

## Boundaries and alternatives

How are the single target, Tailscale/firewall/app-auth separation, AI-free lifecycle, Git/OCI trust, reproducible state, and human authority preserved? What is excluded? Compare a viable alternative for a consequential choice.

## Acceptance and failure scenario

Describe observable pass/fail evidence and one counterexample. Include migration/data impact, rollback limits, and recovery thinking if relevant. No implementation or production deployment is authorised.

## Maintainer effort and requested decision

What is the smallest next decision, and who would carry any ongoing support obligation?
