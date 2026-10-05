# Decision-first review

Agent-generated implementation changes the economics of review.

Producing and mechanically inspecting code can be delegated increasingly well. Human judgement remains scarce.

Model-led agentic engineering therefore treats the pull request as more than a code diff.

A substantial pull request can contain:

- **decisions** — what humans are proposing the system should believe or preserve;
- **implementation** — how those decisions are expressed;
- **evidence** — what has been demonstrated about the result.

![Decision-first pull request](../assets/diagrams/decision-pr-contract.svg)

## Human review priority

Human reviewers should spend their highest-value attention on:

### The decision

- Is this the right problem to solve?
- Is the chosen trade-off acceptable?
- Is the invariant actually desirable?
- Is the abstraction boundary right?
- Are we creating a precedent we want other work to follow?

### The semantic model

- Does this fit the rest of the system?
- Does it conflict with another accepted decision?
- Are responsibilities and ownership in the right place?
- What new states or failure modes become possible?

### Accepted risk

- Is the evidence strong enough for the change being made?
- Which gaps remain?
- Are those gaps acceptable now?
- What would require revisiting the decision?

The human is not prohibited from reviewing code. Code inspection remains appropriate anywhere direct judgement is valuable.

## Agent review priority

Agents are well suited to exhaustive conformance work:

- compare the implementation with proposed decisions;
- load relevant active decisions from `.decisions/`;
- identify violations or ambiguity;
- inspect changed paths for bugs and edge cases;
- assess tests against stated behaviours;
- check for unintended scope expansion;
- verify repository conventions;
- challenge security and failure handling;
- report claims that are stronger than the evidence.

A reviewer should not silently change the implementation to make its own preferred decision true.

If code cannot conform without changing the semantic model, that is a human decision point.

## A possible PR review surface

A tool could eventually present a change approximately like this:

```text
Decisions proposed
  DEC-104  Speculative execution requires accepted confidence
  DEC-105  Authoritative resolution remains the fallback
  DEC-106  Presentation work cannot delay action execution

Relevant active decisions
  11 loaded for changed areas
  0 supersession conflicts

Implementation conformance
  10 verified
  1 material review finding
  0 unresolved invariant violations

Qualification
  E1 deterministic behaviour        pass
  E3 production-seam behaviour      pass
  E4 live dependency                pass
  E6 installed end-to-end path      not supplied

Human review
  [ ] accept proposed decisions
  [ ] accept trade-offs
  [ ] accept residual evidence gap
```

This is not a required format. It illustrates where review attention can move.

## Merge means acceptance

For a project using the decision library, merging a pull request containing a new decision record means the repository accepts that decision.

After merge:

- the decision becomes immutable;
- implementation is expected to conform to it;
- future agents can retrieve it as authoritative context;
- changing it requires another human-authored decision.

A project should therefore make changes to `.decisions/**` conspicuous in review.

Recommended team controls include:

- CODEOWNERS for `.decisions/**`;
- required human approval;
- prevention of bot-only approval for decision changes;
- append-only validation.

The exact repository controls vary by platform.

## Human code review remains risk-based

"AI reviews code, humans review decisions" is a useful direction, but too absolute as a rule.

Direct human code inspection remains valuable for areas such as:

- novel concurrency;
- cryptography;
- security boundaries;
- irreversible data migrations;
- performance-critical algorithms;
- unfamiliar runtime behaviour;
- weak qualification evidence;
- anything where the reviewer wants direct confidence.

The shift is one of **review priority**, not a ban on human code review.

## Why this matters

A pull request containing thousands of agent-generated lines may represent only a few meaningful engineering decisions.

Reviewing those decisions carefully, then using agents and evidence to check the implementation against them, can make human review both more scalable and more relevant.

The question changes from:

> Did the agent write every line correctly?

towards:

> Are these the right decisions, and do the implementation and evidence faithfully realise them?
