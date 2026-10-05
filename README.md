# Model-led agentic engineering

A practical methodology for engineering with AI where the human owns the system model and technical intent, while agents help explore, formalise, implement, challenge and verify it.

> **The implementation can be delegated. The engineering judgement cannot.**

This repository starts as a description of how I work. The intention is to make that process explicit enough that other engineers can adopt, test and improve it, then eventually determine whether it can mature into something closer to a repeatable engineering standard.

It is deliberately not a claim that I invented agentic engineering, spec-driven development, or any other existing discipline. It is an attempt to document a working pattern I arrived at independently and now use heavily.

## The short version

I tend to hold a language-independent model of a system in my head before I care about its implementation language.

That model includes things such as:

- what the system is trying to achieve;
- components and responsibilities;
- state and data flow;
- algorithms and calculations;
- interfaces and contracts;
- invariants;
- trust and security boundaries;
- failure behaviour;
- performance and cost constraints;
- what the system must not do.

AI changes how quickly that model can become working software.

Historically, implementation was a serial bottleneck. I could reason through a problem quickly, but turning the solution into code, tests, infrastructure and documentation still took substantial time. With capable agents, much of that translation can be delegated.

That does **not** mean delegating understanding.

The workflow becomes roughly:

```text
problem
  -> human-owned semantic model
  -> collaborative exploration
  -> explicit intent and constraints
  -> agent implementation
  -> adversarial review
  -> evidence-based qualification
  -> updated model
```

AI can contribute ideas, research, local reasoning and implementation choices. The human remains responsible for the coherence of the system and for deciding what is accepted.

## Why "model-led"?

The model is the durable understanding of the system, not a particular diagram or document.

It is closer to a modern, continuously evolving UML in your head than to a formal UML artefact. The important part is that it is semantic rather than language-specific.

If the same system were reimplemented in another language, most of the model would survive. The engineer would need to understand the new language's constraints and idioms, but not rediscover what the system is supposed to do.

See [The model](docs/model.md).

## Why "mode-based" as well?

Agents are more useful when they are not treated as one undifferentiated intelligence.

I use different interaction modes for different kinds of work:

- **Explore** — expand the problem space and challenge assumptions.
- **Research** — gather evidence and investigate unfamiliar areas.
- **Specify** — turn accepted decisions into a durable engineering brief.
- **Implement** — translate the agreed model into code and other artefacts.
- **Review** — try to find incorrect assumptions, unsafe behaviour and model drift.
- **Qualify** — gather evidence that the implementation actually satisfies the claims being made.

These modes have different authority. A research agent can discover facts but should not silently make product decisions. An implementation agent can make bounded local choices but should not casually redefine architecture. A reviewer should challenge the work, not quietly change the requirements.

See [Agent modes and authority](docs/modes.md).

## What this is not

This is not:

- "vibe coding";
- prompting until something appears to work;
- treating generated code as a black box;
- assuming AI output is correct because it compiles;
- measuring engineering ability by how many lines a human personally typed;
- replacing engineering judgement with model confidence;
- a requirement to use one specific model, IDE, harness or agent framework.

The goal is to increase the amount of **correct engineering intent that can become shipped software**, without reducing understanding or accountability.

## Handbook

Start here:

1. [Core principles](docs/principles.md)
2. [The human-owned system model](docs/model.md)
3. [Agent modes and authority](docs/modes.md)
4. [The working loop](docs/workflow.md)
5. [Externalising intent](docs/externalising-intent.md)
6. [Verification and evidence](docs/verification.md)
7. [Measuring effectiveness](docs/measurement.md)
8. [Anti-patterns](docs/anti-patterns.md)
9. [Abstract examples](docs/examples.md)
10. [Maturity model](docs/maturity.md)

Practical templates:

- [Engineering intent brief](templates/intent-brief.md)
- [Decision record](templates/decision-record.md)
- [Adversarial review brief](templates/adversarial-review.md)
- [Qualification plan](templates/qualification-plan.md)

## Current status

**v0.1: personal working methodology.**

At this stage the repository describes a method that works for me. It is not yet a standard and the maturity model is intentionally provisional.

The next stage is to make the method measurable: capture real agentic engineering sessions, identify where intent is lost between modes, quantify semantic rework, and test whether the approach remains effective across different engineers and codebases.

See [ROADMAP.md](ROADMAP.md).

## A useful test

The simplest test of whether the human still owns the engineering is:

> If the generated implementation disappeared and I had to explain the system to another capable engineer, could I explain what it does, why it behaves that way, its important constraints, and how I would recreate it?

If the answer is no, the agent probably owns too much of the model.

If the answer is yes, the fact that an agent produced the syntax is much less important.
