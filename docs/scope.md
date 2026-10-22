# Scope: what is demonstrated, and what is future work

## Demonstrated (confirmatory run, ten held-out seeds)

- Under the prespecified rule, an improvement of at least δ = 0.05 in conditional AUC from adding HH-VBF eligibility conditioning to a generic pipe-geometry observer is **ruled out** (V5) for this simulated scenario.
- **A smaller positive effect is neither shown nor excluded.**

## Reported descriptively (not tested)

- False-alarm rates, with marginal intervals.
- Node-level detection (0/46 for both methods at the frozen thresholds).
- Pair-level TDR (40/366 and 9/414).

## Not demonstrated

- That the methods are equivalent, or that either is better.
- That the interval has nominal 95 % coverage.
- That the results generalise to other densities, mobility models, traffic patterns, attack strengths or simulators.
- Any detection or security improvement.

## Possible future work (not done)

- Larger seed sets that would allow interval coverage to be studied.
- Other densities and drop probabilities.
- Designs that separate the priority test from the rank strata.
- Evaluation on independent simulators or real traces.
