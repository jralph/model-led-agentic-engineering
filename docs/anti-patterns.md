# Anti-patterns

These are failure modes this methodology is intended to avoid.

## Prompt and pray

Give a vague goal to an agent, accept the first plausible implementation, and rely on runtime luck.

The problem is not short prompts. The problem is unowned intent.

## Black-box ownership

The code works, but the supposed owner cannot explain why.

If every non-trivial question about the system has to be answered by asking an agent to rediscover the implementation, the human does not own enough of the model.

## One omnipotent agent

One context researches, decides, implements, reviews and declares success.

This creates correlated blind spots and makes it easy for an early assumption to become an unquestioned requirement.

Mode separation does not always need separate models, but important work benefits from fresh challenge.

## Silent requirement invention

An agent fills gaps in a specification with plausible product or architecture decisions and nobody notices.

Implementation should surface semantically important ambiguity.

## Silent model drift

The implementation changes an invariant because doing so simplifies the code.

Tests pass because the tests were generated from the changed implementation rather than the original intent.

## Context dumping

Feed the agent the entire repository, every design document and a huge transcript "just in case".

More context can dilute the important constraints.

Retrieve and provide the context that matters to the current mode.

## Documentation theatre

Write enormous specifications because agentic work is supposed to be "spec driven".

If documenting the work takes as long as implementing it manually would have, the process has probably overcorrected.

Externalise high-value intent.

## AI reviewing AI without independence

Ask the same context "are you sure?" and treat "yes" as verification.

A useful review needs a different objective, fresh context, independent evidence, or some combination.

## Benchmark laundering

Use deterministic or synthetic evidence, then describe the result as though it proves live deployed behaviour.

Always state the evidence boundary.

## Moving the goalposts

Run a benchmark, dislike the result, then change thresholds or labels until it passes without an engineering reason.

Threshold changes can be legitimate. They should be explicit decisions.

## Optimising for generated volume

Celebrate thousands of lines written in minutes.

Volume is only useful when it represents coherent, maintainable, validated capability.

## Treating language as irrelevant

A semantic model can be language-independent.

An implementation cannot.

Memory models, type systems, runtime behaviour, concurrency primitives and ecosystem constraints can change the best concrete design.

## Human as rubber stamp

The human approves everything the agent proposes because reviewing is slower than generating.

This destroys the ownership model.

Agentic engineering only works if human attention is spent where judgement matters most.
