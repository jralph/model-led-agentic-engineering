# Qualification plan

Define this before final qualification where practical.

Evidence applies to a specific claim, implementation subject and Decision context. Avoid treating a passing result as universal proof.

## Claim

What exactly are we trying to demonstrate?

## Subject under qualification

Which exact implementation, build, deployment, artefact or revision does this evidence apply to?

Use the most precise identifier available in the chosen workflow. This does not need to be a Git SHA.

## Intent / Challenge context

Which active Intent or Challenge makes this claim relevant?

Optional where obvious.

## Decision basis

Which accepted Decisions define or constrain the claim?

Which adopted Ruleset snapshots are resolved from that Decision basis?

Which proposed Decisions, if any, is this candidate being evaluated against?

Do not treat proposed Decisions as authoritative.

## Evidence class

- [ ] E0 static
- [ ] E1 deterministic behavioural
- [ ] E2 integration
- [ ] E3 production seam
- [ ] E4 live dependency
- [ ] E5 deployed path
- [ ] E6 end-to-end user path

## Scope

What cases, environments and dependencies are included?

## Exclusions

What does this qualification explicitly not demonstrate?

## Success conditions

Define before running the final measurement.

## Failure categories

Keep meaningful failure classes separate.

Examples:

- incorrect success;
- safe refusal;
- timeout;
- provider failure;
- infrastructure failure;
- validation failure.

## Metrics

Only metrics relevant to the claim.

## Result

Record raw counts/distributions where possible.

State whether the evidence still applies to the exact subject and Decision basis named above.

## Challenges raised

Did qualification expose a contradiction, missing Decision, weak evidence boundary or other unresolved question?

- 

## Residual risk

What remains unknown or explicitly accepted?

If accepting the risk materially constrains future engineering, consider whether that acceptance itself needs a human-accepted Decision.
