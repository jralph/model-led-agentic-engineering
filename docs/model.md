# The human-owned system model

"Model" here does not mean an LLM.

It means the engineer's semantic understanding of the system.

## What the model contains

The model can include:

### Purpose

What problem is being solved and for whom?

### Behaviour

What should happen for normal, exceptional and ambiguous inputs?

### Structure

What components exist, what are they responsible for, and which boundaries matter?

### State and data

What state exists, who owns it, how it changes, and which data is allowed to cross which boundary?

### Algorithms and mechanics

What calculations, ranking, routing, matching, scheduling or other mechanics determine behaviour?

These can be specified precisely without manually writing their final implementation.

### Contracts

What does each component promise to callers, and what does it require in return?

### Invariants

What must remain true regardless of implementation?

### Failure behaviour

How does the system fail? Which failures are safe? Which must be retried? Which must stop further work?

### Security and trust

What is trusted, what is untrusted, what capabilities exist, and where must authority be checked?

### Performance and cost

Which paths are latency-sensitive? Where is work allowed to happen asynchronously? Which costs scale with usage?

### Non-goals

What is deliberately not part of the system?

Non-goals are particularly useful with agents because they prevent plausible but unwanted expansion.

## A model is not a giant specification

The aim is not to serialise every thought before implementation starts.

That would replace the coding bottleneck with a documentation bottleneck.

The useful question is:

> What information would be expensive or dangerous for the implementation agent to infer incorrectly?

Externalise that.

Routine implementation details can remain delegated.

## Mental model and external model

In individual work, the richest version of the model may remain in the engineer's head.

Durable artefacts should carry enough of it to:

- resume work after context loss;
- allow another agent to continue safely;
- allow another engineer to challenge the design;
- explain non-obvious behaviour months later;
- detect when implementation has drifted.

The external model may be spread across:

- intent briefs;
- architecture notes;
- decision records;
- tests;
- schemas;
- agent instructions;
- runbooks;
- code.

No single artefact needs to contain everything.

## Model and implementation should disagree loudly

The current implementation is authoritative for what the software actually does.

The model is authoritative for what the engineer intends it to do.

If they differ, that is useful information.

Do not quietly rewrite the intent to match accidental implementation. Decide whether the code is wrong or whether the model has legitimately changed, then reconcile them deliberately.

## Model ownership does not mean refusing AI ideas

Agents can and should contribute.

A research agent may uncover a constraint the engineer did not know. An exploratory discussion may produce a better algorithm. An implementation agent may find a much simpler local design.

The ownership rule is not "the human must invent every idea".

It is:

> The human is responsible for integrating accepted ideas into one coherent system model.

That is the part that cannot be delegated blindly.
