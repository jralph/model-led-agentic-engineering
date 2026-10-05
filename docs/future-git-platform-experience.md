# Potential Git platform: human experience

> **Status:** exploratory implementation concept.  
> This is a possible user experience for a platform that implements model-led agentic engineering.

The biggest UI change is not adding an AI panel.

It is changing the top-level object from **Repository** to **Project**.

A Project is the human-facing system/product model. It may be backed by one Model Repository and several independent Implementation Repositories.

Traditional Git hosts make the file tree, commits, branches, issues and pull requests central because those were the objects humans directly manipulated.

A decision-native platform assumes agents will manipulate much more of the implementation.

The human-facing product therefore centres on:

- intent;
- Decisions;
- Challenges;
- Decision Reviews;
- evidence;
- semantic Areas;
- places where human judgement is required.

Files and branches remain available as implementation drill-downs.

## Project navigation

A possible top-level navigation:

```text
Overview
Model
  Decisions
  Areas
  History
Tasks
  Intents
  Challenges
Decision Reviews
Evidence
Agents
Implementation
  Repositories
  Code
  Commits
  Branches
  Releases
```

This hierarchy is deliberate.

A Project opens on **what the system believes and what needs human attention**, not on a repository list or directory listing.

## Overview

The home view should answer human questions first.

### What needs a human?

- proposed Decisions awaiting review;
- semantic conflicts;
- residual risk requiring acceptance;
- agent workspaces blocked on ambiguity;
- Challenges with strong evidence against an active invariant.

### What is changing?

- open Decision Reviews;
- Tasks under exploration/research;
- active agent workspaces;
- candidate implementations being compared.

### Is the model healthy?

Possible signals:

- recently superseded Decisions;
- active invariants with weak/stale evidence;
- repeated Challenges against the same area;
- implementation changes with no known Decision basis;
- unresolved conformance findings.

### What happened recently?

A semantic activity timeline might show:

> DEC-142 accepted  
> Challenge C-88 raised against DEC-91  
> DR-42 intent changed after review  
> qualification for DEC-142 reached E5  
> candidate B abandoned after conformance failure

Code is reachable from each event, but is not the only history that matters.

## Model

The Model view is the semantic equivalent of the repository browser.

### Decisions

Default views:

- active;
- proposed;
- superseded;
- invariants;
- architecture;
- security;
- product;
- process.

Each Decision can show:

- title;
- type;
- Area;
- accepted date;
- human owner;
- Challenges;
- Decision Reviews;
- evidence;
- supersession chain.

### Areas

Areas are human concepts, not directories.

Example:

```text
Authentication

12 active Decisions
2 invariants
1 open Challenge
1 Decision Review
Evidence: current through main@abc123
Owners: Platform / Identity

Implementation
  3 services
  2 packages
  1 database schema
```

The implementation section reveals concrete repositories, files and services when needed.

This creates a **semantic monorepo** experience even when Authentication is physically implemented across API, web, identity and infrastructure repositories.

### History

Decision history should be more prominent than commit history for humans trying to understand why a system changed.

Example:

> 4 Jan — single-region storage accepted  
> 19 Mar — Challenge: availability requirement changed  
> 2 Apr — multi-region storage supersedes DEC-17  
> 7 Apr — deployed evidence accepted

Git history remains available under Implementation.

## Tasks instead of Issues

The platform uses **Task** as the human-facing work item that replaces much of the traditional Issue/ticket model.

A Task is primarily driven by either:

- **Intent** — a human-owned outcome being pursued;
- **Challenge** — something that deserves investigation.

This is a platform convention, not a new Model-led primitive.

An Intent Task creation flow can ask:

- What outcome are you trying to achieve?
- Why does it matter?
- Which Decisions or Areas may constrain it?
- What would make the work not worth pursuing?

A Challenge Task creation flow can ask:

### What are you challenging?

- Decision
- Implementation
- Evidence
- Observed behaviour
- Opportunity
- Unknown / needs investigation

### What did you observe?

Free-form human or agent evidence.

