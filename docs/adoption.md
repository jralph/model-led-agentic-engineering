# Reference framework: repository adoption

> **Layer:** reference framework  
> This document explains how to install the bundled repository conventions. Using the Model-led methodology itself does not require these files.

The methodology is storage- and tool-independent.

The reference framework provides a portable way to represent Model-led concepts in an ordinary repository.

## Minimum framework setup

A minimal installation normally contains:

```text
.decisions/
  README.md
  schema.yaml

AGENTS.md
```

This is a framework convention.

It is **not** a claim that Model-led requires these paths.

If a repository already has compatible guidance or Decision storage, preserve it rather than recreating it destructively.

## Agent-assisted bootstrap

A user can tell a capable repository agent:

> Set up the Model-led reference framework in this repository using https://github.com/jralph/model-led-agentic-engineering. Preserve the existing repository guidance.

The source [AGENTS.md](../AGENTS.md) contains the framework bootstrap procedure.

The agent should inspect the target before making changes.

## Preserve existing repository guidance

If the target already has `AGENTS.md`, merge framework guidance into it.

Do not replace:

- build/test commands;
- formatting rules;
- language conventions;
- architecture constraints;
- release processes;
- security requirements;
- repository-specific policies.

The framework adds a way to preserve semantic authority. It does not replace existing implementation knowledge.

## Do not manufacture historical Decisions

Installing the framework does not make current code historical Decision authority.

An agent may use existing implementation to:

- reconstruct behaviour;
- identify likely assumptions;
- discover missing authority;
- raise Challenges;
- ask humans which choices should be made explicit.

It must not backfill guessed Decisions as accepted history.

## Framework adoption does not require a ceremonial Decision

A Project can use the Model-led methodology without this framework.

Likewise, installing these repository mechanics does not inherently require a Decision saying "use the framework".

If an established team considers the governance/storage change itself materially important, it may record an ordinary process Decision.

The framework includes an [adoption Decision template](../templates/adoption-decision.md) for that case, but bootstrap should not create one merely to satisfy the framework.

## New Projects

A new Project may start with an empty Decision library.

Do not invent a speculative Decision set before real semantic choices arise.

If the Project scaffolds from reusable Rulesets, those are substantive constraints and can be adopted through ordinary Decisions as appropriate.

## Intent and Challenge storage

The framework does not require `.intents/`, `.challenges/` or `.model/`.

Intent and Challenge are methodology concepts whose representation is implementation-specific.

They may live in:

- tickets;
- planning systems;
- conversations;
- briefs;
- platform-native objects;
- Markdown;
- another workflow.

## Ruleset support

Rulesets are optional framework packaging for reusable accepted Decision records.

If the user asks to materialise a Ruleset:

1. resolve an exact upstream revision/version/digest;
2. create the framework Ruleset structure when needed;
3. copy the complete Decision-record bundle into a new local revision;
4. preserve source provenance;
5. keep older revisions;
6. use an ordinary Decision to adopt/update the revision when it should become Project authority.

Never use a mutable upstream location as live Project authority.

See [Reference framework Rulesets](rulesets.md).

## Updating the framework

When updating a repository from a newer version of this reference framework:

- inspect current local conventions;
- update schemas/templates/guidance carefully;
- never rewrite accepted Decision history;
- preserve target-specific additions;
- surface semantic methodology changes separately from framework mechanics.

A framework upgrade should not silently create new semantic authority.

## Portability goal

The framework is successful if a Project can later migrate its Model-led state to another implementation without changing the meaning of its:

- Intent;
- Challenges;
- Decisions;
- Decision basis;
- Evidence.

The repository layout is replaceable. The semantic model is not.
