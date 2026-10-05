# Abstract examples

These examples are based on real patterns of work but deliberately remove product-specific context.

The point is to show how model-led agentic engineering differs from simply asking an agent to implement a feature.

## Example 1: speculative low-latency decision path

### Problem

An authoritative AI-backed decision path is accurate enough but too slow for an interactive action.

### Human model

The desired mechanism is:

- preserve the existing resolver as the authoritative path;
- run a cheaper/faster path speculatively in parallel;
- allow the speculative path to terminate only above a strict confidence boundary;
- uncertain results must fall back to the authoritative path;
- speculation must not add sequential latency;
- action execution takes priority over optional presentation work;
- future learning/cache promotion is a separate decision.

### Agent contribution

Explore mode can investigate candidate models and racing strategies.

Specify mode can turn the mechanism into an implementation brief.

Implement mode can build concurrency, cancellation, confidence handling and tests.

Review mode can look for cases where the speculative result accidentally becomes authoritative.

Qualify mode measures:

- wrong execution rate;
- safe refusal/fallback rate;
- time to action;
- p50/p95 latency;
- resource usage;
- cost.

The source code may be agent-generated. The algorithm and authority boundaries are human-owned.

---

## Example 2: synthetic cache warming

### Problem

A system benefits from semantic cache hits, but a new deployment has little observed traffic and therefore a cold cache.

### Human model

Generate synthetic user-like inputs for actions whose correct result is already known.

Important invariants:

- runs are finite, not autonomous background traffic;
- synthetic inputs go through the real resolution path;
- the expected action is known before execution;
- only matching results may be published;
- synthetic provenance must survive publication;
- failures must not contaminate normal cache state;
- synthetic usage must not be mistaken for real customer analytics;
- the feature is disabled by default.

### Agent contribution

Agents can propose corpus shapes, implement the scheduler and persistence, build tests and run qualification.

The key engineering work is the model: preventing a cache-warming optimisation from quietly becoming an oracle, an infinite workload or a source of untraceable synthetic data.

---

## Example 3: untrusted extension system

### Problem

Users need to extend a desktop application with custom actions, but arbitrary native code would destroy the application's trust boundary.

### Human model

Extensions are action executors, not unrestricted agents.

Design constraints:

- run extensions inside a sandboxed runtime;
- expose only explicit host capabilities;
- keep secrets outside shared profiles and agent prompts;
- no unrestricted filesystem, process or network access;
- inputs are declared and structured;
- recursion is impossible;
- background triggers cannot invoke extensions initially;
- extension output is terminal by default.

### Agent contribution

Research mode compares sandbox runtimes.

Explore mode considers API shapes.

Specify mode records the capability contract.

Implement mode builds the ABI and host functions.

Review mode tries to escape the sandbox or create privilege escalation.

Qualify mode proves specific capability boundaries.

Again, implementation syntax is downstream of the engineering model.

---

## Example 4: evidence-aware qualification

### Problem

An AI-integrated feature appears to perform well, but different tests are measuring different parts of the system.

### Human model

Evidence must be labelled by what it actually exercised.

Separate:

- fixtures;
- production functions with controlled dependencies;
- real external providers;
- deployed API paths;
- installed end-to-end client paths.

Also distinguish:

- wrong answer;
- safe refusal;
- timeout;
- infrastructure failure.

A faster wrong answer is not a performance improvement.

### Agent contribution

An agent can build a unified benchmark runner, reporting formats and test adapters.

The important engineering decision is what each result is allowed to prove.

That decision should exist before the benchmark produces a number.
