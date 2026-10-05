# Intents

An **Intent** is a human-owned, mutable statement of an outcome being pursued.

It is pre-decisional.

Intent creates direction for exploration and research. It does not, by itself, create durable authority for semantic implementation.

> **Intent:** what outcome are we trying to achieve?  
> **Decision:** what have humans accepted as authoritative while achieving it?

## Intent should describe the outcome

Prefer describing the desired outcome before prescribing implementation where possible.

For example:

> Reduce user-visible command latency without reducing resolution correctness.

is a better Intent than:

> Add a cache before the resolver.

The second statement may eventually describe a valid implementation or Decision, but it narrows the solution space before the problem and existing Decision basis have been explored.

## Intent is human-owned

AI may help:

- clarify the Intent;
- challenge its framing;
- research feasibility;
- suggest alternatives;
- identify relevant existing Decisions;
- surface missing Decisions or new Challenges.

AI must not silently change the objective and then treat the changed objective as authoritative.

For example, an agent must not reinterpret:

> Reduce cost without reducing availability.

as:

> Reduce cost by accepting lower availability.

That changes the Intent and requires human authority.

## Intent is mutable

Unlike an accepted Decision, an Intent is expected to evolve during exploration.

For example:

> Support multiple cloud regions.

may become:

> Survive loss of a region without user-visible interruption.

The second statement expresses the actual outcome more directly and creates more implementation freedom.

Intent therefore does not need the immutable append-only semantics of `.decisions/`.

## Intent may end without a Decision

An Intent creates potential for work. It does not guarantee that work should proceed.

Exploration or research may show that the Intent is:

- already satisfied;
- not worth the trade-off;
- infeasible under current constraints;
- better deferred;
- unnecessary;
- addressable without software changes.

In those cases, the Intent may end without a new Decision or implementation.

## Intent does not always require a new Decision

Implementation requires a sufficient **Decision basis**, not necessarily a new Decision for every Intent.

Suppose the Intent is:

> Reduce infrastructure cost by 20%.

Existing Decisions already constrain:

- availability;
- correctness;
- latency;
- data residency.

If the Intent can be achieved within those constraints, existing Decisions may provide a sufficient basis and implementation can proceed without a new Decision.

If achieving the Intent requires a new semantic trade-off, such as deliberately reducing redundancy, an agent or human may propose the Decision, but human acceptance is required before that semantic choice becomes authoritative or releasable.

The governing rule is:

> **No meaningful semantic implementation may outrun its Decision basis.**

## Intent and Challenge

Intent and Challenge are peer concepts.

An Intent expresses a desired outcome.

A Challenge questions the current model, Decision basis, implementation or evidence.

They can interact without forming a mandatory sequence.

An Intent may expose a Challenge:

> Intent: move away from the current cloud provider.  
> Challenge: current delivery semantics depend on a provider-specific guarantee.

A Challenge may create an Intent:

> Challenge: failover currently takes six minutes.  
> Intent: survive regional failure without meaningful user interruption.

Either may also end after exploration or research without creating the other.

## Intent enters the Model-led loop

An Intent can begin the normal Model-led workflow:

1. frame the desired outcome;
2. reconstruct enough of the relevant semantic model;
3. explore and research;
4. determine whether change is actually required;
5. identify the existing Decision basis;
6. propose and obtain human acceptance for new Decisions where additional semantic authority is necessary;
7. implement if work remains, using the existing accepted Decision basis or the newly accepted Decision;
8. review and qualify;
9. reconcile what was learnt back into the model.

The loop may stop at any appropriate point.

## Sharing Intent

Intent needs to be available to the humans and agents working on the relevant piece of work.

Model-led does not prescribe how it is stored.

It may live in:

- a ticket;
- an engineering brief;
- a design conversation;
- a planning system;
- a review object;
- a platform-native work item.

When implementation is delegated, the active Intent should travel with the relevant Decision basis and context so the agent understands both:

- the outcome being pursued;
- the authority boundaries within which it may pursue it.

Intent can remain useful provenance after work finishes, but it is not durable authority in the same sense as an accepted Decision.

## No `.intents/` requirement

Intent is a first-class Model-led concept, not a required repository artefact.

Model-led deliberately does not define a canonical `.intents/` directory.

The methodology prescribes `.decisions/` because accepted Decisions need an immutable, portable representation of semantic authority.

Intent does not need those same persistence semantics.
