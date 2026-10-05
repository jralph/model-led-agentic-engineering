---
id: DEC-YYYYMMDD-HHMMSS-short-slug
title: <concise decision title>
type: invariant
supersedes: []

# Optional provenance / indexing:
# author: <record/proposal origin>
# accepted_by:
#   - <human identifier>
# recorded_at: YYYY-MM-DDTHH:MM:SS+00:00
# accepted_at: YYYY-MM-DDTHH:MM:SS+00:00
# scope:
#   areas: []
#   paths: []
# related: []
# tags: []
---

# <decision title>

> This record may represent a human-made Decision or an agent-originated proposal. It becomes authoritative only through human acceptance.

## Decision

What is the semantic Decision?

State the durable behaviour, constraint or trade-off directly. If this record is still proposed, do not treat it as authoritative until a human accepts it.

## Why

Why was this decision made?

Include the evidence or rejected alternatives that future engineers or agents are likely to otherwise rediscover incorrectly.

## Consequences

What does this require, permit or prevent?

- 
- 

## Notes

Optional context that helps interpret the decision without turning this record into mutable current-state documentation.

---

Once this Decision has received human acceptance and entered the authoritative Decision set, do not edit, rename or delete it. A later authority change creates a new Decision with this ID in `supersedes`.

A branch, commit or merge is evidence of acceptance only when the project's workflow guarantees that it represents explicit human acceptance.

Optional `author`, `accepted_by` and timestamp fields are descriptive provenance only and do not independently establish authority.
