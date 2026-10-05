# Experiments

This directory is for testing the methodology rather than assuming it works because it feels productive.

The first goal is simple: collect enough structured evidence from real work to understand where model-led agentic engineering succeeds and where intent is lost.

## Initial experiment

For a sample of meaningful engineering tasks:

1. create a short measurement record before or immediately after starting;
2. record the modes used;
3. estimate human active time separately from unattended agent time;
4. record meaningful clarification loops;
5. classify corrections as semantic or implementation-level;
6. record the evidence used to accept the outcome;
7. revisit the task after a useful interval and note semantic rework.

Use [the session measurement template](../templates/session-measurement.md).

## Do not optimise the process around the metric yet

The first data is observational.

Do not deliberately make tasks smaller, avoid exploration, reduce agent calls or change review behaviour to make a number look better.

We are trying to discover useful measures, not hit targets.

## Suggested sample

Start with roughly 20 substantial tasks across different classes:

- new feature;
- architecture change;
- bug investigation;
- performance work;
- infrastructure;
- refactor;
- unfamiliar codebase;
- research-heavy decision.

That is enough to expose patterns without pretending it is statistically conclusive.

## Questions to answer

- Which tasks transfer cleanly from model to implementation?
- Where do semantic corrections cluster?
- Does a separate adversarial review mode find material issues?
- Does more explicit intent reduce correction loops?
- Which tasks need the most human attention?
- Does agent-generated implementation create delayed architectural rework?
- Which parts of the model repeatedly need to be re-explained?
- Are some modes better served by different models or harnesses?
- Does the approach remain effective as a codebase becomes older and more complex?

## Future experiments

Possible controlled comparisons:

- same task with and without an explicit intent brief;
- same task with implementation self-review versus fresh-context review;
- one large context versus targeted context;
- one general agent versus separated modes;
- different models in the same mode;
- another engineer using the same templates;
- model reconstruction from repository artefacts with the original design conversation hidden.

Any result should state its limits. Small synthetic experiments are useful evidence, not universal proof.
