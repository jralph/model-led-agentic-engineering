# Adversarial review brief

Your objective is to find material ways this candidate design or implementation fails to satisfy the active Intent, Decision basis or supported claims.

Do not optimise for agreement.

Do not silently redefine Intent, Decisions or acceptance criteria.

## Inputs

- active Intent:
- originating / related Challenges:
- accepted Decision basis:
- adopted Ruleset snapshots resolved from that basis:
- proposed Decisions under evaluation:
- implementation / candidate under review:
- qualification evidence:
- accepted trade-offs / residual risk:

## Review questions

1. Does the candidate actually pursue the stated Intent?
2. Does any semantic behaviour outrun the accepted Decision basis?
3. Is the implementation relying on a proposed Decision as though it were already authoritative?
4. Does the implementation conflict with any accepted Decision or adopted Rule?
5. Are local exceptions being hidden by editing copied Rules rather than expressed as Project Decisions?
6. Is a semantic choice being hidden as an ordinary implementation detail?
7. Which behaviour appears to have been inferred rather than authorised?
8. Can any protected invariant be violated?
9. Are trust or permission boundaries enforced at the authoritative layer?
10. What happens under retries, concurrency, partial failure and stale state?
11. Which failure states are incorrectly reported as success?
12. Has scope expanded outside the stated non-goals?
13. Do tests exercise the relevant production seam or only a duplicate?
14. Which claims are stronger than the supplied evidence?
15. What is the simplest counter-example to the current design?

## Output

For each material finding, classify it where possible as:

- implementation/conformance defect;
- Decision conflict;
- missing Decision authority;
- Intent mismatch;
- evidence gap;
- residual risk;
- other.

Then record:

- severity;
- evidence;
- affected Intent / Decision / invariant / behaviour;
- why it matters;
- suggested next action;
- whether a Challenge should be raised or updated.

Do not make an unresolved semantic choice authoritative merely to complete the review.

If no material finding exists, state what was actually inspected, which Decision basis was used, and what remains unverified.
