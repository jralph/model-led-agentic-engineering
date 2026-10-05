# .decisions

This directory is the project's append-only library of accepted human decisions.

Read [Decision library](../docs/decision-library.md) for the methodology.

## Rules

1. **Decisions are human-authored.** AI may discuss, challenge and draft a record, but may not originate an accepted decision.
2. **A decision is proposed while it exists only in an unmerged branch or pull request.**
3. **Merging accepts the decision.**
4. **Accepted decision files are immutable.** Do not edit, rename or delete them.
5. **Changed decisions are superseded by new records.**
6. **No mutable status field is used.** Active/superseded state is derived from the graph.
7. **Keep decisions small enough to supersede cleanly.**

## Format

Records are Markdown with YAML front matter validated against [schema.yaml](schema.yaml).

Canonical filename:

```text
YYYY-MM-DDTHHMMSSZ-short-slug.md
```

The filename aids navigation. The `id` inside front matter is the stable identity.

Offset timestamps are allowed in metadata even when filenames are normalised to UTC.

## Accepted history

A validator should treat changes relative to the accepted branch as:

```text
add      allowed
modify   reject
delete   reject
rename   reject
```

Draft records can be edited freely before their pull request is merged.

## Current authority

A decision is active if no accepted decision lists its ID in `supersedes`.

Tooling should derive current authority rather than modifying historical records.