### Why might the current model be wrong or incomplete?

Uncertainty is allowed.

### Which Decisions or Areas may be affected?

Suggested automatically, editable by humans.

### What evidence is attached?

Logs, benchmark output, user reports, traces, source references.

A Challenge Task does not need a solution.

Either Task kind may close after exploration or research without creating a Decision or implementation.

See [Task model](future-git-platform-tasks.md).

## Agent-created Challenge Tasks

Agent findings should become Challenge Tasks rather than quietly turning into implementation or new Decisions.

Example:

> **C-114: Retry path appears inconsistent with DEC-76 idempotency invariant**  
> Raised by: adversarial-review agent  
> Evidence: attached trace + reproduction  
> Decision affected: DEC-76  
> Area: payment/retry

The human can:

- dismiss;
- ask another agent to investigate;
- classify it as implementation drift under an existing Decision;
- request stronger evidence;
- define an Intent if a desired outcome now exists;
- open a Decision Review when there is something to accept;
- accept risk.

This gives agents a safe way to say:

> **I think something is wrong.**

without granting:

> **I have decided how it should change.**

## Decision Review

The default Decision Review should not open on Files Changed, and it should not be scoped to one repository.

A Decision Review belongs to the Project and can carry one implementation candidate spanning several repositories.

A possible header:

```text
DR-42
Reduce cold-start latency without increasing incorrect execution

Decision state
  2 proposed Decisions
  12 applicable active Decisions
  0 semantic conflicts

Challenges
  resolves C-81, C-83

Implementation candidates
  A — conforms 14/14 — E4
  B — conforms 13/14 — E4
  C — conforms 14/14 — E2

Human attention
  DEC-P142 requires approval
  candidate A increases cost by 8%
  E6 evidence not supplied
```

Possible tabs:

```text
Intent
Decisions
Challenges
Candidates
Conformance
Evidence
Code
Activity
```

The Code tab exists, but it is not the front page.

## Changing a proposed Decision

Proposed Decisions remain mutable while review is open.

The UI could show:

> **Performance boundary**  
> Current proposal: p95 < 500 ms  
> Reviewer suggestion: p95 < 750 ms while preserving strict correctness

After the human accepts the edit:

```text
Decision changed.

Affected candidates: A, B, C
Affected evidence: latency qualification
Affected active Decisions: none

Re-evaluate?
[Run all] [Choose agents]
```

The platform then:

1. invalidates conformance/evidence that depended on the old proposal;
2. resumes or creates implementation workspaces;
3. changes code where necessary;
4. reruns conformance;
5. reruns qualification;
6. returns the updated result to human review.

The human changes **intent**, not individual source lines.

## Candidate implementations

When implementation is cheap, the first working approach does not always need to win.

For high-value changes, several agents could produce candidate implementations.

Humans may compare:

| Candidate | Conformance | Evidence | Performance | Cost | Findings |
| --- | --- | --- | --- | --- | --- |
| A | Pass | E4 | best | medium | 0 |
| B | 1 violation | E4 | good | lowest | 1 |
| C | Pass | E2 | good | highest | 0 |

The human can ask:

> Why is C more expensive?

or:

> Reconcile A's latency with B's lower cost.

The work becomes closer to design evaluation than line-by-line implementation supervision.

## Implementation repositories

Implementation repositories remain ordinary Git repositories.

They are visible when a human wants low-level control, local work, debugging or implementation inspection, but they are not the primary Project navigation model.

A Decision Review can show an implementation candidate as a set of exact repository revisions rather than several unrelated pull requests.

External agents and harnesses should be able to pick up a Decision Review locally, work across the required repositories, and attach their candidate revisions back to the Project.

See [Project and repository model](future-git-platform-project-repositories.md).

## Code view

Code remains fully available.

Implementation can retain familiar tools:

- tree;
- file view;
- blame;
- diffs;
- commits;
- branches;
- language-aware navigation.

But it gains semantic overlays.

### Decision context

For a file/function/component:

- applicable active Decisions;
- proposed Decisions touching it;
- open Challenges;
- evidence;
- last Decision Review.

