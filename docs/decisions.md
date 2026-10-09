# Decisions

> **Layer:** methodology  
> This document defines Decision semantics. For the repository/file representation supplied by this project, see the [reference framework Decision library](decision-library.md).

A **Decision** is a semantic choice that becomes authoritative through human acceptance.

It answers:

> **What has been accepted as authoritative?**

## Proposal and authority are different

Agents may:

- identify that a Decision is needed;
- originate a proposed Decision;
- recommend alternatives;
- draft Decision prose;
- challenge a proposed or accepted Decision.

A proposal is not authoritative merely because an agent wrote, committed or implemented it.

Human acceptance creates semantic Decision authority.

## Human acceptance is workflow-independent

Acceptance may happen:

- before a Decision is recorded, through explicit human direction;
- during review of an agent-proposed Decision;
- through a team governance process;
- through another explicit acceptance mechanism.

Model-led does not define the storage or review mechanism.

Git, pull requests and metadata may provide useful provenance, but none is intrinsically the semantic definition of acceptance.

## Decisions become rules for later work

A new Decision usually emerges because exploration, investigation or implementation exposed a semantic choice that existing authority could not answer.

After acceptance, that choice is no longer open.

It becomes part of the Decision basis for later work and acts as a constraint or **rule to follow**.

Rule is descriptive language here, not a second Model-led object type.

This gives a simple lifecycle:

```text
Intent / Challenge / investigation
        ↓
semantic choice exposed
        ↓
proposed Decision
        ↓
human acceptance
        ↓
accepted Decision
        ↓
rule/constraint for future work
```

## Decision basis

The **Decision basis** is the set of accepted Decisions that authoritatively governs a meaningful semantic implementation change.

Work does not require a new Decision merely because work occurs.

Examples:

- a bug may be fixed because implementation violates an existing Decision;
- a refactor may preserve every existing semantic constraint;
- an Intent may be achieved entirely inside existing accepted boundaries;
- a Challenge may be resolved with stronger Evidence and no semantic change.

A new Decision is required only where the existing Decision basis is insufficient.

## Proposed Decisions and candidate implementation

Agents may explore, implement and qualify a candidate against a proposed Decision.

That can be useful because implementation often exposes whether the proposal is coherent.

But semantic behaviour that depends on the proposal must not become authoritative or releasable until the Decision receives human acceptance.

## Accepted Decision history

Accepted Decisions represent historical authority.

They should not be silently rewritten when current thinking changes.

A later Decision can supersede earlier authority while preserving the fact that the earlier Decision was once accepted.

The methodology requires that this history remain reconstructable. It does not prescribe files, IDs, YAML or a particular persistence mechanism.

## Reuse

An accepted Decision may be useful outside the context where it originated.

A framework may package accepted Decisions for distribution, scaffolding or organisational standards.

That does not create a new semantic type.

The bundled reference framework calls a grouping of reusable accepted Decision records a **Ruleset**.

See [Model-led reference framework](framework.md).
