## Model-led agentic engineering

This repository uses Model-led agentic engineering.

> **Model-led defines what engineering knowledge and authority need to exist. It does not prescribe how tools should execute against them.**
>
> **Humans own intent, judgement and decision authority.**  
> **Agents explore, research, propose, implement, challenge and verify.**  
> **Semantic implementation must not outrun its Decision basis.**  
> **Evidence determines what can actually be claimed.**

### Authority

- **Intent** is a human-owned, mutable outcome being pursued. Agents may help refine or research it but must not silently change the objective and treat the change as authoritative.
- **Challenge** is a pre-decisional question. Humans or agents may raise Challenges against Decisions, missing Decision authority, implementation, evidence, behaviour, opportunities or unknowns.
- **Decision** is durable semantic authority once human-accepted. Agents may reason about, originate, recommend and draft proposed semantic Decisions; human acceptance is what makes them authoritative.
- **Decision basis** is the set of accepted and proposed Decisions sufficient to govern a meaningful semantic implementation change.
- **Implementation** is how current authority is realised. Ordinary local implementation choices may be delegated.
- **Evidence** bounds what may be claimed about correctness, safety, behaviour, performance or other outcomes.

### Decision library

Accepted Decisions live in `.decisions/`.

When working with Decision records:

1. Never modify, rename or delete an accepted Decision record.
2. Change accepted authority by creating a new Decision that lists the earlier Decision in `supersedes`; the new Decision becomes authoritative only through human acceptance.
3. A proposed Decision may be agent- or human-originated and may be edited before human acceptance.
4. Do not treat a commit, branch, merge, agent-authored metadata or existing code as proof of human acceptance unless the project's workflow explicitly guarantees that relationship.
5. Do not create an authoritative Decision merely because existing code appears to imply one.
6. If required semantic authority is missing, propose a Decision and/or surface a Challenge, then obtain human acceptance before making that semantic choice binding on the system.

### Working behaviour

Before making a meaningful semantic change:

1. identify the active Intent or Challenge;
2. identify the relevant Decision basis;
3. determine whether existing Decisions are sufficient;
4. if new semantic authority is required, an agent may propose the Decision, but obtain human acceptance before establishing that behaviour as authoritative implementation;
5. implement with bounded local discretion;
6. review implementation for conformance with all relevant active/proposed Decisions;
7. qualify claims with evidence appropriate to the claim;
8. report uncertainty, residual risk and unresolved Challenges.

Intent or Challenge may legitimately end after exploration/research without implementation.

### Agent modes

Use explicit modes where useful:

- **Explore** — expand the problem space; advisory authority.
- **Research** — gather evidence; evidential authority, not decisional.
- **Specify** — represent accepted human intent/Decisions or draft proposed semantic Decisions; do not treat a proposal as authority without human acceptance.
- **Implement** — translate the Decision basis into artefacts with bounded local discretion.
- **Review** — challenge conformance, assumptions and risk without redefining requirements.
- **Qualify** — establish what evidence actually demonstrates.

The same agent may move between modes, but authority must not silently expand when the mode changes.

### Review

Human review should prioritise:

- Decisions;
- semantic changes;
- trade-offs;
- accepted risk.

Agents may perform exhaustive implementation-conformance review.

Direct human code inspection remains appropriate wherever risk, novelty or judgement warrants it.

### Repository conventions

Model-led does not replace repository-specific engineering rules.

Preserve and follow this repository's existing:

- build and test instructions;
- language/framework conventions;
- security requirements;
- architecture constraints;
- release processes;
- more specific agent guidance.

Do not create `.intents/`, `.challenges/`, `.model/` or a Task abstraction unless this repository's chosen workflow explicitly calls for them.
