# Repository guidance for agents

This repository documents a human-owned engineering methodology. AI assistance is expected, including for drafting and restructuring the documentation itself, but the methodology must not be allowed to drift simply because an agent found a more fashionable way to describe it.

## Core contract

> **Model-led defines what engineering knowledge and authority need to exist. It does not prescribe how tools should execute against them.**
>
> **Humans own intent, judgement and decisions.**  
> **Agents explore, research, implement, challenge and verify.**  
> **Semantic implementation must not outrun its Decision basis.**  
> **Evidence determines what can actually be claimed.**

## Core intent

Preserve these ideas unless the owner explicitly changes them:

1. The human engineer owns the coherent semantic model, technical direction and accountability for the system.
2. Agents may contribute research, ideas, local reasoning, implementation and critique.
3. Implementation may be delegated without delegating understanding.
4. Agent work should happen in explicit modes with bounded authority.
5. Claims about correctness, safety, performance or productivity require evidence appropriate to the claim.
6. Source code is one representation of engineering intent, not the only measure of engineering authorship.
7. Language and framework constraints still matter. "Language-independent model" does not mean implementation details are irrelevant.
8. Accepted engineering decisions require human authority. Agents may draft decision records only from explicit human decisions; they must not originate accepted decisions.
9. Accepted files under `.decisions/` are append-only history. Never edit, rename or delete an accepted record; supersede it with a new human-authored decision.
10. Model-led agentic engineering governs above the implementation workflow. Do not rewrite it as a mandatory spec-driven, task-driven or tool-specific process.
11. Decision-first review is a core practice: humans prioritise decisions and accepted risk; agents can perform exhaustive conformance review; direct human code review remains risk-based.
12. Intent is human-owned, mutable and pre-decisional. Agents may help refine or research it but must not silently change the human objective and treat the change as authoritative.
13. Challenges are pre-decisional questions and may be raised by humans or agents. They may question existing Decisions or expose missing Decision authority without changing the model.
14. Meaningful semantic implementation requires a sufficient Decision basis. Intent or Challenge alone does not authorise new system semantics.
15. The methodology does not prescribe a Task object, .intents/ or .challenges/ storage convention. Those are implementation/workflow choices.
16. The methodology is currently a personal working method, not a validated standard.

## Writing rules

- Use British English.
- Prefer plain engineering language over AI-industry marketing language.
- Do not describe the approach as "10x", "revolutionary", "the future of software engineering", or similar.
- Do not imply that humans are no longer needed to understand code.
- Do not imply that an agent can verify its own work merely by saying it reviewed it.
- Do not turn every concept into a framework, acronym or score.
- Distinguish observed practice, proposed practice and future research.
- Examples should be generic and should not depend on knowledge of any private or branded product.
- Keep the handbook readable before making it academically complete.

## Evidence rules

When documenting measurements:

- record what was actually measured;
- preserve failed and inconclusive results;
- state the evidence boundary;
- do not promote fixture evidence into live-system evidence;
- do not treat a finite zero-failure sample as proof of universal correctness;
- do not collapse several metrics into a composite productivity score without empirical justification.

## Bootstrapping Model-led into another repository

If a user points an agent at this methodology repository and asks to **set up Model-led** in a new or existing target repository, treat that as an adoption/bootstrap request.

Read and use:

- `docs/adoption.md`;
- `templates/model-led-agent-guidance.md`;
- `.decisions/README.md`;
- `.decisions/schema.yaml`.

Then:

1. **Inspect the target repository first.** Read its existing root/subtree agent instructions, documentation and structure. Do not assume a blank repository.
2. **Preserve existing guidance.** If the target has `AGENTS.md`, merge the reusable Model-led guidance into it. Do not replace repository-specific build, test, language, security, architecture or release instructions.
3. **Create the canonical Decision library** at `.decisions/` if it does not exist:
   - `.decisions/README.md` using the current portable append-only rules;
   - `.decisions/schema.yaml` using the current schema.
4. **Do not create `.intents/`, `.challenges/`, `.model/` or a generic Task system** unless the target repository's chosen workflow explicitly calls for them.
5. **Do not infer historical Decisions from code.** Existing source, tests and architecture may reveal behaviour or missing authority, but they are not proof of human Decisions.
6. **Existing repository adoption:** when the user explicitly asks to retrofit Model-led into an established repository, that request is normally sufficient human authority to draft the first proposed process Decision stating that the repository adopts Model-led as its engineering governance method. The Decision is not accepted until the bootstrap change is accepted/merged. Do not backfill any other Decisions without explicit human judgement.
7. **New project adoption:** when the project is being created as Model-led from inception, do not create a ceremonial adoption Decision. Begin with an empty Decision library and record Decisions only as real semantic choices arise.
8. **Validate conservatively.** Run appropriate existing checks for the files changed and report any ambiguity or incompatibility rather than overwriting it.
9. **Explain the resulting boundary:** Intent and Challenge are storage-agnostic; accepted Decisions live in `.decisions/`; meaningful semantic implementation must have a sufficient Decision basis.

A bootstrap should leave the target repository ready to use Model-led without coupling it to this repository, a specific agent harness or a specific project-management tool.

## Repository shape

- `README.md`: short explanation and navigation.
- `docs/`: current methodology.
- `.decisions/`: immutable accepted human decision history; additions only after acceptance.
- `templates/`: practical artefacts engineers can copy.
- `ROADMAP.md`: proposed evolution and research, not current truth.

If implementation experience disproves part of the handbook, update the handbook. Do not preserve a claim because it was previously written down.
