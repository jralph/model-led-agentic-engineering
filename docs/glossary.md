# Glossary

## Agent

An AI system acting with enough context and tooling to carry out multi-step work rather than only returning a single completion.

## Authority

The decisions a mode or agent is allowed to make without escalating.

## Engineering intent

The desired behaviour, constraints, trade-offs and rationale that an implementation is meant to express.

## Global intent

The coherent direction of the whole system: how local decisions fit together and which trade-offs are accepted.

## Invariant

A property that must remain true across implementation changes.

## Local intelligence

Useful reasoning contributed by an agent within a bounded problem: research findings, implementation choices, edge cases, alternatives or critique.

Local intelligence can alter the global model when the human deliberately integrates it.

## Mode

A declared type of agentic work with a particular objective and authority boundary.

Examples: Explore, Research, Specify, Implement, Review and Qualify.

## Model

The human-owned, language-independent semantic understanding of a system.

Not an LLM.

## Model drift

A meaningful difference between the intended semantic model and the implemented behaviour.

## Qualification

Gathering evidence to determine whether an implementation supports specific engineering claims.

## Semantic correction

A correction to behaviour, architecture, algorithms, boundaries or invariants rather than ordinary syntax or local coding detail.

## Semantic throughput

The rate at which correct engineering intent becomes validated software outcomes.

This is a concept rather than a fully defined metric.

## Specification

A durable projection of the model created for a particular piece of work.

It does not need to contain the whole system model.

## Decision-first review

A review model where human attention prioritises engineering decisions, semantic changes, trade-offs and accepted risk, while agents can perform exhaustive implementation-conformance review against those decisions.

It does not prohibit direct human code review.

## Implementation workflow

The process used to turn intent into software, such as spec-driven development, autonomous agent execution, conventional tickets or manual coding.

Model-led agentic engineering does not prescribe one implementation workflow.


## Challenge

A semantic primitive that questions the current Decision set, the absence of a Decision where human authority appears necessary, implementation, evidence, observed behaviour or an engineering opportunity without changing the authoritative semantic model.

A Challenge is not defined by a particular file, folder or storage format. Challenges may be raised by humans or agents and may remain unresolved while evidence is gathered.

## Decision basis

The accepted Decisions that authoritatively govern a meaningful semantic implementation change.

Proposed Decisions may guide candidate implementation, review and qualification while under consideration, but they do not join the authoritative Decision basis until human acceptance.

A Challenge may reveal that no adequate Decision basis exists. An agent may propose the missing Decision but must not make it authoritative without human acceptance.


## Intent

A human-owned, mutable statement of an outcome being pursued.

Intent is pre-decisional: it can guide exploration, research and implementation planning, but it does not itself authorise new semantic behaviour. Meaningful semantic implementation requires a sufficient Decision basis.

Intent is a semantic concept rather than a prescribed repository file type.

