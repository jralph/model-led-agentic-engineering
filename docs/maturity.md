# Provisional maturity model

This is a descriptive tool for discussing adoption.

It is not a ranking of engineers, and higher is not automatically better for every task.

The levels are provisional and should change if measurement shows they are not useful.

## M0 — AI-assisted coding

AI helps with:

- completion;
- syntax;
- small functions;
- explanations;
- isolated debugging.

The human still performs most implementation directly.

## M1 — delegated implementation

The engineer delegates bounded coding tasks to an agent.

Typical pattern:

> Implement this function / endpoint / component.

The human reviews the result.

Intent is still mostly communicated task by task.

## M2 — explicit intent-driven work

The engineer provides behaviours, constraints and acceptance criteria rather than only implementation requests.

Agents can implement larger coherent slices.

Important requirements are externalised.

## M3 — model-led engineering

The engineer works from a language-independent semantic model of the system.

They deliberately delegate implementation while retaining ownership of:

- architecture;
- algorithms;
- invariants;
- boundaries;
- trade-offs;
- acceptance.

The engineer can explain the system independently of the generated syntax.

## M4 — mode-separated agentic engineering

AI participation is separated into explicit modes such as:

- exploration;
- research;
- specification;
- implementation;
- adversarial review;
- qualification.

Modes have bounded authority and deliberate hand-offs.

Different models or agents may be selected for different modes.

## M5 — measured model-led engineering

The workflow is instrumented.

The team can evaluate:

- intent fidelity;
- semantic corrections;
- human active time;
- qualification outcomes;
- delayed rework;
- where independent review adds value.

Durable model artefacts allow other engineers and future agents to reconstruct enough intent to work safely.

## Organisational maturity is separate

One engineer can operate at M4 inside an organisation that has almost no shared agentic engineering practice.

A future organisational model may need different dimensions:

- shared standards;
- safe tooling;
- access and data controls;
- auditable evidence;
- team ownership of semantic models;
- agent-friendly repositories;
- measurement without surveillance.

That is future work.
