---
id: DEC-20261005-212900-portable-model-led-bootstrap
title: Model-led adoption is portable and conservative
type: process
decided_at: 2026-10-05T21:29:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - adoption
    - agent-guidance
supersedes: []
related:
  - DEC-20261005-211100-intent-is-pre-decisional-human-direction
  - DEC-20261005-203000-challenges-are-unresolved-question-primitive
tags:
  - adoption
  - bootstrap
  - portability
---

## Decision

Model-led adoption should require only the portable Decision library and repository agent guidance needed to preserve Model-led authority boundaries.

Bootstrap must preserve existing repository-specific instructions and must not infer historical Decisions from implementation.

When a human explicitly asks to adopt Model-led in an established repository, that request is normally sufficient human authority to draft an initial process Decision recording the adoption of Model-led. The adoption Decision becomes accepted only when the bootstrap change is accepted.

A new project created as Model-led from inception does not require a ceremonial adoption Decision.

Intent and Challenge remain storage-agnostic. Bootstrap must not create mandatory `.intents/`, `.challenges/`, `.model/` or Task structures.

## Why

Model-led is intended to govern engineering knowledge and authority without prescribing execution tooling.

A small portable bootstrap makes the method usable across existing agent harnesses and repository structures while retaining a clear provenance boundary for established projects that change their governance model.

Backfilling inferred Decisions from code would manufacture human authority that did not exist.

A new project has no previous governance history to explain, so an adoption Decision would add ceremony without useful provenance.

## Consequences

- a capable agent can bootstrap Model-led from this methodology repository;
- the target repository receives `.decisions/` semantics and reusable Model-led `AGENTS.md` guidance;
- existing project guidance is merged rather than replaced;
- established repositories will normally begin their Decision history with an explicit Model-led adoption Decision;
- new Model-led projects may begin with an empty Decision library;
- no other historical Decisions are created without explicit human judgement;
- the bootstrap remains independent of coding agent, IDE, ticket system and implementation workflow.
