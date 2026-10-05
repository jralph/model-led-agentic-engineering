# Adopting Model-led in a repository

Model-led is intended to be portable.

A new or existing repository should be able to adopt the methodology without adopting a particular coding agent, IDE, ticket system, specification workflow or source-control platform.

The minimum repository-level setup is deliberately small:

- an `.decisions/` library for accepted human Decisions;
- agent guidance that preserves the Model-led authority boundaries;
- the project's existing code, tests, documentation and workflows.

Intent and Challenge are first-class Model-led concepts, but the methodology does not prescribe `.intents/`, `.challenges/` or a generic Task object.

## Agent-assisted bootstrap

A user should be able to tell a capable repository agent something equivalent to:

> Set up Model-led agentic engineering in this repository using https://github.com/jralph/model-led-agentic-engineering. Follow the bootstrap instructions in that repository's AGENTS.md and preserve the existing repository guidance.

The source methodology repository's [AGENTS.md](../AGENTS.md) contains the canonical bootstrap procedure.

The agent should inspect the target repository before making changes and adapt the setup rather than blindly replacing existing files.

## Minimum result

A bootstrapped repository should contain:

```text
.decisions/
  README.md
  schema.yaml

AGENTS.md
```

If the target repository already has an `AGENTS.md`, Model-led guidance should be merged into it rather than replacing unrelated instructions.

If the target already has a compatible decision library, the agent should preserve it and report any incompatibilities rather than destructively recreating it.

## Existing repositories usually start with an adoption Decision

For an established repository, adopting Model-led changes how future semantic authority is handled.

When a human explicitly asks to set up or adopt Model-led in that repository, that instruction is normally the **human acceptance event for the semantic choice itself**:

> Adopt Model-led agentic engineering as this repository's engineering governance method.

Use [the adoption Decision template](../templates/adoption-decision.md) to record that Decision.

The repository's normal workflow may still require review/merge before the record reaches its accepted history. That workflow requirement should be preserved, but it is not a second semantic Decision unless the project chooses to make it one.

This Decision establishes the governance boundary **from adoption onward**. It does not claim that historical implementation choices were already Model-led Decisions.

Decision provenance fields such as `author` and `accepted_by` are optional. Do not invent identity metadata merely to populate front matter; rely on the repository/review history when it already provides suitable provenance.

## Do not seed other Decisions from code

Bootstrap establishes the **mechanism** for recording Decisions.

It must not manufacture historical authority.

An agent must not inspect an existing repository, infer that architectural or behavioural choices "must have been decisions", and then write those guesses into `.decisions/` as accepted records.

Existing implementation can be used to:

- reconstruct current behaviour;
- identify likely assumptions;
- find missing Decision authority;
- raise or report Challenges;
- ask humans which existing choices should become explicit Decisions.

Only explicit human acceptance can make a semantic Decision authoritative.

Agents may propose other Decisions during bootstrap if useful, but bootstrap should not make them authoritative without human acceptance and should not manufacture historical Decision authority from code.

A newly created Project using Model-led from inception may therefore begin with **zero Decision records**. That is valid.

## Canonical Decision library

The target repository's `.decisions/` should preserve the semantics defined by [Decision library](decision-library.md):

- records are Markdown with YAML front matter;
- accepted records are immutable;
- changes happen through superseding Decisions;
- active state is derived from the supersession graph;
- agents may originate proposed semantic Decisions, but human acceptance is what makes them authoritative.

The bootstrap agent should copy the current [decision schema](../.decisions/schema.yaml) into the target repository.

Use the portable [Decision library README template](../templates/decisions-readme.md) for the target `.decisions/README.md`.

## Canonical agent guidance

The reusable target-repository guidance is in [Model-led agent guidance](../templates/model-led-agent-guidance.md).

A bootstrap agent should merge those rules into the target root `AGENTS.md`.

Do not copy this methodology repository's entire root `AGENTS.md` into a target project. It contains instructions specific to maintaining the methodology itself.

## Preserve repository-specific instructions

Model-led sits above the implementation workflow.

Bootstrap must therefore preserve instructions such as:

- build/test commands;
- formatting rules;
- language conventions;
- architecture-specific constraints;
- release processes;
- security requirements;
- repository-specific agent policies.

Model-led adds semantic authority and review rules; it does not replace useful local engineering guidance.

## No mandatory Intent or Challenge storage

Do not create these merely because Model-led has the concepts:

```text
.intents/
.challenges/
.model/
```

Intent and Challenge are storage-agnostic.

A project may represent them through:

- its existing issue tracker;
- planning documents;
- chat/conversation;
- briefs;
- a platform-native object;
- another workflow chosen by the implementor.

Only `.decisions/` has a prescribed repository representation in the current methodology.

## Existing repository adoption

For an established codebase, bootstrap should normally:

1. inspect existing repository and agent guidance;
2. add the Decision library mechanics;
3. merge Model-led agent rules;
4. record the Model-led adoption Decision from the user's explicit adoption instruction;
5. preserve the repository's normal publication/review mechanism for getting that accepted Decision record into durable history;
6. run existing validation appropriate to documentation/configuration changes;
7. report that the repository is ready for Model-led work;
8. optionally identify areas where Decision authority appears absent; agents may propose Decisions, but must not make them authoritative without human acceptance.

The repository does not need to be remodelled before useful work can begin.

Model-led can grow incrementally as real Intents, Challenges and Decisions arise.

## New project adoption

For a new project, the same minimum repository mechanics apply, but an adoption Decision is unnecessary.

The project is Model-led from inception; there is no earlier governance model whose transition needs provenance.

Do not invent a ceremonial adoption Decision or a large speculative Decision set before the project has encountered real choices.

Begin from human Intent, explore/research, and record Decisions when durable semantic authority is actually established.

This keeps the methodology lightweight rather than turning startup scaffolding into a heavyweight specification exercise.

## Updating an existing Model-led setup

When asked to update Model-led from a newer methodology source:

- inspect the target's existing Model-led guidance;
- update reusable rules and schema carefully;
- never rewrite accepted Decision records;
- preserve target-specific additions;
- surface material methodology changes to the human;
- agents may propose new semantic rules, but do not make them authoritative without human acceptance.

Bootstrap and upgrades should remain conservative.
