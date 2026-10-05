---
id: DEC-20261005-213800-human-acceptance-makes-semantic-decisions-authoritative
title: Human acceptance makes semantic Decisions authoritative
type: process
decided_at: 2026-10-05T21:38:00+01:00
author: jralph
scope:
  areas:
    - engineering-method
    - decisions
    - review
    - authority
supersedes:
  - DEC-20261005-185500-human-decision-authority
  - DEC-20261005-185520-pr-acceptance-boundary
related:
  - DEC-20261005-211100-intent-is-pre-decisional-human-direction
  - DEC-20261005-212900-portable-model-led-bootstrap
tags:
  - human-authority
  - acceptance
  - decisions
---

## Decision

Agents may reason about, originate, recommend and draft proposed semantic Decisions.

A semantic Decision becomes authoritative only through human acceptance.

Human acceptance is the semantic boundary. The mechanism used to represent that acceptance is implementation-specific.

Examples include:

- a human making the Decision explicitly before an agent records it;
- a human accepting an agent-proposed Decision during review;
- a pull-request merge where repository policy guarantees that semantic Decision changes receive human approval;
- another explicit workflow event that records human acceptance.

A Git commit, merge, branch location, agent-authored metadata or agent write access is not, by itself, proof of human acceptance.

Agents may continue to make ordinary local implementation decisions within delegated authority without separate human acceptance for each one.

Once a semantic Decision is accepted into the authoritative Decision set, its record is immutable and future authority changes are represented through superseding Decisions.

## Why

The earlier formulation conflated three different things:

- local implementation decisions made within delegated authority;
- semantic Decisions proposed by an agent;
- authoritative semantic Decisions accepted by humans.

Agents are capable of useful decision-making and may discover better semantic choices than the human initially considered. Preventing them from proposing those choices unnecessarily limits exploration.

The boundary that matters is not who first generated the idea or typed the Decision record. It is who has authority to make that semantic choice binding on the system.

Likewise, pull requests are a useful acceptance mechanism but are not part of the methodology's semantic definition. Model-led should work for direct-to-main workflows, external review systems and future collaboration platforms as long as human acceptance remains explicit.

## Consequences

- agents may originate proposed semantic Decisions;
- proposed Decisions do not become authoritative solely because an agent writes or commits them;
- humans own semantic Decision authority;
- explicit human instruction may constitute acceptance before the Decision record is written;
- PR merge is a common acceptance mechanism, not the universal definition of acceptance;
- repositories using merge as acceptance should enforce human review of Decision changes;
- direct-write workflows must preserve an equivalent human-acceptance boundary;
- ordinary local implementation decisions remain within delegated agent authority;
- accepted Decision records remain immutable and are changed only through supersession.
