# Decision library

A model-led project needs a durable place to preserve the decisions that matter after the original conversation has disappeared.

The `.decisions/` directory is an append-only, machine-readable library of **accepted human decisions**.

It is deliberately narrower than general documentation.

Code tells us what the system currently does. Tests tell us which behaviour is mechanically enforced. Architecture documentation explains how the system fits together. The decision library preserves **why important constraints and choices exist**.

## The core rule

> **Agents may draft decision records. Agents must not originate accepted decisions.**

A decision can be discussed with AI, challenged by AI, researched by AI and written into a record by AI.

The authority must still come from a human.

"Human-authored" therefore means **human-originated and human-accepted**, not necessarily human-typed.

An agent must not infer that any of these constitute an accepted decision:

- its own recommendation;
- an implementation detail it introduced;
- existing code;
- an old document;
- an unanswered suggestion;
- a discussion that did not reach an explicit conclusion.

If the decision is not clear, the agent should surface the ambiguity.

## Why an immutable library?

Engineering decisions accumulate history.

A choice that looks unnecessary six months later may exist because an earlier implementation failed, a security boundary was deliberately tightened, or an apparently simpler approach had an unacceptable trade-off.

Normal documentation is often edited in place. That preserves the current explanation but loses the path that led there.

Decision records work more like database migrations:

- a proposed decision can change while it is still in a branch or pull request;
- merging accepts it;
- after acceptance, its record is immutable;
- a later decision can supersede it;
- the original record remains part of history.

This lets humans and agents reconstruct not only **what is currently authoritative**, but **how the system arrived there**.

## Pull requests are the acceptance boundary

A pull request can carry three related things together:

1. **decisions** — what the system is being asked to believe or preserve;
2. **implementation** — how those decisions are expressed in software;
3. **evidence** — why the implementation is considered acceptable.

When the pull request is accepted and merged, its new decision records are accepted with it.

This gives the records useful provenance through Git:

- the implementation that accompanied the decision;
- discussion and review around it;
- the human who proposed/accepted it;
- the evidence available at the time;
- later changes that supersede it.

For team repositories, `.decisions/**` should normally require human review through repository policy or CODEOWNERS.

For individual work, an explicit human decision followed by merging the change is sufficient.

## Decision records

Records are Markdown files with YAML front matter.

Example:

```markdown
---
id: DEC-20261005-185500-resolver-authority
title: Speculative results cannot silently become authoritative
type: invariant
decided_at: 2026-10-05T18:55:00+01:00
author: jralph
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

The prose can be AI-drafted. The decision cannot be AI-originated.

## Required metadata

The initial schema requires:

- `id` — stable unique identifier;
- `title` — concise human-readable decision;
- `type` — the kind of decision;
- `decided_at` — offset-aware date/time;
- `author` — the human source of authority;
- `supersedes` — earlier decisions replaced by this one, or an empty list.

Optional structured fields include:

- `scope.areas`;
- `scope.paths`;
- `related`;
- `tags`.

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

A decision is active when:

- it exists on the accepted branch; and
- no accepted decision supersedes it.

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

Once a decision has reached the accepted branch:

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

This applies to accepted records, not drafts that are still being refined inside the same unmerged pull request.

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
