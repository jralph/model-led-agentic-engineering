# Adversarial review brief

Your objective is to find material ways this design or implementation fails to satisfy its stated intent.

Do not optimise for agreement.

Do not silently redefine the requirements.

## Inputs

- intent/spec:
- implementation/change:
- relevant active/proposed decisions:
- relevant invariants:
- accepted trade-offs:

## Review questions

1. Where does the implementation differ semantically from the stated intent?
2. Which behaviour appears to have been inferred rather than specified?
3. Can any protected invariant be violated?
4. Are trust or permission boundaries enforced at the authoritative layer?
5. What happens under retries, concurrency, partial failure and stale state?
6. Which failure states are incorrectly reported as success?
7. Has scope expanded outside the stated non-goals?
8. Do tests exercise the production seam or a duplicate?
9. Which claims are stronger than the evidence?
10. What is the simplest counter-example to the current design?

## Output

For each material finding:

- severity;
- evidence;
- affected invariant/behaviour;
- why it matters;
- suggested next action.

If no material finding exists, state what was actually inspected and what remains unverified.
