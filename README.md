# Model-led agentic engineering

A practical methodology for engineering with AI where humans retain semantic intent, judgement and decision authority while agents explore, research, propose, implement, challenge and verify.

> **The implementation can be delegated. The engineering judgement cannot.**

## Core contract

> **Model-led defines what engineering knowledge and authority need to exist. It does not prescribe how tools should execute against them.**
>
> **Humans own intent, judgement and decision authority.**  
> **Agents explore, research, propose, implement, challenge and verify.**  
> **Semantic implementation must not outrun its Decision basis.**  
> **Evidence determines what can actually be claimed.**

This repository now deliberately contains **two layers**:

1. the **Model-led methodology**: the reasoning, authority and review model;
2. a **reference framework**: one concrete repository-based way to apply that methodology.

Keeping those layers separate is important. The methodology should survive if every file convention in this repository is replaced.

---

## Methodology

The methodology is the portable part.

It defines concepts such as:

- the human-owned semantic **Model**;
- human-owned **Intent**;
- unresolved **Challenges**;
- proposed and accepted **Decisions**;
- the accepted **Decision basis** governing implementation;
- bounded agent authority;
- decision-first review;
- Evidence and qualification.

It does **not** require Git, pull requests, YAML, `.decisions/`, `.rulesets/`, `AGENTS.md`, a Task object, a specific coding agent, or a particular implementation workflow.

See [Model-led methodology](docs/methodology.md).

### The short version

I tend to hold a language-independent semantic model of a system before I care about its implementation language.

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

Historically, implementation was a serial bottleneck. With capable agents, much of the translation from semantic intent into code, tests, infrastructure and documentation can be delegated.

That does **not** mean delegating understanding.

The engineer maintains the coherent model, agents contribute local intelligence and execution, and what is learnt feeds back into the model.

### Intent, Challenge and Decision

These concepts answer different questions.

> **Intent:** what outcome are we trying to achieve?

> **Challenge:** what deserves to be questioned or investigated?

> **Decision:** what semantic choice has received human authority?

> **Decision basis:** which already-accepted Decisions constrain the resulting implementation?

An Intent or Challenge can end after exploration or research with no implementation.

Implementation may also proceed entirely under existing accepted Decisions. **Work does not imply a new Decision.**

A new Decision is needed only when the existing Decision basis cannot authorise the semantic change being pursued.

See [Decisions](docs/decisions.md), [Intents](docs/intents.md) and [Challenges](docs/challenges.md).

### Decisions become rules for later work

A Decision is a semantic choice while it is being considered.

After human acceptance, it becomes authoritative and constrains later work.

In ordinary language, that accepted Decision is now a **rule to follow**.

Model-led does not introduce a second semantic primitive called Rule. A Rule is simply an accepted Decision being used as an established constraint.

That distinction matters because it keeps the methodology small:

```text
work / investigation
    ↓
new semantic choice
    ↓
Decision
    ↓
human acceptance
    ↓
existing constraint / rule for future work
```

### Human acceptance, not typing, creates authority

Agents may reason about, originate, recommend and draft proposed semantic Decisions.

A semantic Decision becomes authoritative only through **human acceptance**.

Acceptance is workflow-independent. It may happen before recording, during review, through team governance, or through another explicit mechanism.

The methodology does not define Git state, a merge button or a metadata field as authority.

### Decision-first review

As implementation throughput increases, human review should concentrate scarce judgement on:

- semantic Decisions;
- trade-offs;
- trust boundaries;
- accepted risk;
- whether the implementation still expresses the intended model.

Agents can perform exhaustive implementation-conformance review and qualification.

Direct human code inspection remains appropriate wherever risk, novelty or judgement warrants it.

See [Decision-first review](docs/decision-review.md).

### Evidence bounds claims

A passing test does not prove every possible claim about an implementation.

Model-led separates:

- what we intend;
- what we decided;
- what was implemented;
- what was actually demonstrated.

See [Verification and evidence](docs/verification.md).

---

## Reference framework

The repository also contains an optional **reference framework** for applying Model-led in ordinary repositories today.

It is an implementation of the methodology, not part of the methodology contract.

See [Model-led reference framework](docs/framework.md).

### Decision library

The reference framework stores Decision records under:

```text
.decisions/
```

and supplies:

