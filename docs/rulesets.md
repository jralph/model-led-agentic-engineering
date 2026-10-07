# Rules and Rulesets

Model-led Decisions are Project authority.

Some engineering constraints are useful across many Projects and should not need to be rediscovered or rewritten independently each time.

Model-led therefore distinguishes reusable **Rules** and **Rulesets** from Project **Decisions**.

> **Rule:** a reusable normative statement intended to constrain Projects that adopt it.  
> **Ruleset:** a named, distributable collection of Rules.  
> **Ruleset snapshot:** an exact, self-contained local copy of one Ruleset revision/version.  
> **Decision:** the Project's human-accepted semantic authority, including the choice to adopt a particular Ruleset snapshot.

A Rule is not automatically authoritative for a Project merely because it exists upstream.

## Why Rules are not Decisions

A Decision is immutable Project history once accepted.

A reusable Rule has a different lifecycle.

An organisation may maintain a security Ruleset and improve it over time:

- strengthen a security requirement;
- clarify wording;
- add a new Rule;
- remove an obsolete Rule;
- reorganise the upstream repository.

Calling the mutable upstream material a Decision would weaken the meaning of immutable Decision history.

Rules therefore remain reusable source material until a Project deliberately adopts a particular snapshot.

## Adoption materialises a local snapshot

A Project must not depend on mutable upstream Ruleset content for semantic authority.

Adoption copies the exact Ruleset revision into the Project.

Conceptually:

```text
upstream ruleset
  company-security @ abc123
          |
          | copy / materialise
          v
project
  .rulesets/
    company-security/
      abc123/
        ...
          |
          | human-accepted Decision
          v
  authoritative Project semantics
```

The upstream revision is provenance.

The local snapshot is the durable material the Project may evaluate or adopt.

Once materialised under a snapshot identity, it is immutable. If different content is needed, materialise a new snapshot with a different identity.

Do not use a symlink, floating branch, `latest` reference or remote fetch as the authoritative representation.

If the upstream Ruleset disappears or changes, the Project must still be able to reconstruct exactly what it accepted.

## Project Decision adopts the snapshot

Rules gain Project authority through a human-accepted Decision.

For example:

> Adopt the local `company-security` Ruleset snapshot `abc123` for all production application code.

That Decision becomes part of the Project's accepted Decision basis.

The Rules inside the adopted snapshot derive their Project authority from that adoption Decision.

The Decision should refer to the local snapshot identity/path rather than treating an external repository as the authoritative source.

The snapshot itself can carry provenance such as:

```yaml
name: company-security
source:
  location: https://example.invalid/company/security-rules
  revision: abc123
```

The exact metadata format is implementation-specific. The important requirement is that the local copy is complete and identifies the source revision/version/digest strongly enough to distinguish it from later snapshots.

## Updates are additive

A local snapshot is immutable Project material from the moment it is materialised.

Do not update a snapshot in place, whether or not it has already been adopted.

Suppose the Project currently contains:

```text
.rulesets/
  company-security/
    abc123/
```

A newer upstream revision `xyz789` becomes available.

Updating means:

1. copy the new Ruleset revision into a new local snapshot;
2. keep the old `abc123` snapshot unchanged;
3. inspect the Rule differences and implementation impact;
4. resolve conflicts or required exceptions;
5. accept a new Project Decision adopting `xyz789`;
6. supersede the earlier adoption Decision where appropriate;
7. update implementation and Evidence against the new authority.

The Project then contains both:

```text
.rulesets/
  company-security/
    abc123/
    xyz789/
```

The old snapshot remains because historical Decisions still refer to it.

This is analogous to immutable Decision history: new authority is additive rather than a rewrite of the past.

## Upstream changes do nothing automatically

A Ruleset source may continue to evolve after adoption.

That must not silently alter a Project.

If upstream moves from `abc123` to `xyz789`:

- existing Projects remain governed by their locally adopted snapshot;
- new Projects may scaffold from `xyz789`;
- existing Projects may choose to evaluate and adopt `xyz789`;
- tooling may notify Projects that a newer snapshot exists;
- tooling must not silently replace Project authority.

This avoids turning organisational guidance into an implicit remote dependency.

## Ruleset adoption and Decision basis

A meaningful semantic implementation still requires an accepted Decision basis.

A Ruleset does not replace that concept.

Instead:

```text
DEC-42
  Adopt company-security snapshot abc123
       |
       +-- SEC-001
       +-- SEC-002
       +-- SEC-003
```

`DEC-42` is the accepted Project Decision.

The Rules are authoritative in that Project because `DEC-42` adopted their exact local snapshot.

When an agent reconstructs the Decision basis, it should also load the Rules from any Ruleset snapshots adopted by those Decisions.

## Ruleset scope and exceptions

A Project may not always adopt a Ruleset globally.

The adoption Decision may define scope, exclusions or other Project-specific conditions.

For example:

> Adopt `company-security/abc123` for production services, excluding the isolated legacy migration tool described in DEC-91.

Do not edit the copied Rule files to encode a local exception.

Keep the snapshot faithful to its source.

Project-specific exceptions belong in Project Decisions so the difference between reusable Rule and local authority remains visible.

There is no implicit precedence rule between an adopted Rule and another accepted Decision.

If they conflict, that is a semantic conflict requiring human judgement.

## Project scaffolding

Rulesets make scaffolding semantic rather than only structural.

A new Project template might materialise:

- a company security Ruleset;
- a reliability Ruleset;
- a data-governance Ruleset;
- a product-family Ruleset.

The Project can then begin with Decisions adopting those local snapshots before implementation is generated.

Unlike the ceremonial "adopt Model-led" Decision, Ruleset adoption is substantive semantic authority and may be useful even for a brand-new Project.

An implementation agent can start with:

> Intent: create the service.

plus:

> Decision basis: DEC-SEC-01, DEC-REL-01, DEC-DATA-01, each adopting the relevant local Ruleset snapshot.

This lets implementation be generated inside known non-negotiables from the beginning.

## Rulesets are optional

Model-led does not require a Project to use Rulesets.

They are useful when normative constraints should be reused or distributed across Projects.

A Project with no reusable standards can continue to use only local Decisions.

## Portable repository convention

For repositories that use Rulesets, the recommended portable location is:

```text
.rulesets/
  <ruleset-name>/
    <snapshot-id>/
      ...
```

The snapshot ID should identify the exact imported revision/version/digest. For a Git-backed upstream Ruleset, use or record the exact commit SHA rather than a branch name.

For every materialised snapshot:

- do not modify it in place;
- do not replace it with a symlink or remote reference;
- add a new sibling snapshot for different content or updates.

Once a snapshot is referenced by an accepted Decision, also do not delete it while historical Decisions depend on it.

This repository layout is a portable convention, not a requirement that the upstream Ruleset itself use Git.
