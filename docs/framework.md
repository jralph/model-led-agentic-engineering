# Model-led reference framework

> **Layer:** reference framework  
> This is one concrete, portable implementation of the Model-led methodology. Projects may use it, adapt it or replace it with another implementation.

The methodology defines the semantic contract.

The reference framework answers a different question:

> **How can we apply that contract in an ordinary repository today?**

It provides repository conventions, schemas, templates and agent guidance without making those mechanics part of Model-led itself.

## Framework conventions

The current reference framework uses:

- `.decisions/` for durable Decision records;
- Markdown Decision records with YAML front matter;
- append-only accepted Decision history;
- `AGENTS.md` guidance for agents;
- reusable templates for Intent, Challenge, review and qualification;
- optional Rulesets for distributing already-accepted Decisions;
- Git/review history as useful provenance when available.

These are framework choices.

A different implementation could store the same Model-led concepts in a database or platform-native object model and still follow the methodology.

## Decision library

The framework represents accepted and proposed Decisions as ordinary Decision records.

The canonical repository convention is documented in [Decision library](decision-library.md).

The framework provides:

- `.decisions/schema.yaml`;
- [Decision record template](../templates/decision-record.md);
- [portable Decision-library README](../templates/decisions-readme.md).

The file format is deliberately small. The semantic authority still comes from human acceptance, not from the presence of a file or metadata field.

## Rules and Rulesets

The framework uses **Ruleset** as a packaging/distribution concept.

It does **not** introduce a separate semantic Rule type.

A Rule is simply an already-accepted Decision being reused as a constraint.

A Ruleset is therefore:

> **a named, versioned grouping of ordinary accepted Decision records for reuse or distribution.**

Ruleset entries use the same Decision representation and semantics as any other Decision. There is no separate Rule schema or Rule file format.

The framework can materialise exact Ruleset revisions locally so that project authority never floats with a mutable upstream source.

A Project may use an ordinary Decision to adopt or update a materialised Ruleset revision.

See [Framework Rulesets](rulesets.md).

## Why snapshot Rulesets?

An upstream Ruleset may continue evolving.

A Project needs to be able to reconstruct exactly which accepted Decisions it was following at a particular point in time.

The framework therefore favours additive local snapshots:

```text
.rulesets/
  company-security/
    abc123/
      <ordinary Decision records>
    xyz789/
      <ordinary Decision records>
```

The directory shape is a framework convention, not a methodology requirement.

Old revisions remain available for history. Updating means materialising a new revision and deliberately changing Project authority through the normal Decision process.

## Bootstrap

The framework supports agent-assisted repository setup.

A user can say:

> **Set up the Model-led reference framework in this repository using https://github.com/jralph/model-led-agentic-engineering**

The bootstrap process preserves existing repository guidance and installs only the framework mechanics requested.

See [Framework adoption](adoption.md).

## Templates

Framework templates include:

- [Engineering Intent brief](../templates/intent-brief.md)
- [Decision record](../templates/decision-record.md)
- [Challenge](../templates/challenge.md)
- [Adversarial review](../templates/adversarial-review.md)
- [Qualification plan](../templates/qualification-plan.md)
- [Session measurement](../templates/session-measurement.md)
- [Ruleset adoption Decision](../templates/ruleset-adoption-decision.md)
- [Ruleset directory README](../templates/rulesets-readme.md)
- [Reusable agent guidance](../templates/model-led-agent-guidance.md)

These templates are conveniences, not Model-led semantic primitives.

## Framework portability

The framework should remain replaceable.

A Project should be able to move from this repository representation to another Model-led implementation without changing the meaning of its Intent, Challenges, Decisions, Decision basis or Evidence.

That is the test that the framework has not leaked back into the methodology.
