---
id: DEC-20261005-211100-intent-is-pre-decisional-human-direction
title: Intent is pre-decisional human direction
type: process
decided_at: 2026-10-05T21:11:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - intent
    - decisions
supersedes: []
related:
  - DEC-20261005-203000-challenges-are-unresolved-question-primitive
  - DEC-20261005-185500-human-decision-authority
tags:
  - intent
  - decisions
  - authority
---

## Decision

Model-led agentic engineering defines Intent as a human-owned, mutable statement of an outcome being pursued.

Intent is pre-decisional. It may lead to exploration, research, Challenges, Decisions and implementation, but it may also end without any change to the system.

Intent does not itself authorise a meaningful semantic implementation change. Implementation must have a sufficient Decision basis. Existing accepted Decisions may be sufficient; a new Decision is required only when the work introduces a semantic choice that is not already authorised.

Intent is a semantic concept rather than a prescribed repository file type. The methodology does not require a canonical `.intents/` directory.

## Why

Desired outcomes and accepted system authority are different things.

Treating Intent as equivalent to Decision would either make every idea authoritative too early or force every piece of work to create unnecessary Decisions.

Keeping Intent mutable allows exploration to refine or reject the objective while preserving the rule that important system semantics require explicit human authority.

## Consequences

- AI may help draft, challenge and research Intent but may not silently change the human objective;
- an Intent may close, defer or be abandoned after exploration/research without a new Decision;
- an Intent may proceed directly to implementation when existing Decisions provide a sufficient basis;
- new human Decisions are required only when new semantic authority is needed;
- Intent and Challenge remain separate peer concepts;
- Model-led does not prescribe storage for Intent.
