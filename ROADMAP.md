# Roadmap

This repository contains two tracks that should evolve independently:

- the **Model-led methodology**, which must stay focused on reasoning, authority, review and Evidence;
- the **reference framework**, which is one concrete repository implementation and is expected to change more freely.

Neither should be treated as a standard before it has been tested properly.

## Stage 1: describe the working method

Status: **current**

### Methodology goals

- document the mental/system Model that sits above source code;
- define Intent, Challenge, Decision, Decision basis, authority, review and Evidence clearly;
- define the agent modes I already use in practice;
- document the hand-offs between exploration, implementation, review and qualification;
- capture the distinction between implementation authorship and engineering ownership;
- keep the methodology independent of repository layout and tooling.

### Reference-framework goals

- provide lightweight repository conventions and templates without slowing the workflow down;
- test whether `.decisions/`, agent guidance and reusable Decision packaging are useful implementations of the methodology;
- keep framework mechanics replaceable.

Success here means I can explain both "this is approximately how I work" and "this is one practical way to apply it" without confusing the two.

## Stage 2: instrument real work

### Methodology research

Goals:

- capture representative agentic engineering work from start to finish;
- record human active time separately from agent wall time;
- record clarification loops and semantic corrections;
- distinguish implementation corrections from Decision/model corrections;
- record which mode found defects;
- measure rework after release;
- identify where the Model was not transferred to an agent accurately;
- test whether existing Decision bases reduce unnecessary new Decisions;
- measure whether decision-first review and independent qualification improve outcomes.

### Reference-framework experiments

Use real work to test the bundled implementation:

- validate append-only Decision records and supersession graphs;
- resolve active Decisions for a changed path or semantic area;
- generate compact Decision context for agents;
- summarise proposed Decision changes in reviews;
- check implementation conformance against accepted Decisions;
- rerun conformance and qualification when a proposed Decision changes;
- prototype reusable-Decision packaging through Rulesets:
  - materialise exact Ruleset revisions as bundles of ordinary Decision records;
  - resolve adopted bundled Decisions into Project context;
  - compare Ruleset revisions during upgrades;
  - preserve historical bundles after adoption Decisions are superseded.

The framework experiments should be allowed to fail or change without redefining the methodology.

The important question is not "how many tokens did the agent use?" It is "how faithfully and efficiently did engineering intent become a correct outcome?"

## Stage 3: test transferability

Goals:

- use the handbook on several different projects;
- have another experienced engineer try the method;
- compare tasks with and without explicit mode separation;
- test how much of the method survives different models and harnesses;
- determine which artefacts are actually useful and which are ceremony;
- compare traditional code-first review with decision-first review on substantial agent-generated changes;
- test whether another engineer can change a proposed decision and have agents reliably propagate that change through implementation and evidence.

A personal workflow only becomes a methodology if somebody else can reproduce useful parts of it.

## Stage 4: stabilise terminology and controls

Potential outputs:

- a stable glossary;
- a minimum viable intent contract;
- a stable authority model for agent modes;
- evidence classes for qualification;
- a small set of metrics with demonstrated value;
- examples showing both successful and failed applications.

At this point the repository may be suitable for public release.

## Exploratory application: decision-native Git collaboration

This is **not** part of the current methodology requirement.

A future implementation may explore whether Model-led concepts can become first-class collaboration primitives rather than remaining only repository conventions. The platform would implement the methodology; it would not redefine or replace it.

A central hypothesis is that **Project** should replace **Repository** as the primary human collaboration unit, creating semantic-monorepo coherence over one Model Repository and 1..N physical Implementation Repositories.

Potential experiments:

- make Project the top-level semantic collaboration object above repositories;
- test Task as the platform work item for Intent- or Challenge-driven potential work, while keeping Task outside the Model-led methodology itself;
- allow Tasks to close after exploration/research without forcing Decisions, branches or implementation;
- test a dedicated Model Repository plus 1..N normal Implementation Repositories;
- render active and proposed Decisions as first-class Project objects;
- test semantic Areas as a human navigation model above repositories, folders and files;
- allow external harnesses to pick up a Decision Review and attach multi-repository candidate revisions;
- prototype immutable Project States and recoverable cross-repository acceptance transactions;
- replace or augment Pull Requests with Decision Reviews;
- compare several agent implementations against the same proposed decisions;
- detect likely semantic conflicts where Git has no textual conflict;
- rerun implementation, conformance review and qualification after a human changes a proposed decision;
- attach evidence levels and residual risk directly to the review;
- retain traditional code diffs as a drill-down rather than the only primary review surface.

The proposal is documented in [Potential future Git platform](docs/future-git-platform.md).

It should remain clearly separated from the core methodology until implementation and user testing show whether the model is actually useful.

## Stage 5: candidate standard

Only pursue this if earlier stages provide evidence that a more formal standard would be useful.

A future standard might define:

- required ownership boundaries;
- minimum intent artefacts;
- mode/authority declarations;
- verification independence;
- traceability between intent, implementation and qualification;
- evidence requirements for AI-generated changes;
- auditable session metadata without requiring full private transcripts.

It should not prescribe one model, coding agent, IDE or vendor.

## Open research questions

1. How much of the human semantic model needs to be externalised for another engineer or agent to reconstruct it reliably?
2. Can intent fidelity be measured without turning the process into heavyweight specification work?
3. Which mode boundaries actually reduce defects?
4. When is a separate reviewer genuinely independent enough to provide additional evidence?
5. How do we measure long-term maintainability of highly agent-generated code?
6. Does the method transfer to engineers who think less visually/systemically?
7. How do teams share ownership of the semantic model?
8. What is the minimum durable context an agent needs to make a safe change six months later?
9. Which agent-session data is useful for measurement without creating privacy or surveillance problems?
10. At what point does formalisation reduce the very throughput the method is intended to unlock?
