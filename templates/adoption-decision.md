---
id: DEC-YYYYMMDD-HHMMSS-adopt-model-led
title: Adopt Model-led agentic engineering
type: process
decided_at: YYYY-MM-DDTHH:MM:SS+00:00
author: <human decision owner>
scope:
  areas:
    - engineering-method
supersedes: []
related: []
tags:
  - model-led
  - adoption
---

## Decision

This repository adopts Model-led agentic engineering as its engineering governance method.

Future meaningful semantic implementation must have a sufficient Decision basis. Intent remains human-owned; Challenges may be raised by humans or agents; agents may propose semantic Decisions; human acceptance makes those Decisions authoritative; and evidence bounds what may be claimed.

## Why

The repository existed before Model-led was adopted. Recording the adoption creates a clear provenance boundary for how engineering authority will be handled from this point forward.

This Decision does not attempt to reconstruct or legitimise historical architectural choices as prior Decisions.

## Consequences

- accepted human Decisions are recorded in `.decisions/`;
- agents may propose missing semantic Decisions when the Decision basis is insufficient, but those proposals do not become authoritative without human acceptance;
- existing repository-specific engineering practices remain in force unless separately changed;
- historical implementation is not automatically converted into Decision history.
