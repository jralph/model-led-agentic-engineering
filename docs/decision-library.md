# Decision library

A model-led project needs a durable place to preserve the decisions that matter after the original conversation has disappeared.

The `.decisions/` directory is an append-only, machine-readable library of **human-accepted semantic Decisions**.

It is deliberately narrower than general documentation.

Code tells us what the system currently does. Tests tell us which behaviour is mechanically enforced. Architecture documentation explains how the system fits together. The decision library preserves **why important constraints and choices exist**.

## The core rule

> **Agents may reason about, originate, recommend and draft proposed semantic Decisions. A semantic Decision becomes authoritative only through human acceptance.**

The authority boundary is not who first generated the idea or typed the record.

An agent can propose a better architectural, behavioural or security Decision than the human originally considered. That proposal remains non-authoritative until a human accepts the semantic choice.

Human acceptance may happen:

- before the record is written, through an explicit human Decision/instruction;
- during review of an agent-proposed Decision;
- through another explicit acceptance workflow.

Agents may also make ordinary local implementation decisions inside delegated authority without requiring separate human approval for every choice.

None of these alone prove human acceptance:

- an agent recommendation;
- an implementation detail introduced by an agent;
- existing code;
- an old document;
- an unanswered suggestion;
- a commit authored by an agent;
- presence on a particular branch;
- metadata claiming approval.

If semantic authority remains unclear, the agent should surface the ambiguity.

## Why an immutable library?

Engineering decisions accumulate history.

A choice that looks unnecessary six months later may exist because an earlier implementation failed, a security boundary was deliberately tightened, or an apparently simpler approach had an unacceptable trade-off.

Normal documentation is often edited in place. That preserves the current explanation but loses the path that led there.

Decision records work more like database migrations:

- a proposed Decision can change before human acceptance;
- the project's acceptance mechanism records when the Decision becomes authoritative;
- after acceptance, its record is immutable;
- a later Decision can supersede it;
- the original record remains part of history.

This lets humans and agents reconstruct not only **what is currently authoritative**, but **how the system arrived there**.

## Human acceptance is the authority boundary

A semantic Decision becomes authoritative when a human accepts it.

Model-led does not prescribe the mechanism that represents this event.

A pull request is one useful implementation because it can carry three related things together:

1. **Decisions** — what the system is being asked to believe or preserve;
2. **implementation** — how those Decisions are expressed in software;
3. **evidence** — why the implementation is considered acceptable.

In a repository whose policy guarantees human approval for Decision changes, merging that pull request can represent the human acceptance event.

That is a workflow property, not a semantic property of Git itself.

A direct-to-main workflow can also be valid when the human has already explicitly made or accepted the Decision before an agent records it.

Useful provenance includes:

- how/when human acceptance occurred;
- the implementation that accompanied the Decision;
- discussion and review around it;
- the evidence available at the time;
- later changes that supersede it.

For team repositories, `.decisions/**` should normally require an explicit human acceptance control such as CODEOWNERS/required review or an equivalent platform mechanism.

## Decision records

Records are Markdown files with YAML front matter.

Example:

```markdown
---
id: DEC-20261005-185500-resolver-authority
title: Speculative results cannot silently become authoritative
type: invariant
# Optional provenance:
author: agent:example
accepted_by:
  - human:example
recorded_at: 2026-10-05T18:50:00+01:00
accepted_at: 2026-10-05T18:55:00+01:00
scope:
  areas:
    - resolver
    - cache
  paths:
    - api/src/lib/resolver/**
supersedes: []
related: []
tags:
  - safety
  - resolution
---

## Decision

A speculative result may terminate resolution only when it satisfies the
explicitly accepted confidence boundary. Otherwise the authoritative resolver
remains responsible for the result.

## Why

The speculative path exists to reduce latency. Allowing uncertainty to change
execution semantics would trade latency for incorrect actions.

## Consequences

- uncertain results fall through rather than execute;
- qualification must count incorrect execution separately from refusal;
- weakening this boundary requires a new decision.
```

The prose and even the proposed semantic choice may be AI-originated. The Decision becomes authoritative only through human acceptance.

## Decision metadata

The canonical schema requires only fields that describe the semantic Decision itself:

- `id` — stable unique identifier;
- `title` — concise human-readable Decision;
- `type` — the kind of Decision;
- `supersedes` — earlier Decisions replaced by this one, or an empty list.

Everything else is optional provenance or indexing metadata.

Optional provenance fields include:

- `author` — who originated/authored the record or proposal;
- `accepted_by` — human(s) recorded as accepting the Decision;
- `recorded_at` — when the record/proposal was written;
- `accepted_at` — when human acceptance was recorded;
- `decided_at` — retained as an optional legacy/general timestamp for backwards compatibility.

Optional indexing fields include:

