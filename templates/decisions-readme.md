# .decisions

This directory uses the **Model-led reference framework** to represent human-accepted semantic Decisions.

The Model-led methodology does not require this path or format; this is the portable repository convention supplied by [model-led-agentic-engineering](https://github.com/jralph/model-led-agentic-engineering).

## Rules

1. **Agents may propose semantic Decisions.** AI may research, challenge, originate, recommend and draft proposals.
2. **Human acceptance creates semantic authority.** A proposed Decision is not authoritative until a human accepts it.
3. **Acceptance is workflow-specific.** In a pull-request workflow, merge after human review is a common acceptance mechanism, but Git state alone is not proof of authority.
4. **Accepted Decision files must not be modified, renamed or deleted.**
5. **Changed authority is expressed through a new human-accepted Decision that supersedes earlier Decisions.**
6. **No mutable status field is required.** Active/superseded state is derived from the accepted supersession graph.
7. **Do not infer historical Decisions from existing code.** Implementation can reveal behaviour or missing authority, but it is not proof that a semantic Decision received human acceptance.
8. **Keep Decisions small enough to supersede cleanly.**

## Format

Decision records are Markdown with YAML front matter validated against [schema.yaml](schema.yaml).

Canonical filename:

```text
YYYY-MM-DDTHHMMSSZ-short-slug.md
```

The filename aids navigation. The `id` in front matter is the stable identity.

## Required vs optional front matter

Required semantic fields:

- `id`;
- `title`;
- `type`;
- `supersedes`.

Optional provenance/indexing fields include:

- `author`;
- `accepted_by`;
- `recorded_at`;
- `accepted_at`;
- legacy/general `decided_at`;
- `scope`;
- `related`;
- `tags`.

These fields are descriptive only and do not independently prove human acceptance. Where repository/review history already provides trustworthy provenance, prefer that history rather than duplicating workflow state in YAML.

## Accepted history

Where the accepted branch represents human-accepted authority, treat changes to already-accepted Decision records as:

```text
add      allowed
modify   reject
delete   reject
rename   reject
```

Proposed Decision records remain editable before human acceptance.

## Active Decisions

A Decision is active when:

- it has received human acceptance; and
- no later human-accepted Decision lists its ID in `supersedes`.

Tooling should derive active authority rather than modifying historical records.
