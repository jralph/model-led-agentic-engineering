---
id: DEC-20261007-114300-rulesets-are-reusable-local-snapshots
title: Rulesets are reusable local snapshots adopted by Project Decisions
type: process
supersedes: []
related:
  - DEC-20261005-213800-human-acceptance-makes-semantic-decisions-authoritative
tags:
  - rulesets
  - reuse
  - portability
---

## Decision

Model-led defines a **Rule** as a reusable normative statement and a **Ruleset** as a distributable collection of Rules.

Reusable upstream Rulesets may evolve over time. They are not themselves Project Decisions.

A Project adopts Rules through a human-accepted Project Decision that references an exact **local Ruleset snapshot**.

Adoption must materialise/copy the complete snapshot into the Project. Project authority must not depend on a mutable upstream location, symlink, floating reference or remote fetch.

Once a local Ruleset snapshot is referenced by an accepted Decision, that snapshot is immutable Project history.

Updating a Ruleset is additive:

- materialise the newer snapshot alongside the old one;
- retain the old snapshot;
- accept a new Project Decision adopting the newer snapshot;
- supersede the earlier adoption Decision where appropriate.

Rules in an adopted snapshot derive Project authority from the Decision that adopts that snapshot.

## Why

Reusable security, reliability, data, product and engineering standards should be distributable across Projects without weakening immutable Project Decision history.

Treating mutable upstream Rules as Decisions would create two incompatible Decision lifecycles.

Linking Project authority directly to an upstream Ruleset would also allow external changes to alter a Project without human acceptance.

Local immutable snapshots preserve exact historical authority while still allowing reusable Rulesets to evolve and be deliberately upgraded.

## Consequences

- Rules and Rulesets are distinct from Decisions;
- a Project may be scaffolded with reusable Ruleset snapshots;
- substantive Ruleset adoption is recorded as a Project Decision, including for new Projects where appropriate;
- Projects using Rulesets should keep local snapshots in a portable repository representation such as `.rulesets/<name>/<snapshot>/`;
- agents must resolve adopted Rules alongside the Decision basis;
- local exceptions are expressed as Project Decisions rather than edits to imported Rules;
- upstream updates may be discovered or proposed but never silently change Project authority;
- old snapshots remain available for historical reconstruction after an upgrade.
