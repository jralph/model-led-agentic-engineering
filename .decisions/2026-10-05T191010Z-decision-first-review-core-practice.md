---
id: DEC-20261005-201010-decision-first-review-core-practice
title: Decision-first review is a core model-led practice
type: process
decided_at: 2026-10-05T20:10:10+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - review
    - decision-library
supersedes: []
related:
  - DEC-20261005-185500-human-decision-authority
  - DEC-20261005-185520-pr-acceptance-boundary
tags:
  - review
  - decisions
  - verification
---

## Decision

Human review should treat engineering decisions, semantic changes, trade-offs and accepted risk as the primary review surface for substantial agent-generated changes.

Agents may take primary responsibility for exhaustive implementation review and decision-conformance checking, supported by independent qualification evidence.

Human code inspection remains risk-based and is required whenever direct human judgement is warranted.

Proposed decisions remain mutable during review. When a human changes a proposed decision, agents should re-evaluate the implementation and evidence against the new authoritative intent and modify the implementation where necessary.

## Why

Agent implementation throughput can exceed the amount of code humans can meaningfully inspect line by line.

Preserving the old review process without changing its centre of gravity risks making review ceremonial rather than effective.

The decisions are where human judgement is most difficult to replace: what the system should do, which boundaries matter, which trade-offs are acceptable and which risks can be accepted.

Agents are better positioned to exhaustively trace whether implementation conforms to those decisions.

## Consequences

- decision review becomes a first-class part of pull-request review;
- implementation reviewers should load relevant active and proposed decisions;
- a change to a proposed decision should trigger fresh conformance review and qualification;
- code review is not removed, but human attention is allocated according to risk and judgement value;
- future review tooling should present decision changes separately from implementation conformance.
