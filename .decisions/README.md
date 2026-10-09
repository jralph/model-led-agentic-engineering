# .decisions

This directory is this repository's use of the **Model-led reference framework**.

It is the framework's append-only representation of human-accepted semantic Decisions.

The Model-led methodology itself does not require this directory or file format.

Read [Decisions](../docs/decisions.md) for methodology semantics and [Reference framework: Decision library](../docs/decision-library.md) for this representation.

## Library conventions

1. **Agents may propose semantic Decisions.** They may reason about, originate, recommend and draft proposals.
2. **Human acceptance creates authority.** A semantic Decision is not authoritative until a human accepts it.
3. **Acceptance mechanism is workflow-specific.** Pull-request merge after human review is common, but Git state alone is not proof of acceptance.
4. **Accepted Decision files are immutable.** Do not edit, rename or delete them.
5. **Changed authority is superseded by new human-accepted Decisions.**
6. **No mutable status field is used.** Active/superseded state is derived from the accepted graph.
7. **Keep Decisions small enough to supersede cleanly.**

## Format

Records are Markdown with YAML front matter validated against [schema.yaml](schema.yaml).

Canonical filename:

```text
YYYY-MM-DDTHHMMSSZ-short-slug.md
```

The filename aids navigation. The `id` inside front matter is the stable identity.

Offset timestamps are allowed in metadata even when filenames are normalised to UTC.

## Required vs optional front matter

Required semantic fields:

- `id`;
- `title`;
- `type`;
- `supersedes`.

Optional provenance/indexing fields include `author`, `accepted_by`, `recorded_at`, `accepted_at`, `decided_at`, `scope`, `related` and `tags`.

`author` and `accepted_by` may name the same person, different people, several people, or be omitted entirely.

These fields describe provenance only. They do not prove human acceptance. Where the surrounding repository/review workflow already provides trustworthy provenance, that history is preferred over duplicating it in Decision metadata.

## Accepted history

Where the repository uses an accepted branch as the durable representation of human acceptance, a validator should treat changes to already-accepted Decision files as:

```text
add      allowed
modify   reject
delete   reject
rename   reject
```

Proposed records can be edited freely before human acceptance.

## Current authority

A Decision is active if it has been human-accepted and no later human-accepted Decision lists its ID in `supersedes`.

Tooling should derive current authority rather than modifying historical records.
