# Roadmap

This repository is intentionally starting as a personal handbook rather than pretending to be a standard before the method has been tested properly.

## Stage 1: describe the working method

Status: **current**

Goals:

- document the mental/system model that sits above source code;
- define the agent modes I already use in practice;
- document the hand-offs between exploration, specification, implementation and verification;
- capture the distinction between implementation authorship and engineering authorship;
- provide lightweight templates without slowing the workflow down.

Success here means I can point at the repository and say, "this is approximately how I work", without needing a long verbal explanation.

## Stage 2: instrument real work

Goals:

- capture representative agentic engineering tasks from start to finish;
- record human active time separately from agent wall time;
- record clarification loops and semantic corrections;
- distinguish implementation corrections from design/model corrections;
- record which mode found defects;
- measure rework after the initial merge or release;
- identify where the model was not transferred to an agent accurately.

The important question is not "how many tokens did the agent use?" It is "how faithfully and efficiently did engineering intent become a correct outcome?"

## Stage 3: test transferability

Goals:

- use the handbook on several different projects;
- have another experienced engineer try the method;
- compare tasks with and without explicit mode separation;
- test how much of the method survives different models and harnesses;
- determine which artefacts are actually useful and which are ceremony.

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
