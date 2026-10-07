---
id: DEC-YYYYMMDD-HHMMSS-adopt-ruleset
title: Adopt <ruleset-name> Ruleset snapshot <snapshot-id>
type: process
supersedes: []

# Optional provenance / indexing:
# scope:
#   areas: []
#   paths: []
# related: []
# tags:
#   - ruleset
---

## Decision

Adopt the locally materialised `<ruleset-name>` Ruleset snapshot `<snapshot-id>` stored at:

```text
.rulesets/<ruleset-name>/<snapshot-id>/
```

for:

<project scope>

The local snapshot is the immutable material adopted by this Decision. The Decision is what gives its Rules Project authority. Its upstream source/revision is provenance recorded with the snapshot.

## Why

Why should this Project adopt this Ruleset snapshot?

Include relevant organisational standard, security, reliability, compliance or product rationale.

## Exceptions / scope

List any explicit Project-specific exclusions or scope restrictions.

Do not edit copied Rule files to encode local exceptions.

- none / <Decision reference>

## Consequences

- semantic implementation in scope must conform to the adopted Rules;
- agents resolving this Decision as part of the Decision basis must also load the referenced local Ruleset snapshot;
- upstream Ruleset changes do not affect this Project automatically;
- updating the Ruleset requires a new local snapshot and a new human-accepted Decision;
- the previous snapshot remains in the repository for historical reconstruction.
