# Repository guidance for agents

This repository contains two related but distinct things:

1. the **Model-led methodology**: semantic reasoning, authority, review and Evidence;
2. the **reference framework**: one concrete repository-based implementation of that methodology.

Do not allow framework mechanics to leak back into methodology claims.

## Core contract

> **Model-led defines what engineering knowledge and authority need to exist. It does not prescribe how tools should execute against them.**
>
> **Humans own intent, judgement and decision authority.**  
> **Agents explore, research, propose, implement, challenge and verify.**  
> **Semantic implementation must not outrun its Decision basis.**  
> **Evidence determines what can actually be claimed.**

## Methodology invariants

Preserve these ideas unless the owner explicitly changes them:

1. The human engineer owns the coherent semantic Model, technical direction and accountability.
2. Agents may contribute research, ideas, local reasoning, implementation and critique.
3. Implementation may be delegated without delegating understanding.
4. Agent work should happen in explicit modes with bounded authority where useful.
5. Claims about correctness, safety, performance or productivity require appropriate Evidence.
6. Source code is one representation of engineering intent, not the only measure of engineering authorship.
7. Language/framework constraints still matter. "Language-independent Model" does not make implementation details irrelevant.
8. Intent is human-owned, mutable and pre-decisional.
9. Challenges are unresolved questions and may be raised by humans or agents without changing authority.
10. Agents may originate proposed semantic Decisions. Human acceptance is what makes a semantic Decision authoritative.
11. The accepted Decision basis, not Intent or Challenge alone, governs meaningful semantic implementation.
12. Existing accepted Decisions may be sufficient for work. Work does not require a new Decision merely because work occurred.
13. A new Decision is needed only when existing semantic authority is insufficient.
14. Once accepted, a Decision constrains later work and may be described as a rule to follow. **Rule is not a separate methodology primitive.**
15. Accepted Decision history must remain reconstructable; changed authority is represented through later Decisions rather than silent rewriting.
16. Decision-first review prioritises semantic Decisions, trade-offs and accepted risk while agents can perform exhaustive implementation-conformance review.
17. Model-led governs above implementation workflow and storage choices.
18. The methodology does **not** prescribe `.decisions/`, `.rulesets/`, YAML, Git, pull requests, `AGENTS.md`, Task objects or another repository convention.
19. The methodology is currently a personal working method, not a validated standard.

See [docs/methodology.md](docs/methodology.md) and [docs/decisions.md](docs/decisions.md).

## Reference framework invariants

This repository also maintains the bundled reference framework.

These are framework rules, not methodology requirements:

1. Project Decision records use the `.decisions/` repository convention.
2. Accepted Decision records in this repository are append-only. Never edit, rename or delete one; supersede changed authority with a new Decision.
3. Decision front matter follows the framework schema. Provenance fields such as `author`, `accepted_by` and timestamps are optional and do not prove authority.
4. The framework may use Git/review history as provenance and enforcement, but Git state is not semantic authority by itself.
5. Framework templates are conveniences, not new Model-led primitives.
6. A framework **Ruleset** is a versioned/distributable grouping of ordinary accepted Decision records.
7. There is no separate Rule record type, Rule schema or Rule semantic lifecycle. A Rule is simply an accepted Decision being reused as a constraint.
8. Ruleset revisions may be materialised under the optional `.rulesets/` convention.
9. Materialised Ruleset revisions are self-contained snapshots. Never use symlinks, floating refs or mutable remote content as live authority.
10. Ruleset updates are additive: add a new revision, retain historical revisions, and change Project authority through ordinary Decisions.
11. Another Model-led implementation may replace every framework mechanic above.

See [docs/framework.md](docs/framework.md), [docs/decision-library.md](docs/decision-library.md) and [docs/rulesets.md](docs/rulesets.md).

## Writing rules

