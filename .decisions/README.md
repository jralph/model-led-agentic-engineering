# .decisions

This directory is the project's append-only library of accepted human decisions.

Read [Decision library](../docs/decision-library.md) for the methodology.

## Rules

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
