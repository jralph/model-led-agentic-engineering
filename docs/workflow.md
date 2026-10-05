# The working loop

There is no requirement to follow these steps mechanically.

They describe the loop I tend to use when the work is substantial enough to justify it.

## 1. Frame the problem

Start with the outcome, not a technology.

Questions:

- What is actually wrong?
- Who experiences it?
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

## 4. Decide

Integrate useful findings into the model.

Explicitly reject alternatives where the reason will matter later.

This is the key human ownership point.

The decision can be as simple as:

> Keep the existing authoritative path. Add a speculative path in parallel, but only allow it to terminate when confidence is above the accepted boundary. Uncertain cases must fall back without delaying the existing path.

That is already enough to constrain a large amount of implementation.

## 5. Crystallise intent

For non-trivial work, turn the accepted model into an artefact another agent can execute.

Use the [intent brief](../templates/intent-brief.md) as a starting point.

A useful brief usually captures:

- outcome;
- current behaviour;
- desired behaviour;
- invariants;
- non-goals;
- allowed local discretion;
- acceptance criteria;
- verification expectations.

The goal is not prose quality. It is fidelity.

## 6. Delegate implementation

Give an implementation agent the agreed model plus enough repository context.

Allow it to make ordinary local implementation choices.

Require it to stop or surface uncertainty when satisfying the task would require changing a protected assumption.

For large changes, implement in bounded slices so incorrect assumptions are found before they spread.

## 7. Review adversarially

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

## 8. Qualify the claims

Choose evidence that matches the claim.

If the claim is "the parser handles these known cases", deterministic fixtures may be sufficient.

If the claim is "the deployed integration works with the real provider", fixtures are not sufficient.

Record failures and limitations.

Do not reinterpret the experiment after seeing the result.

## 9. Reconcile the model

Implementation and verification often reveal something new.

Update:

- the mental model;
- durable intent;
- relevant tests;
- agent guidance;
- architecture documentation.

Do not let the repository accumulate an old description of a system nobody believes.

## 10. Release and observe

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