- Use British English.
- Prefer plain engineering language over AI-industry marketing language.
- Do not describe the approach as "10x", "revolutionary", "the future of software engineering", or similar.
- Do not imply that humans no longer need to understand their systems.
- Do not imply that an agent can verify its own work merely by saying it reviewed it.
- Do not turn every concept into a framework, acronym or score.
- Distinguish methodology, reference-framework convention, exploratory platform design and observed evidence.
- Keep the handbook readable before making it academically complete.

## Evidence rules

When documenting measurements:

- record what was actually measured;
- preserve failed and inconclusive results;
- state the evidence boundary;
- do not promote fixture Evidence into live-system Evidence;
- do not treat a finite zero-failure sample as proof of universal correctness;
- do not collapse several metrics into a composite productivity score without empirical justification.

## Maintaining methodology documents

Methodology documents should explain concepts and reasoning without requiring framework mechanics.

Avoid methodology claims such as:

- "Decisions live in `.decisions/`";
- "Rulesets are a Model-led primitive";
- "human acceptance happens through pull-request merge";
- "Intent belongs in a particular file";
- "a Project must use YAML".

It is fine to mention the bundled reference framework as an example, provided the implementation boundary is explicit.

## Maintaining framework documents

Framework documents may prescribe concrete conventions such as:

- `.decisions/`;
- schema/front matter;
- repository bootstrap;
- `AGENTS.md`;
- `.rulesets/`;
- Git-oriented validation.

Make clear that these are replaceable implementation choices.

## Bootstrapping the reference framework into another repository

If a user points an agent at this repository and asks to **set up Model-led**, treat that as a request to install the bundled reference framework unless they specify another implementation.

Read and use:

- `docs/framework.md`;
- `docs/adoption.md`;
- `docs/decision-library.md`;
- `templates/model-led-agent-guidance.md`;
- `templates/decisions-readme.md`;
- `.decisions/schema.yaml`.

Then:

1. **Inspect the target repository first.** Read existing root/subtree agent instructions, documentation and structure.
2. **Preserve existing guidance.** Merge reusable framework guidance into existing `AGENTS.md`; do not replace repository-specific build, test, language, security, architecture or release instructions.
3. **Create the framework Decision library** only if needed:
   - `.decisions/README.md` from `templates/decisions-readme.md`;
   - `.decisions/schema.yaml` from the current schema.
4. **Do not invent storage for methodology concepts.** Do not create `.intents/`, `.challenges/`, `.model/` or a generic Task system merely because those concepts exist.
5. **Do not infer historical Decisions from code.** Existing implementation may reveal behaviour or missing authority, but it is not proof of accepted Decisions.
6. **Do not create a ceremonial framework-adoption Decision by default.** Record one only if the human actually wants the governance/storage transition preserved as a semantic Decision.
7. **New Projects may start with an empty Decision library.** Add Decisions when real semantic choices arise.
8. **Validate conservatively.** Report ambiguity or incompatibility rather than overwriting it.

### Ruleset bootstrap

If the user asks to materialise/adopt a Ruleset:

1. read `docs/rulesets.md`;
2. resolve an exact upstream Ruleset revision/version/digest;
3. copy the complete bundle of ordinary Decision records into a new local framework snapshot;
4. preserve older snapshots;
5. use an ordinary Project Decision to adopt/update that snapshot when it should constrain the Project;
6. never invent a separate Rule record type or rewrite imported Decisions as a different schema.

## Repository shape

- `README.md`: top-level methodology/framework split and navigation.
- `docs/methodology.md`: methodology boundary.
- `docs/framework.md`: reference-framework boundary.
- `docs/`: methodology handbook plus clearly labelled framework/exploration documents.
- `.decisions/`: this repository's use of the reference framework to preserve accepted Decision history.
- `templates/`: reference-framework artefacts.
- `ROADMAP.md`: proposed evolution and research.

If implementation experience disproves part of the handbook, update the handbook. Do not preserve a claim merely because it was previously written.
