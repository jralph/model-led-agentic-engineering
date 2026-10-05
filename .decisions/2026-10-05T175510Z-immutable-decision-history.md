---
id: DEC-20261005-185510-immutable-decision-history
title: Accepted decision history is append-only
type: process
decided_at: 2026-10-05T18:55:10+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - decision-library
supersedes: []
related:
  - DEC-20261005-185500-human-decision-authority
tags:
  - immutability
  - provenance
---

## Decision

Decision records may be edited while they are proposals in an unmerged branch or pull request.

Once accepted into the repository's main history, a decision record is immutable.

A changed decision is represented by a new record that lists the earlier decision in `supersedes`. The earlier file remains unchanged.

## Why

The decision library should preserve how the system arrived at its current model, not only the latest explanation.

Editing decisions in place destroys historical reasoning and makes it difficult for engineers or agents to reconstruct why a constraint existed at a particular point in time.

The model is analogous to database migrations: append new history instead of rewriting accepted history.

## Consequences

- accepted decision files are not modified, renamed or deleted;
- there is no mutable `status` field;
- active/superseded state is derived from the graph;
- tooling can enforce append-only behaviour from Git diffs;
- decisions should be small enough to supersede without paragraph-level override rules.
