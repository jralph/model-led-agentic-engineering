# The working loop

There is no requirement to follow these steps mechanically.

They describe the loop I tend to use when the work is substantial enough to justify it.

## 1. Frame the Intent or Challenge

Work commonly begins from either:

- an **Intent** — a human-owned outcome being pursued;
- a **Challenge** — something about the current model, Decision basis, implementation or evidence that deserves investigation.

Start with the outcome or question, not a technology.

Questions:

- What are we trying to achieve or understand?
- Who experiences the problem or benefit?
- What would a good outcome look like?
- What constraints already exist?
- Which parts are facts and which are assumptions?

At this point I often already have a candidate solution in mind. I still want the problem stated independently so the solution can be challenged.

## 2. Build the semantic model

Think through the mechanism before implementation details:

- responsibilities;
- flows;
- state;
- algorithms;
- failure modes;
- trust boundaries;
- performance-sensitive paths;
- important invariants.

This may happen mostly mentally.

For complicated work I explain the model conversationally to an AI. The act of explaining it is useful because gaps become visible.

## 3. Explore and research

Use AI to increase breadth and depth.

Ask it to:

- challenge the design;
- find counter-examples;
- inspect the current implementation;
- research unfamiliar constraints;
- compare plausible alternatives;
- calculate or benchmark where intuition is not enough.

AI may introduce ideas here.

Nothing becomes architecture merely because it was suggested.

## 4. Decide whether anything should change

Exploration and research do not imply implementation.

An Intent may be abandoned, deferred, already satisfied or judged not worth the trade-off.

A Challenge may be disproved, resolved by existing Decisions, or turn out to be an evidence problem rather than a model problem.

If no change is required, the work can end here.

If something remains unresolved but the correct change is not yet known, preserve it as a Challenge.

Not every investigation is ready to become a Decision.

When something appears wrong, incomplete or uncertain but the correct change is not yet known, record a **Challenge** rather than forcing a solution.

A Challenge can be raised by a human or agent and may target an existing Decision, implementation that may not conform, weak or stale evidence, unexplained observed behaviour, an opportunity worth investigating, or a genuine unknown.

See [Challenges](challenges.md).

## 5. Establish the Decision basis

Identify the accepted Decisions that already govern the work.

If they are sufficient, no new Decision is required.

If the work requires a semantic choice that is not already authorised, an agent or human may propose a Decision. Human acceptance is required before that semantic choice becomes authoritative or releasable behaviour. Candidate implementation may be explored against the proposal before acceptance.

Integrate useful findings into the model.

Explicitly reject alternatives where the reason will matter later.

This is the key human ownership point.

The decision can be as simple as:

> Keep the existing authoritative path. Add a speculative path in parallel, but only allow it to terminate when confidence is above the accepted boundary. Uncertain cases must fall back without delaying the existing path.

That is already enough to constrain a large amount of implementation.

## 6. Record durable decisions

Not every choice needs a permanent record.

When forgetting a decision would make future engineers or agents likely to weaken a boundary, repeat a rejected design, change important behaviour or misunderstand an accepted trade-off, add a record to the project's `.decisions/` library.

An agent may originate or draft the proposed Decision record. The semantic Decision becomes authoritative only through human acceptance.

Keep proposed Decisions with the implementation/review context where practical. They may be refined before acceptance. A pull-request merge can represent human acceptance when the repository workflow guarantees that relationship, but Model-led does not require Git or pull requests.

Once accepted into the authoritative Decision set, the Decision record becomes immutable.

See [Decision library](decision-library.md).

## 7. Crystallise implementation context

For non-trivial work, turn enough of the active Intent or Challenge, accepted Decision basis, proposed Decisions under evaluation and relevant model context into an artefact another agent can execute.

This does not require a particular specification workflow. A full spec-driven process may be appropriate for some work; a short intent brief may be enough for other work.

Use the [intent brief](../templates/intent-brief.md) as one lightweight starting point.

A useful brief usually captures:

- active Intent and/or Challenge;
- accepted Decision basis;
- proposed Decisions under evaluation;
- current behaviour;
- desired behaviour;
- invariants;
- non-goals;
- allowed local discretion;
- acceptance criteria;
- verification expectations.

The goal is not prose quality. It is fidelity.

## 8. Delegate implementation

Give an implementation agent the agreed model plus enough repository context.

Allow it to make ordinary local implementation choices.

Require it to stop or surface uncertainty when satisfying the task would require changing a protected assumption.

For large changes, implement in bounded slices so incorrect assumptions are found before they spread.

## 9. Review adversarially

Do not ask only:

> Does this look good?

Ask:

- Where does this violate the stated intent?
- What behaviour was inferred rather than specified?
- What unsafe states are now possible?
- Which claims are not actually proven?
- What changed outside the intended scope?
- What would make this fail under concurrency, retries or stale state?

A separate review context is useful because it is less invested in defending the implementation.

For projects using a decision library, review should also load the relevant active and proposed decisions and check the implementation against them. Human review should prioritise whether the decisions and trade-offs themselves are acceptable; agent review can take primary responsibility for exhaustive conformance checking.

See [Decision-first review](decision-review.md).

## 10. Qualify the claims

Choose evidence that matches the claim.

If the claim is "the parser handles these known cases", deterministic fixtures may be sufficient.

If the claim is "the deployed integration works with the real provider", fixtures are not sufficient.

Record failures and limitations.

Do not reinterpret the experiment after seeing the result.

## 11. Reconcile the model

Implementation and verification often reveal something new.

Update:

- the mental model;
- durable intent;
- relevant tests;
- agent guidance;
- architecture documentation.

Do not let the repository accumulate an old description of a system nobody believes.

## 12. Release and observe

Production is another source of evidence.

Watch for:

- behaviour that contradicts the model;
- repeated user corrections;
- unexpected costs;
- performance tails;
- operational complexity;
- places where future agents repeatedly misunderstand the same thing.

Feed those observations into the next loop.

## The loop can be fast

For a small change this process may take minutes.

The methodology should reduce implementation friction, not replace it with process friction.

The amount of explicit modelling should scale with the cost of being misunderstood.
