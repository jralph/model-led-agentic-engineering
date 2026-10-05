---
id: DEC-YYYYMMDD-HHMMSS-adopt-model-led
title: Adopt Model-led agentic engineering
type: process
supersedes: []

# Optional provenance / indexing:
# author: <record/proposal origin>
# accepted_by:
#   - <human identifier>
# recorded_at: YYYY-MM-DDTHH:MM:SS+00:00
# accepted_at: YYYY-MM-DDTHH:MM:SS+00:00
# scope:
#   areas:
#     - engineering-method
# tags:
#   - model-led
#   - adoption
---

> Use this Decision for an established project adopting Model-led. A new project created as Model-led from inception does not need a ceremonial adoption Decision.

## Decision

This repository adopts Model-led agentic engineering as its engineering governance method.

Future meaningful semantic implementation must have a sufficient Decision basis. Intent remains human-owned; Challenges may be raised by humans or agents; agents may propose semantic Decisions; human acceptance makes those Decisions authoritative; and Evidence bounds what may be claimed.

## Why

The repository existed before Model-led was adopted. Recording the adoption creates a clear provenance boundary for how engineering authority will be handled from this point forward.

This Decision does not attempt to reconstruct or legitimise historical architectural choices as prior Decisions.

## Consequences

- human-accepted semantic Decisions are recorded in `.decisions/`;
- agents may propose missing semantic Decisions when the Decision basis is insufficient, but those proposals do not become authoritative without human acceptance;
- existing repository-specific engineering practices remain in force unless separately changed;
- historical implementation is not automatically converted into Decision history.
