---
id: DEC-20261009-111800-separate-methodology-and-reference-framework
title: Separate Model-led methodology from the reference framework
type: process
supersedes:
  - DEC-20261005-212900-portable-model-led-bootstrap
  - DEC-20261007-114300-projects-adopt-immutable-local-ruleset-snapshots
related:
  - DEC-20261005-201000-model-led-above-implementation-workflow
  - DEC-20261005-213800-human-acceptance-makes-semantic-decisions-authoritative
tags:
  - methodology
  - framework
  - decisions
  - rulesets
---

## Decision

Model-led is split conceptually into two layers.

### Methodology

The methodology defines the reasoning and authority model:

- human-owned Intent and judgement;
- Challenges;
- semantic Decisions and Decision basis;
- bounded agent authority;
- human acceptance;
- implementation conformance;
- review and Evidence.

The methodology does not prescribe repository folders, YAML schemas, Git, pull requests, `AGENTS.md`, Ruleset storage, bootstrap files or another concrete representation.

A Decision is a semantic choice that has received human acceptance. Once accepted, it constrains later work and can therefore be treated as a rule to follow. **Rule is not a separate Model-led semantic type.**

New Decisions arise when work, exploration or investigation exposes a semantic choice that requires authority. Existing accepted Decisions can simply constrain later work without being decided again.

### Reference framework

This repository also provides an optional reference framework that implements the methodology using portable repository conventions.

The framework may define:

- a `.decisions/` library;
- Decision-record YAML/front matter and schemas;
- templates and agent guidance;
- bootstrap behaviour;
- Git/review conventions;
- reusable Rulesets and their local storage.

Within the framework, a **Ruleset** is a versioned/distributable grouping of ordinary accepted Decision records for reuse. Its entries use the same Decision representation; there is no separate Rule file type or Rule schema.

The framework may materialise immutable local Ruleset revisions and use ordinary Project Decisions to adopt or update them. These mechanics are framework choices, not Model-led methodology requirements.

## Why

The repository had started to mix semantic methodology with one particular way of storing and operating it.

That made implementation choices such as `.decisions/`, `.rulesets/` and YAML appear to be part of Model-led itself, despite the existing principle that Model-led defines what knowledge and authority must exist rather than how tools execute against them.

Rules and Decisions had also started to compete as semantic concepts. In practice, the distinction is simpler: a new Decision is the act/result of establishing semantic authority; once accepted, that Decision becomes an existing constraint or rule for future work. Rulesets only need to package those existing Decisions for reuse.

Separating methodology from framework keeps the reasoning model portable while still providing a concrete, useful way to adopt it today.

## Consequences

- methodology documentation must avoid prescribing repository layouts, file formats or Git mechanisms;
- framework documentation must clearly identify itself as one optional implementation of Model-led;
- `.decisions/`, `.rulesets/`, schemas, templates and bootstrap instructions belong to the framework;
- Rule is not a separate methodology primitive or record type;
- Rulesets package ordinary accepted Decision records rather than defining a second normative record format;
- existing accepted Decisions may be reused as rules without creating new Decisions;
- new Decisions are needed only when existing authority is insufficient;
- another tool or platform may implement the same methodology without using this reference framework.
