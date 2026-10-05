---
id: DEC-20261005-185520-pr-acceptance-boundary
title: Pull request merge accepts decisions with implementation and evidence
type: process
decided_at: 2026-10-05T18:55:20+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - decision-library
    - review
supersedes: []
related:
  - DEC-20261005-185500-human-decision-authority
  - DEC-20261005-185510-immutable-decision-history
tags:
  - pull-request
  - review
  - acceptance
---

## Decision

A pull request is the acceptance boundary for new decision records.

A change may carry its human-authored decisions, implementation and qualification evidence together. When that pull request is accepted and merged, its new decisions become accepted and immutable at the same time as the implementation enters the accepted repository history.

Human review should prioritise the decisions, semantic model and accepted risk. Agents may take primary responsibility for exhaustive implementation-conformance review, with direct human code review applied where risk or judgement warrants it.

## Why

As implementation becomes cheaper, manually inspecting every generated line is not always the highest-value use of experienced human attention.

The decision layer captures the parts that require human authority: what behaviour is wanted, which boundaries matter, which trade-offs are acceptable and which risks are being accepted.

Keeping decisions, implementation and evidence in one pull request also gives the decision durable Git provenance.

## Consequences

- changes to `.decisions/**` should be conspicuous during review;
- team repositories should normally require human approval for new decision records;
- agent reviewers should check changed code against relevant active and proposed decisions;
- merge history can be used to find the implementation and discussion associated with a decision;
- human code inspection remains appropriate for high-risk, novel or weakly qualified changes.
