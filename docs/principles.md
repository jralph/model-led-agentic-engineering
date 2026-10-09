# Core principles

These are the current principles behind model-led agentic engineering.

They are intended as working rules, not slogans.

## 1. The human owns the coherent model

Agents can investigate, suggest, implement and challenge. The engineer remains responsible for the overall model of the system and for deciding which local contributions become part of it.

An agent can contribute local intelligence.

The human retains global intent.

## 2. Implementation can be delegated; accountability cannot

An engineer does not need to personally type every line to own an implementation.

They do need to understand what the implementation is meant to do, why it exists, how it fits into the wider system, and what evidence supports accepting it.

"I didn't write the code" is not the same as "I don't know the code".

## 3. Intent is direction, not authority

An Intent describes a human-owned outcome being pursued.

It can be refined, deferred or abandoned during exploration. It does not itself authorise new system semantics.

Implementation may proceed under existing accepted Decisions when they provide a sufficient basis. If a new semantic choice is required, an agent or human may propose it, but human acceptance is needed before that semantic choice becomes authoritative or releasable.

Important behaviours, algorithms, invariants and boundaries should still be understandable without relying on the syntax of a particular language.

Language constraints still matter. A Rust implementation may need a different shape from a Go implementation. The point is that the underlying behaviour and reasoning should not disappear when the language changes.

## 4. Govern above the implementation workflow

Model-led engineering does not prescribe one way to turn intent into software.

Spec-driven development, autonomous agents, lightweight briefs, conventional tickets and manual coding can all operate inside the same human-owned model.

The methodology governs authority, durable decisions, review and evidence rather than requiring a particular delivery sequence.

## 5. Give agents bounded authority

Different tasks need different freedom.

A researcher should be free to discover evidence, not silently choose product direction. An implementation agent should make ordinary local implementation decisions, not redefine a security boundary because it is convenient. A reviewer should challenge assumptions, not move the acceptance criteria.

Authority should be explicit enough that ambiguity causes escalation rather than silent redesign.

## 6. Semantic Decision authority is human

Agents can explore, challenge, reason about, propose, write and review semantic Decisions.

The distinction is authority: a semantic Decision becomes authoritative only through human acceptance.

That acceptance may happen before a Decision is recorded, during review, through team governance or through another explicit workflow event. Model-led does not prescribe the mechanism.

Agents may make ordinary local implementation decisions inside delegated authority without separate human approval for every choice.

When a semantic Decision materially constrains future engineering, preserve it in durable Decision history. A proposal may change before acceptance; once accepted, later authority changes should supersede rather than silently rewrite the historical Decision.

## 7. Preserve unresolved questions as Challenges

Not every problem should be forced immediately into a solution or Decision.

A Challenge records something about the current model, implementation, evidence or observed behaviour that may need attention. Humans and agents may both raise Challenges because doing so does not change the authoritative model.

Agents should raise a Challenge when they discover semantic ambiguity outside their delegated authority rather than silently making that choice binding on the system.

When a Challenge is resolved, implementation may be corrected under an existing Decision, evidence may be improved, or an agent/human may propose a new Decision that becomes authoritative only through human acceptance.

## 8. Review decisions before implementation detail

When agent-generated changes are large, human review should prioritise the decisions, semantic changes, trade-offs and accepted risk that shape the implementation.

Agents can perform exhaustive conformance review against the accepted Decision basis and separately evaluate candidate implementation against proposed Decisions, supported by qualification evidence. Human code inspection remains available wherever risk, novelty or direct judgement warrants it.

Changing a proposed decision during review should cause the implementation and evidence to be re-evaluated against that new intent.

## 9. Preserve invariants more strongly than implementation details

Implementation is expected to change.

Important invariants should survive refactors, model changes and agent changes.

Examples:

- a speculative fast path must never override an authoritative result outside its confidence boundary;
- untrusted extensions must not acquire unrestricted host access;
- private user content must not enter analytics;
- a failed operation must not be reported as successful.

If an invariant matters, encode it in more than somebody's memory.

## 10. Evidence beats confidence

Agent confidence is not evidence.

Compilation is not evidence of correct behaviour. Unit tests are not evidence of deployed behaviour. A synthetic benchmark is not evidence of production latency.

Match the evidence to the claim.

## 11. Separate exploration from commitment

Agents should be allowed to explore broadly without every suggestion becoming architecture.

A useful workflow has a deliberate decision boundary between:

- things considered;
- things accepted;
- things specified;
- things implemented.

This lets AI increase the breadth of investigation without allowing it to increase architectural randomness.

## 12. Optimise for semantic throughput, not code volume

Lines of code are a poor measure of this style of engineering.

The useful output is validated capability: correct behaviours, safe abstractions, resolved problems and durable decisions.

The aim is to increase the amount of engineering intent that can become working software per unit of human attention.

## 13. Keep the model reconstructable

A purely mental model works surprisingly well for one engineer, until it does not.

Externalise the parts another engineer or future agent would need to safely continue the work:

- invariants;
- non-obvious decisions;
- contracts;
- boundaries;
- acceptance criteria;
- evidence.

Do not attempt to document every thought.

## 14. The human should be able to explain the system

A useful ownership test is whether the engineer can explain the logic and behaviour of the system without hiding behind the generated source.

They may need to inspect syntax or library details. They should not need the agent to tell them what their own system is for.
