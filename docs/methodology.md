# Model-led methodology

> **Layer:** methodology  
> This document describes the reasoning and authority model. It does not prescribe a repository layout, file format, Git workflow or tool.

Model-led agentic engineering is a governing engineering practice for working with agents while keeping semantic intent, judgement and authority coherent.

Its central contract is:

> **Model-led defines what engineering knowledge and authority need to exist. It does not prescribe how tools should execute against them.**
>
> **Humans own intent, judgement and decision authority.**  
> **Agents explore, research, propose, implement, challenge and verify.**  
> **Semantic implementation must not outrun its Decision basis.**  
> **Evidence determines what can actually be claimed.**

## What the methodology defines

The methodology defines semantic concepts and authority boundaries.

### Model

The coherent understanding of what the system is for, how it behaves, its important constraints, trade-offs, invariants and boundaries.

### Intent

A human-owned, mutable outcome being pursued.

Intent explains **what outcome is wanted**. It does not itself create semantic authority.

### Challenge

An unresolved question about the model, Decision basis, implementation, evidence or observed behaviour.

A Challenge can be raised by a human or agent because raising a question does not change authority.

### Decision

A semantic choice that becomes authoritative through human acceptance.

Agents may reason about, originate, recommend and draft proposed Decisions. Human acceptance is what makes a semantic Decision authoritative.

Once accepted, a Decision constrains future work. In ordinary language, it is now a **rule to follow**, but Rule is not a separate Model-led semantic type.

### Decision basis

The accepted Decisions that govern a meaningful semantic implementation change.

A piece of work may use only existing Decisions. A new Decision is needed only when the existing basis is insufficient for the semantic change being pursued.

### Agent authority

Agents operate with bounded authority.

They may make ordinary local implementation choices within delegated authority. They may propose semantic Decisions outside that local discretion, but cannot make those proposals authoritative themselves.

### Review

Human review prioritises semantic Decisions, trade-offs and accepted risk.

Agents can perform exhaustive conformance analysis against the accepted Decision basis and evaluate candidate implementation against proposed Decisions.

### Evidence and qualification

Claims about correctness, behaviour, safety, performance or other outcomes are bounded by the evidence actually gathered.

Agent confidence is not evidence.

## The working distinction

A useful way to separate the main concepts is:

> **Intent / Challenge:** why are we spending attention on this?

> **Decision:** what semantic choice has received human authority?

> **Decision basis:** which already-accepted choices constrain the resulting implementation?

> **Implementation:** how is that authority realised?

> **Evidence:** what has actually been demonstrated?

This means work does not imply a new Decision.

Exploration or research may end with no implementation. A Challenge may lead to an implementation correction under an existing Decision. An Intent may be achieved entirely inside an existing Decision basis.

New Decisions are required only when new semantic authority is required.

## Accepted Decisions become constraints

A Decision begins as a semantic choice under consideration.

After human acceptance it becomes part of the authoritative model and constrains later work.

That same accepted Decision may later be:

- retrieved as context;
- used as an invariant;
- checked for implementation conformance;
- reused in another context;
- packaged by a framework for distribution.

The methodology does not introduce a second semantic object called a Rule for this. Calling an accepted Decision a rule simply describes how it is being used.

## Durable history without prescribed storage

Accepted Decisions should remain reconstructable as historical authority.

Changing an accepted Decision creates new authority rather than silently rewriting what was previously accepted.

The methodology does **not** prescribe how that history is represented.

It may be implemented through:

- repository files;
- a database;
- a platform-native Decision object;
- an organisational system;
- another durable mechanism.

The bundled [reference framework](framework.md) uses repository files, but that is an implementation choice.

## What the methodology deliberately does not define

Model-led does not require:

- a `.decisions/` directory;
- a `.rulesets/` directory;
- YAML front matter;
- a particular Decision ID format;
- Git;
- pull requests;
- `AGENTS.md`;
- a Task object;
- a particular specification process;
- a particular coding agent, model, IDE or harness.

Those things may be useful implementations of the methodology.

They are not the methodology itself.

## Continue through the methodology handbook

- [Core principles](principles.md)
- [The human-owned system model](model.md)
- [Authorship, ownership and understanding](authorship-and-ownership.md)
- [Agent modes and authority](modes.md)
- [The working loop](workflow.md)
- [Decisions](decisions.md)
- [Intents](intents.md)
- [Challenges](challenges.md)
- [Decision-first review](decision-review.md)
- [Verification and evidence](verification.md)
- [Externalising intent](externalising-intent.md)
- [Measuring effectiveness](measurement.md)
- [Anti-patterns](anti-patterns.md)
- [Glossary](glossary.md)
