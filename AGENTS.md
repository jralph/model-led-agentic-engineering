# Repository guidance for agents

This repository documents a human-owned engineering methodology. AI assistance is expected, including for drafting and restructuring the documentation itself, but the methodology must not be allowed to drift simply because an agent found a more fashionable way to describe it.

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
12. The methodology is currently a personal working method, not a validated standard.

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

## Repository shape

- `README.md`: short explanation and navigation.
- `docs/`: current methodology.
- `.decisions/`: immutable accepted human decision history; additions only after acceptance.
- `templates/`: practical artefacts engineers can copy.
- `ROADMAP.md`: proposed evolution and research, not current truth.

If implementation experience disproves part of the handbook, update the handbook. Do not preserve a claim because it was previously written down.
