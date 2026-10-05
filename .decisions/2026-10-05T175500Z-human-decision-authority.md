---
id: DEC-20261005-185500-human-decision-authority
title: Accepted engineering decisions require human authority
type: invariant
decided_at: 2026-10-05T18:55:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - decision-library
supersedes: []
related: []
tags:
  - human-authority
  - agents
---

## Decision

An agent may research, challenge, recommend, draft and record an engineering decision only when the decision itself comes from an explicit human judgement.

An agent must not independently promote its own recommendation, an implementation detail, existing code or an unresolved discussion into an accepted decision.

## Why

Model-led agentic engineering depends on the human retaining ownership of the coherent semantic model.

Allowing agents to create accepted decisions autonomously would move authority from implementation assistance into unbounded technical governance.

The text of a decision can be AI-written. The authority behind it must be human.

## Consequences

- agents should surface ambiguity rather than inventing a decision;
- decision metadata names the human source of authority;
- repository controls may require human approval for decision changes;
- tooling must not treat "written by an agent" and "decided by an agent" as the same thing.
