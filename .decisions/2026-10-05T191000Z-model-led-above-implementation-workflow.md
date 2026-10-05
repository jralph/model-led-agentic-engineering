---
id: DEC-20261005-201000-model-led-above-implementation-workflow
title: Model-led engineering governs above the implementation workflow
type: process
decided_at: 2026-10-05T20:10:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - workflow
    - specification
supersedes: []
related:
  - DEC-20261005-185500-human-decision-authority
  - DEC-20261005-185520-pr-acceptance-boundary
tags:
  - methodology
  - implementation
  - spec-driven
---

## Decision

Model-led agentic engineering does not prescribe a specific implementation workflow.

It governs human ownership of the semantic model, accepted decisions, agent authority, review and evidence.

Spec-driven development, autonomous coding agents, manual implementation and other delivery processes may operate inside model-led engineering.

A specification is one possible projection of the model for implementation; it is not the model-led methodology itself.

## Why

The purpose of model-led engineering is to preserve human technical authority and durable intent while allowing implementation mechanisms to evolve.

Binding the methodology to one implementation process would make it unnecessarily dependent on a particular tool or style of delivery and would confuse a governing engineering practice with a feature-delivery workflow.

## Consequences

- projects may adopt model-led engineering without adopting spec-driven development;
- spec-driven workflows such as Kiro Specs or GitHub Spec Kit can be used inside model-led projects;
- model-led documentation should distinguish durable decisions and ownership from temporary implementation artefacts;
- tooling should integrate with multiple implementation workflows rather than assume one.
