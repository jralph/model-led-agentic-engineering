# Externalising intent

The largest long-term risk in model-led agentic engineering is that the authoritative model exists only in one person's head.

The answer is not to write down everything.

The answer is to externalise the parts where incorrect inference is expensive.

## What deserves to be durable

### Invariants

Anything that must survive implementation changes.

Write these as direct statements:

- "This path may recommend an action but may not execute it."
- "A retry must never create a second customer-visible operation."
- "Private content must not be emitted into analytics."

### Non-obvious decisions

If a future engineer is likely to "simplify" something back into a previously rejected design, record why the current decision exists.

### Contracts

Interface shape is useful, but behavioural contracts are more important:

- ordering guarantees;
- idempotency;
- allowed retries;
- consistency expectations;
- timeout behaviour;
- ownership of validation.

### Non-goals

Agents are very good at completing patterns.

If a plausible extension is deliberately excluded, say so.

### Acceptance conditions

Describe observable success rather than internal implementation shape where possible.

### Evidence boundaries

Record what has actually been proven and what remains assumed.

## Useful artefacts

A repository can carry the external model through several small artefacts rather than one master specification.

### Intent brief

The contract for one piece of work.

### Decision record

Why a non-obvious choice was made.

### Agent guidance

Persistent constraints an implementation or review agent should always know.

### Tests

Executable examples of behaviour and invariants.

### Schema

Machine-checkable contracts where structure matters.

### Runbook

Operational behaviour that only becomes relevant outside the code path.

### Architecture/context document

A map for reconstructing how the whole system fits together.

## Source-of-truth hierarchy

Be explicit about what wins when artefacts disagree.

A practical hierarchy is:

1. observed runtime behaviour tells you what the system currently does;
2. implemented code is the source of truth for intended current implementation;
3. tests describe enforced examples and contracts;
4. architecture and intent docs explain why;
5. roadmap documents describe proposed future behaviour.

That does not mean code is always correct.

It means a stale design document must not be presented as evidence of shipped behaviour.

## Keep documentation cheap to update

Agentic engineering can make implementation move faster than documentation.

That makes stale intent more dangerous.

Prefer:

- short documents with strong boundaries;
- generated inventories where facts can be generated;
- explicit "implemented", "proposed" and "historical" status;
- tests for machine-checkable claims;
- links to the actual implementation seam.

Avoid large prose documents that try to duplicate source code.

## Context is a projection of the model

No agent receives the whole system model.

Every prompt, spec, repository instruction and retrieved file is a projection of it.

A major part of effective agentic engineering is choosing the smallest projection that preserves the decisions relevant to the current task.

Too little context causes incorrect inference.

Too much context consumes attention and can make the important constraints harder to identify.

The goal is not maximum context.

It is **sufficient, high-signal context**.
