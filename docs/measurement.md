# Measuring effectiveness

The long-term aim is to quantify whether model-led agentic engineering actually improves engineering throughput without hiding quality loss.

The methodology does **not** currently define one composite productivity score.

That would be premature.

Instead, measure several dimensions independently.

## What not to optimise

Avoid treating these as primary success metrics:

- lines of generated code;
- token volume;
- number of agent calls;
- percentage of code written by AI;
- number of parallel agents;
- raw wall-clock speed without outcome quality.

They can be useful diagnostics, but none means the engineering was good.

## Per-task record

For representative tasks, capture:

### Outcome

- Did the accepted behaviour ship?
- Did qualification pass?
- What residual risk remained?
- Was the task later reverted or substantially redesigned?

### Human active time (HAT)

Approximate time the engineer actively spent:

- thinking;
- explaining;
- deciding;
- reviewing;
- interpreting evidence.

Do not include unattended agent execution.

### Agent wall time (AWT)

Total elapsed agent execution time.

Keep this separate from human active time because ten minutes of unattended work is not equivalent to ten minutes of human attention.

### Mode usage

Which modes were used?

- Explore
- Research
- Specify
- Implement
- Review
- Qualify

Record whether modes used separate contexts/models where relevant.

### Clarification loops

How many times did implementation have to stop because intent was genuinely ambiguous?

This can reveal missing model transfer.

### Semantic corrections

Count corrections where the implementation misunderstood behaviour, architecture, a boundary or an invariant.

Examples:

- wrong ownership of state;
- incorrect retry semantics;
- broadened security authority;
- wrong algorithm;
- product behaviour changed.

These are more important than ordinary coding fixes.

### Implementation corrections

Count local defects that do not change the model:

- syntax;
- incorrect library usage;
- small edge-case bug;
- failing type;
- formatting.

Separating these from semantic corrections matters.

### First-pass semantic acceptance

Did the first substantial implementation preserve the intended model?

Record:

- yes;
- mostly, with bounded corrections;
- no, required redesign.

Avoid fake precision until enough data exists.

### Review discovery

Which issues were found by:

- implementation self-check;
- adversarial review;
- deterministic test;
- integration test;
- human inspection;
- production observation?

This helps determine whether mode separation is providing value.

### Rework horizon

Check the change after a useful interval, for example 7 and 30 days:

- no semantic rework;
- local maintenance only;
- significant redesign;
- reverted.

Fast initial output with large delayed rework is not high throughput.

## Candidate derived metrics

These are hypotheses to test, not standards.

### Semantic correction rate

```text
semantic corrections / substantial implementation tasks
```

Useful for tracking how often intent transfer fails.

### First-pass semantic acceptance rate

```text
tasks accepted semantically on first substantial implementation / tasks measured
```

This may become a useful measure of human-to-agent model transfer.

### Validated throughput per human active hour

```text
accepted, qualified task outcomes / human active hours
```

Only compare similar classes of work. Do not use this as a universal engineer ranking.

### Delayed semantic rework rate

```text
tasks requiring semantic redesign within N days / tasks shipped
```

Useful for detecting apparent speed purchased with architectural debt.

### Independent defect yield

```text
material issues found outside the implementation context / tasks reviewed
```

Can help determine whether separate review/qualification modes are worthwhile.

## Measuring model transfer directly

A more interesting future experiment is to test whether another capable engineer or agent can reconstruct the intended system from durable artefacts.

Possible test:

1. hide the original design conversation;
2. provide the repository and externalised intent;
3. ask the reviewer to explain the component behaviour, invariants and trade-offs;
4. compare that explanation with the model owner's expected model.

This could provide a more direct measure of how much critical intent remains trapped in one person's head.

## Session instrumentation

Full transcripts are not necessarily required.

Useful metadata may include:

- task identifier;
- model/harness;
- mode;
- start/end;
- token/cost metadata;
- tool usage;
- explicit hand-off artefacts;
- human corrections;
- final qualification result.

Privacy matters. A methodology should not require organisations to centrally record developers' private reasoning conversations.

## The measurement goal

The question is not:

> How much code did AI produce?

It is:

> How efficiently did a correct human-owned model become a validated software outcome, and did that outcome remain coherent over time?
