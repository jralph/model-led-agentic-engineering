# .decisions

This directory is the append-only library of accepted human Decisions for this repository.

The repository uses [Model-led agentic engineering](https://github.com/jralph/model-led-agentic-engineering).

## Rules

1. **Decisions require human authority.** AI may research, challenge, recommend and draft Decision records, but may not originate an accepted Decision.
2. **A proposed Decision may change before acceptance.**
3. **Acceptance makes the Decision immutable.** In a pull-request workflow, merge is normally the acceptance boundary.
4. **Accepted Decision files must not be modified, renamed or deleted.**
5. **Changed authority is expressed through a new Decision that supersedes earlier Decisions.**
6. **No mutable status field is required.** Active/superseded state is derived from the supersession graph.
7. **Do not infer historical Decisions from existing code.** Implementation can reveal behaviour or missing authority, but it is not proof that a human Decision was made.
8. **Keep Decisions small enough to supersede cleanly.**

## Format

Decision records are Markdown with YAML front matter validated against [schema.yaml](schema.yaml).

Canonical filename:

```text
YYYY-MM-DDTHHMMSSZ-short-slug.md
```

The filename aids navigation. The `id` in front matter is the stable identity.

## Accepted history

Once a Decision exists on the accepted branch, treat changes as:

```text
add      allowed
modify   reject
delete   reject
rename   reject
```

Draft Decision records remain editable before acceptance.

## Active Decisions

A Decision is active when:

- it is accepted; and
- no accepted Decision lists its ID in `supersedes`.

Tooling should derive active authority rather than modifying historical records.
