# Reference framework: Rulesets

> **Layer:** reference framework  
> Rulesets are a packaging and distribution convention. They are not a separate Model-led semantic primitive.

The Model-led methodology has **Decisions**.

Once a Decision has received human acceptance, it constrains future work. In ordinary language, that accepted Decision is a rule to follow.

The reference framework uses **Ruleset** to group those already-accepted Decision records for reuse.

> **Rule:** an accepted Decision being reused as a constraint. Not a new record type.  
> **Ruleset:** a named, versioned bundle of ordinary accepted Decision records.  
> **Ruleset revision:** an exact snapshot of that bundle.

There is no separate Rule schema, Rule file type or Rule lifecycle.

## Why Rulesets exist

Some accepted Decisions are useful across many Projects:

- security invariants;
- reliability requirements;
- data-handling standards;
- organisational constraints;
- product-family Decisions;
- engineering standards.

Those Decisions should not need to be manually rewritten in every Project.

A Ruleset packages them for distribution.

## Ruleset contents are Decision records

A Ruleset contains the same Decision records used elsewhere by the framework.

Conceptually:

```text
company-security/
  DEC-...-server-side-authorisation.md
  DEC-...-secrets-never-enter-logs.md
  DEC-...-approved-data-regions.md
```

Each item is still a Decision record.

Calling it a Rule merely describes its role when another Project follows that already-made Decision.

## Upstream Rulesets may evolve

A maintained Ruleset can gain new accepted Decisions or superseding Decisions over time.

For distribution, the framework identifies exact Ruleset revisions.

A Project must not let a mutable upstream location silently change its authority.

## Local materialisation

The reference framework may copy exact Ruleset revisions into a Project:

```text
.rulesets/
  company-security/
    abc123/
      <ordinary Decision records>
    xyz789/
      <ordinary Decision records>
```

`.rulesets/` is a framework convention, not a methodology requirement.

The local snapshot is self-contained.

Do not use:

- symlinks to mutable upstream content;
- floating branches;
- `latest`;
- remote fetches as the source of current authority.

The upstream revision/commit/digest is provenance.

The copied Decision records are the material that the Project can reconstruct later.

## Materialisation is not adoption

Copying a Ruleset revision into a Project makes it available for evaluation.

It does not by itself change Project authority.

A Project can use an ordinary human-accepted Decision to adopt a particular Ruleset revision and define its scope.

For example:

> Adopt the locally materialised `company-security@abc123` Ruleset revision for production services.

That adoption Decision is a normal Decision. It does not use a special Ruleset Decision type.

When active, the framework resolves the accepted Decision records in the adopted Ruleset revision into the Project's effective Decision context.

## Updating a Ruleset

Ruleset updates are additive.

If the Project has:

```text
.rulesets/
  company-security/
    abc123/
```

and evaluates a newer revision `xyz789`, the framework adds:

```text
.rulesets/
  company-security/
    abc123/
    xyz789/
```

The old revision remains.

If the Project chooses to move to `xyz789`, it accepts an ordinary Decision adopting the new revision and superseding/updating the earlier adoption Decision where appropriate.

This preserves historical reconstruction.

## Ruleset Decisions and Project Decisions

A Decision inside a reusable Ruleset represents semantic authority that was already established in the Ruleset's source/governance context.

The Project does not need to invent the same Decision again.

Instead, its adoption Decision says that those existing accepted Decisions now constrain this Project in the adopted scope.

This keeps the roles clear:

- **new semantic choice** → investigate/work → new Decision;
- **existing accepted choice** → can be followed as a rule;
- **many reusable accepted choices** → can be packaged as a Ruleset.

## Conflicts and exceptions

A copied Ruleset revision should remain faithful to its source.

Do not edit imported Decision records to encode Project-specific exceptions.

If a Ruleset Decision conflicts with Project authority:

- raise a Challenge;
- decide whether the Project should accept an exception;
- adopt a different Ruleset revision;
- change/supersede Project authority as appropriate;
- optionally challenge the upstream Ruleset.

Local semantic changes remain ordinary Decisions.

## Framework templates

The framework provides:

- [Ruleset adoption Decision template](../templates/ruleset-adoption-decision.md);
- [Ruleset directory README template](../templates/rulesets-readme.md).

These templates use ordinary Decision semantics and the same Decision record format.

## Relationship to the methodology

Rulesets solve a **distribution** problem, not a reasoning problem.

A different Model-led implementation could distribute accepted Decisions through an organisational policy service, database inheritance, package registry or another mechanism and never use the word Ruleset.

That would still be Model-led.
