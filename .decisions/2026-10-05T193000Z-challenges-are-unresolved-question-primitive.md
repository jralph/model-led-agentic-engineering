---
id: DEC-20261005-203000-challenges-are-unresolved-question-primitive
title: Challenges are the unresolved-question primitive
type: process
decided_at: 2026-10-05T20:30:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - challenges
    - review
supersedes: []
related:
  - DEC-20261005-185500-human-decision-authority
  - DEC-20261005-201010-decision-first-review-core-practice
tags:
  - challenges
  - agents
  - decisions
---

## Decision

Model-led agentic engineering defines a Challenge as the semantic concept of questioning the current Decision set, the absence of a Decision where human authority appears necessary, implementation, evidence, observed behaviour or an engineering opportunity without changing the semantic model.

The methodology does not prescribe a specific file, folder or storage format for Challenges.

Challenges may be created by humans or agents.

A Challenge may remain unresolved and does not need to contain a proposed solution.

When resolving a Challenge would require a semantic model change, a human-authored Decision is required. When the active Decisions already define the correct behaviour, implementation or evidence may be corrected without creating a new Decision.

## Why

Agentic engineering needs a safe place for machines to surface discoveries without silently acquiring authority to change the system model.

Traditional Issues often mix observation, solution and implementation work. That can encourage premature solutionising and makes it difficult to distinguish "something may be wrong" from "we have decided what to do".

Challenges preserve unresolved knowledge while keeping the human Decision boundary intact.

They also provide a natural representation for bugs: either implementation violates an existing Decision, or the bug exposes behaviour that has not yet been decided.

## Consequences

- agents may autonomously raise Challenges;
- agents must not resolve semantic ambiguity by inventing a Decision;
- a Challenge can target an existing Decision, the absence of a needed Decision, implementation, evidence, behaviour, opportunities or unknowns;
- Challenge records are mutable during investigation and are not part of immutable Decision history;
- a Challenge can resolve with no change, an implementation correction, a Decision change, evidence correction, accepted risk or a split/duplicate;
- meaningful semantic implementation changes still require a Decision basis;
- the methodology does not mandate a particular storage mechanism for Challenges because Challenge is a semantic primitive rather than a repository file type.
