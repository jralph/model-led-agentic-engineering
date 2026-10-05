---
id: DEC-20261005-214800-optional-decision-provenance
title: Decision provenance metadata is optional
type: process
supersedes: []
related:
  - DEC-20261005-213800-human-acceptance-makes-semantic-decisions-authoritative
tags:
  - decisions
  - provenance
  - portability
---

## Decision

The canonical Decision schema requires only fields that describe the semantic Decision itself:

- `id`;
- `title`;
- `type`;
- `supersedes`.

Provenance and indexing metadata is optional.

Optional provenance may include:

- `author` — who originated/authored the record or proposal;
- `accepted_by` — human(s) recorded as having accepted the semantic Decision;
- `recorded_at` — when the record/proposal was written;
- `accepted_at` — when human acceptance was recorded;
- legacy/general `decided_at` timestamps.

These fields are descriptive only. They do not independently establish human acceptance or semantic authority.

Where a repository or review system already provides trustworthy provenance, that workflow history is preferred over duplicating the same state in Decision front matter.

Model-led does not require Git. Other workflows may record acceptance provenance elsewhere or use optional front matter when useful.

## Why

The methodology distinguishes semantic authority from the mechanics used to record it.

Requiring author or timestamp metadata would imply that YAML fields participate in authority when they do not. An agent can write any metadata value, so those fields cannot prove human acceptance.

Keeping provenance optional also avoids coupling Model-led to Git, pull requests, a specific identity system or a particular collaboration platform.

## Consequences

- existing Decision records remain valid unchanged;
- `author` and `decided_at` are no longer required by the canonical schema;
- `accepted_by`, `recorded_at` and `accepted_at` are available as optional provenance;
- provenance metadata may be omitted entirely;
- repository/review history is preferred when it already supplies equivalent provenance;
- front matter remains useful for portability where external workflow provenance is unavailable or undesirable;
- acceptance authority continues to come from the project's human acceptance mechanism, never from metadata alone.
