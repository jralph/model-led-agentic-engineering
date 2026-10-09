# Reference framework: Decision library

> **Layer:** reference framework  
> This document defines the repository representation supplied by this project. Decision semantics belong to the [Model-led methodology](decisions.md).

The reference framework stores Decision records in:

```text
.decisions/
```

This is a portable convention, not a Model-led methodology requirement.

## What the library represents

A Decision record represents a proposed or human-accepted semantic Decision.

The presence of a file does not itself create authority.

> **Human acceptance creates semantic Decision authority.**

A project using another Model-led implementation could store the same semantic Decisions somewhere completely different.

## Record format

The framework uses Markdown files with YAML front matter.

Minimal example:

```markdown
---
id: DEC-20261009-120000-example
title: Example Decision
type: architecture
supersedes: []
---

## Decision

State the semantic choice directly.
```

The framework schema requires only:

- `id`;
- `title`;
- `type`;
- `supersedes`.

Optional provenance/indexing metadata includes:

- `author`;
- `accepted_by`;
- `recorded_at`;
- `accepted_at`;
- legacy/general `decided_at`;
- `scope`;
- `related`;
- `tags`.

Metadata is descriptive provenance. It does not independently prove human acceptance.

See [`.decisions/schema.yaml`](../.decisions/schema.yaml) and the [Decision record template](../templates/decision-record.md).

## Proposed and accepted records

A proposed Decision record may be edited while the proposal is still under consideration.

Once the Decision has received human acceptance and entered the accepted framework history, the record is append-only historical authority:

```text
add      allowed
modify   reject
delete   reject
rename   reject
```

If authority changes, add a new Decision that supersedes the earlier one.

The framework can enforce this through Git diffs, CI or another repository policy.

The methodology only requires the accepted history to remain reconstructable. Append-only files are how this framework implements that requirement.

## Acceptance and Git

Git is useful provenance, but Git state is not semantic authority by itself.

A project may choose a workflow where reviewed merge represents human acceptance.

A direct-write workflow may also be valid where the human already made/accepted the Decision before the record was written.

The framework should make its chosen acceptance mechanism explicit.

For team repositories, changes to accepted Decision history can be protected with mechanisms such as:

- required human review;
- CODEOWNERS;
- append-only validation;
- prevention of agent-only approval.

These are framework controls, not methodology requirements.

## Active Decision set

The framework derives the active Decision set from accepted history:

- an accepted Decision is active;
- a later accepted Decision may supersede it;
- supersession does not mutate the earlier record.

Tools may index scope/path metadata to retrieve high-signal Decision context.

## Rulesets use the same Decision records

The framework does not define a second Rule record type.

A Ruleset is a versioned bundle of **ordinary accepted Decision records** being distributed for reuse.

When those accepted Decisions are used as constraints, they are rules in the ordinary sense of the word.

Ruleset entries therefore use the same Decision format and schema described above.

See [Reference framework Rulesets](rulesets.md).

## Relationship to the methodology

The methodology defines:

- what a Decision means;
- how authority is obtained;
- Decision basis;
- supersession/history semantics.

This document defines:

- where this framework stores records;
- how those records are formatted;
- how a repository can validate them.

Another framework can replace every mechanic in this document without changing Model-led.