### Why view

A human can ask:

> Why does this retry happen here?

The platform should answer using:

1. accepted Decisions;
2. current architecture/context;
3. implementation;
4. evidence;

rather than inferring rationale solely from source code.

### Drift view

Highlight areas where:

- no Decision basis is known;
- implementation changed since evidence was gathered;
- Decision path scope no longer maps cleanly after refactoring;
- review found likely model drift.

## Folders and file types

Folder structures remain useful implementation structures.

They should stop being the primary human navigation model.

A human usually cares more that:

> this change alters authentication authority

than:

> six TypeScript files and two Go files changed.

Languages and frameworks still matter where they create real constraints.

When a language choice is semantically important, preserve the reason as a Decision.

Otherwise agents can optimise implementation structure while humans navigate the model through Areas, Decisions and Challenges.

This does not mean encouraging chaotic repositories. Agent tooling still benefits from coherent source organisation.

It simply stops forcing humans to use implementation layout as their primary mental model.

## Branches and commits

Branches become low-level implementation workspaces rather than the primary human coordination object.

One Agent Workspace may contain branches, forks or worktrees in several repositories while appearing to the human as one candidate implementation.

A human may see:

> Candidate A  
> baseline main@abc123  
> 18 implementation checkpoints  
> conformance clean

instead of:

> feat/cold-resolve-v3-agent-a

The branch still exists underneath for Git interoperability.

Commits remain useful for:

- checkpoints;
- bisect;
- provenance;
- rollback;
- local workflows.

The Decision Review becomes the primary semantic historical event.

## Notifications

Agent-heavy development can create enormous event volume.

Humans should be notified primarily about **judgement-required events**:

- proposed Decision awaits review;
- strong Challenge against active invariant;
- semantic conflict between concurrent work;
- agent blocked because the model is ambiguous;
- insufficient qualification for requested acceptance;
- residual risk requires human acceptance.

Agent progress and implementation noise can remain machine activity unless explicitly followed.

## Search

Search should understand semantic objects.

Examples:

> Why is this API read-only?

> Which active Decisions govern customer deletion?

> What would be affected if DEC-142 changed?

> Which Challenges currently question authentication?

> Show implementation changed since evidence for this invariant was collected.

> Which Decisions have no current strong evidence?

> Why was the previous queue approach rejected?

These queries can use structured relationships rather than relying only on semantic search over code.

## Planning

Traditional boards organise Issues into implementation work.

A decision-native board could organise:

- Intent Tasks awaiting exploration;
- Challenge Tasks awaiting investigation;
- Tasks needing a human Decision;
- Tasks ready for implementation under an existing Decision basis;
- Decision Reviews implementing;
- reviews qualifying;
- residual risk awaiting acceptance.

The work queue becomes closer to:

> **outcomes, questions and decisions the organisation needs to resolve**

than:

> tickets developers need to code.

Agents derive low-level execution steps underneath these Tasks rather than flooding the human planning surface with machine subtasks.

## Releases

A release can point to one immutable Project State and therefore snapshot:

- accepted Decision graph;
- Model Repository revision;
- exact revisions for every Implementation Repository;
- applicable qualification evidence;
- known open Challenges;
- explicitly accepted residual risk.

That lets someone answer:

> What did we believe, what did we ship, and what had we actually demonstrated at this point?

## Compatibility mode

Adoption should be gradual.

An ordinary Git repository could be imported and initially behave normally:

- source tree remains;
- existing Issues and Pull Requests remain visible;
- `.decisions/` is detected if present;
- new work can opt into Decision Reviews;
- Issues can be linked or converted to Challenges;
- existing CI can become Evidence inputs.

The platform should prove that the semantic model is useful before asking teams to reorganise everything around it.

## Product principle

If implemented, the platform should optimise for:

> **Show humans the minimum information needed to make good engineering decisions, while giving agents enough structured context and evidence to execute those decisions safely.**

That is a different optimisation target from maximising how much repository state is visible on one screen.