- `scope.areas`;
- `scope.paths`;
- `related`;
- `tags`.

Provenance metadata is descriptive only. It does not independently establish human acceptance or semantic authority.

Where repository/review history already provides trustworthy provenance, prefer that rather than duplicating the same workflow state in YAML. Front matter remains useful where external provenance is unavailable, when portability matters, or when the project deliberately wants the metadata inline.

The schema is intentionally small. More metadata should be added only when real tooling needs it.

## Initial decision types

### invariant

Something that must remain true until explicitly superseded.

These are particularly valuable for agents because they constrain future implementation.

### architecture

A durable structural or technology decision.

### behaviour

An accepted user-visible or system behaviour.

### interface

A contract between components or systems.

### security

A trust, permission, privacy or security decision.

### operational

A reliability, release, observability or operational decision.

### product

A product-boundary decision that materially constrains engineering behaviour.

### process

A decision about how engineering work itself is carried out.

Types are classifications, not different levels of importance.

## Supersession, not mutation

Accepted records are never updated to say they are obsolete.

There is intentionally no mutable `status: superseded` field.

A new record instead declares:

```yaml
supersedes:
  - DEC-20261005-185500-resolver-authority
```

The current state is derived from the decision graph.

This preserves history and makes the authoritative set mechanically calculable.

Keep decisions small enough that they can be superseded cleanly. Avoid partial overrides of paragraphs inside older records.

## Scope

Scope lets tooling select high-signal decisions for a task.

For example:

```yaml
scope:
  areas:
    - analytics
  paths:
    - api/src/analytics/**
    - shared/analytics/**
```

An agent changing one of those paths could automatically receive every active decision that applies there.

Scope is advisory context selection, not proof that a decision is irrelevant everywhere else.

An invariant with broad system impact may intentionally omit paths or use a broad area.

## Active decisions

A Decision is active when:

- it has received human acceptance and entered the project's authoritative Decision set; and
- no later human-accepted Decision supersedes it.

A tool should derive this rather than mutate records.

Useful future commands might include:

```text
decisions list
decisions active
decisions show <id>
decisions for <path>
decisions graph
decisions validate
decisions context <path>
```

The exact tooling is not part of the current methodology.

## Immutability rules

Once a Decision has received human acceptance and entered the authoritative Decision set:

- do not modify it;
- do not delete it;
- do not rename it;
- do not change its metadata;
- do not "fix" its wording.

If wording was misleading enough to matter, add a new decision that supersedes it.

A validator can enforce this cheaply by comparing a pull request against its base:

```text
new .decisions file       allowed
modified .decisions file  rejected
deleted .decisions file   rejected
```

This applies to accepted records, not proposals that are still being refined before human acceptance.

## Decisions can adopt reusable Rulesets

A Project Decision may adopt an exact local snapshot of a reusable Ruleset.

Rulesets are distinct from Decisions:

- a Ruleset is reusable normative material that may evolve upstream;
- a Ruleset snapshot is an exact local copy;
- the Project Decision is what gives that snapshot semantic authority.

For example:

> Adopt the local `company-security/abc123` Ruleset snapshot for production services.

The adopted Rules derive their Project authority from that Decision.

The snapshot should be complete and local. Do not make the Decision depend on a mutable upstream branch, symlink, `latest` reference or remote fetch.

If the Project later adopts `company-security/xyz789`, add that new snapshot alongside `abc123` and accept a new Decision that supersedes or updates the earlier adoption. Keep the old snapshot because historical Decision authority must remain reconstructable.

See [Rules and Rulesets](rulesets.md).

## Decisions are not a replacement for everything else

Do not put every implementation detail into the library.

A decision record is useful when forgetting the decision would make a future engineer or agent likely to:

- change important behaviour;
- weaken a boundary;
- repeat a rejected design;
- misunderstand an architectural constraint;
- make the wrong trade-off;
- misinterpret accepted risk.

Routine code choices belong in code.

Detailed current architecture belongs in architecture/context documentation.

Future ideas belong in a roadmap.

The decision library preserves durable **human intent**.

## Decision review

The decision library also changes what deserves scarce human review attention.

As implementation becomes cheaper, humans do not necessarily add the most value by manually inspecting every generated line.

Human review should prioritise questions such as:

- Do we want the system to behave this way?
- Is this invariant correct?
- Is the trust boundary acceptable?
- Is this the abstraction we want future work to inherit?
- Are the trade-offs and residual risks acceptable?
- Does this decision conflict with another active decision?

Agents can perform exhaustive implementation review against those decisions:

- does the diff conform to the new decisions?
- does it violate any existing active decision?
- are important behaviours untested?
- did implementation silently broaden scope?
- does the supplied evidence support the claims?

Humans still inspect code directly whenever risk, novelty or judgement warrants it.

See [Decision-first review](decision-review.md).
