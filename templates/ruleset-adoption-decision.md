---
id: DEC-YYYYMMDD-HHMMSS-adopt-ruleset
title: Adopt <ruleset-name> Ruleset revision <snapshot-id>
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

Adopt the locally materialised `<ruleset-name>` Ruleset revision `<snapshot-id>` stored at:

```text
.rulesets/<ruleset-name>/<snapshot-id>/
```

for:

<project scope>

The local snapshot is a framework package of ordinary accepted Decision records. This Project Decision makes those existing Decisions applicable to the Project in the scope below. Its upstream source/revision is provenance recorded with the snapshot.

This is an ordinary Decision record; Ruleset adoption does not introduce a new Decision type.

## Why

Why should this Project adopt this Ruleset snapshot?

Include relevant organisational standard, security, reliability, compliance or product rationale.

## Exceptions / scope

List any explicit Project-specific exclusions or scope restrictions.

Do not edit imported Decision records to encode local exceptions.

- none / <Decision reference>

## Consequences

- semantic implementation in scope must conform to the accepted Decisions supplied by the adopted Ruleset revision;
- agents resolving this adoption Decision must also load the referenced Decision-record bundle;
- upstream Ruleset changes do not affect this Project automatically;
- updating the Ruleset requires a new local snapshot and a new human-accepted Decision;
- the previous snapshot remains in the repository for historical reconstruction.
