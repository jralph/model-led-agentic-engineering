# Authorship, ownership and understanding

AI makes several ideas that used to be bundled together separable.

Historically, the person who designed a system, wrote most of its code, reviewed it and maintained it was often the same person. That made "who wrote the code?" a reasonable shortcut for "who understands and owns this system?"

It is becoming a poor shortcut.

## Four different things

### Design authorship

Who formed the architecture, algorithms, behaviours, constraints and trade-offs?

### Artefact authorship

Who physically produced the source code, tests, prose or configuration?

With agents, this may be mostly or entirely machine-generated.

### Engineering ownership

Who can explain the system, reason about changes, recognise when an implementation violates the intended model, and decide what happens next?

### Accountability

Who accepts responsibility for the technical outcome?

These can now be different.

## Zero manually written lines can still represent real engineering

A useful extreme case is a system where the engineer personally types effectively none of the production source.

That does not automatically mean the system is a black box.

The engineer may still have specified:

- the architecture;
- the algorithms;
- the behaviour of each subsystem;
- calculations and ranking mechanics;
- state transitions;
- APIs and contracts;
- failure and retry behaviour;
- security boundaries;
- performance requirements;
- what must never happen.

An agent then translates that model into a language-specific implementation.

The engineer can still legitimately own the implementation if they understand what was built and can reason about why it behaves as it does.

## The language-switch test

Imagine the implementation were rewritten tomorrow in another language.

Would the engineer still understand:

- what each component is for;
- how information moves through the system;
- which algorithms are being performed;
- which invariants must remain true;
- where authority lives;
- how failures are meant to behave?

If yes, much of the engineering knowledge is above the syntax layer.

The engineer will still need time to learn the new language's constraints, runtime model and idioms. A language-independent semantic model does not make language-specific engineering irrelevant.

It simply means the system does not have to be rediscovered from scratch.

## The source-code test

Given an unfamiliar generated function in a system they own, the engineer should usually be able to:

1. explain what the function is supposed to achieve from the surrounding model;
2. inspect the implementation and map it back to that behaviour;
3. identify whether it violates an invariant or introduces an unexpected assumption;
4. know where to investigate if observed behaviour differs.

They do not need to have memorised every generated line.

## The dangerous version

This methodology is **not**:

> "The agent wrote it, therefore I own it."

Ownership requires understanding and judgement.

Warning signs include:

- the engineer cannot explain a subsystem without asking the agent;
- generated implementation decisions repeatedly surprise the supposed owner;
- nobody knows why a major algorithm or dependency was chosen;
- tests were generated from the implementation but no human can state the intended behaviour;
- the only durable description of the system is the code itself and the owner does not comfortably read it.

That is black-box delegation, not model-led engineering.

## A better question than "how much code did you write?"

Ask:

> "How much of the system can you explain, defend, change and verify without delegating the judgement back to the agent?"

That is much closer to the capability that matters.
