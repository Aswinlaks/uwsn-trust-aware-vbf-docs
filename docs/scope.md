# Scope: what is demonstrated, and what is future work

## Demonstrated in this simulated scenario

- **Study A (confirmatory):** adding HH-VBF eligibility rules to a single passive observer does not improve discrimination over generic pipe geometry by 0.05 AUC or more (verdict V5). A smaller positive effect is neither shown nor excluded.
- **Study B (prespecified, fresh networks):** combining the evidence of all observers of a node through the median improves node-level attribution over the max-pair rule in four of five attack conditions.
- **Study B:** honest-node scores rise with the number of observers that judge them, and collisions that hide genuine forwards explain a replicated part of this rise.
- **Study C (prespecified, completed under a recovery amendment):** adding collision-state evidence to median fusion gives a small further gain.

## Reported descriptively (not tested)

- Detection and honest false-alarm rates at the frozen thresholds.
- Results under two simulated lying-observer policies.

## Not demonstrated

- That median fusion beats the max-pair rule against the adaptive (ENV) attacker.
- That our fusion rule outperforms the adapted channel-aware comparator.
- That the coverage-based adjustment (full7) generalises; it did not.
- That the results hold in noisy or fading channels, other densities and topologies, or other simulators.

## Possible future work

- A second scenario with a different density or topology.
- A realistic noisy channel, where channel-state evidence is not near-perfect.
- Collusive observers and position falsification.