- a Markdown/YAML Decision format;
- a schema;
- append-only history conventions;
- Decision templates;
- agent guidance;
- Git/review-friendly provenance.

Those are framework choices.

Another Model-led implementation could use database records, platform-native objects or a completely different storage mechanism.

See [Reference framework Decision library](docs/decision-library.md).

### Rulesets

Rulesets exist only at the framework layer.

A Ruleset is:

> **a named, versioned grouping of ordinary accepted Decision records for reuse or distribution.**

There is no separate Rule file format or Rule semantic type.

The same Decision record that represented an accepted choice can later be distributed in a Ruleset and reused as a rule.

The framework can materialise exact Ruleset revisions locally, for example:

```text
.rulesets/
  company-security/
    abc123/
      <ordinary Decision records>
    xyz789/
      <ordinary Decision records>
```

Old revisions remain available for historical reconstruction.

A Project may use a normal human-accepted Decision to adopt or update a particular Ruleset revision.

See [Reference framework Rulesets](docs/rulesets.md).

### Repository bootstrap

A capable repository agent can install the reference framework into a new or existing repository.

A user can say:

> **Set up the Model-led reference framework in this repository using https://github.com/jralph/model-led-agentic-engineering**

The framework bootstrap preserves existing repository-specific guidance and installs only the conventions needed for this implementation.

See [Reference framework adoption](docs/adoption.md).

---

## Documentation

### Methodology handbook

1. [Methodology overview](docs/methodology.md)
2. [Core principles](docs/principles.md)
3. [The human-owned system model](docs/model.md)
4. [Authorship, ownership and understanding](docs/authorship-and-ownership.md)
5. [Agent modes and authority](docs/modes.md)
6. [The working loop](docs/workflow.md)
7. [Decisions](docs/decisions.md)
8. [Intents](docs/intents.md)
9. [Challenges](docs/challenges.md)
10. [Decision-first review](docs/decision-review.md)
11. [Model-led vs other AI engineering approaches](docs/model-led-vs.md)
12. [Externalising intent](docs/externalising-intent.md)
13. [Verification and evidence](docs/verification.md)
14. [Measuring effectiveness](docs/measurement.md)
15. [Anti-patterns](docs/anti-patterns.md)
16. [Abstract examples](docs/examples.md)
17. [Maturity model](docs/maturity.md)
18. [Glossary](docs/glossary.md)

### Reference framework

1. [Framework overview](docs/framework.md)
2. [Decision library](docs/decision-library.md)
3. [Repository adoption / bootstrap](docs/adoption.md)
4. [Rulesets](docs/rulesets.md)

Framework templates:

- [Engineering Intent brief](templates/intent-brief.md)
- [Decision record](templates/decision-record.md)
- [Challenge](templates/challenge.md)
- [Adversarial review brief](templates/adversarial-review.md)
- [Qualification plan](templates/qualification-plan.md)
- [Session measurement](templates/session-measurement.md)
- [Ruleset adoption Decision](templates/ruleset-adoption-decision.md)
- [Ruleset directory README](templates/rulesets-readme.md)
- [Reusable agent guidance](templates/model-led-agent-guidance.md)

Experimental measurement work lives in [experiments/](experiments/).

---

## Exploratory applications

The methodology and reference framework are not the only possible implementation.

One exploratory direction is a **Project-first, decision-native Git platform** designed around agent-heavy engineering.

That platform is another possible implementation of Model-led. It must not redefine the methodology merely because its UI introduces objects such as Project, Task, Decision Review or Area.

See [Potential future Git platform](docs/future-git-platform.md).

---

## Current status

**v0.1: personal working methodology plus reference framework.**

The methodology describes a working engineering model that still needs broader testing.

The reference framework is deliberately provisional. Its storage conventions and templates should evolve or be replaced when evidence shows a better implementation.

The next stage is to measure real work: intent transfer, semantic corrections, human active time, qualification quality and delayed rework.

See [ROADMAP.md](ROADMAP.md).

## A useful ownership test

> If the generated implementation disappeared and I had to explain the system to another capable engineer, could I explain what it does, why it behaves that way, its important constraints, and how I would recreate it?

If the answer is no, the agent probably owns too much of the model.

If the answer is yes, the fact that an agent produced the syntax is much less important.
