# Methodology

## Simulated network

| Item | Value |
|---|---|
| Nodes | 100 (1 fixed sink, 99 mobile sensors; meandering-current mobility, 0.3 m/s unless stated) |
| Volume | 3000 × 3000 × 2500 m |
| Traffic | 10 sources; 80-byte packets; 0.033 packets/s; runs of 3000 s |
| Channel | 1000 m range-limited propagation, no ambient noise; a packet is lost only when another arrival overlaps it (collision) |
| Routing | HH-VBF, pipe width 400 m; trust influence on forwarding disabled |
| Attackers | selective-forwarding insiders (20 % unless stated) that drop packets they should forward with probability p |

## Conditions

| Name | Setting | Used in |
|---|---|---|
| CL03 / CL06 | clean (no attackers), 0.3 / 0.6 m/s | Study B; Study C (CL03) |
| S75 | 20 % insiders, p = 0.75 (standard) | Studies A, B, C |
| S30 | 20 % insiders, p = 0.3 (stealthy) | Studies B, C |
| ENV | 20 % insiders, p = 0.75, drop only when their neighbourhood is thinner than usual (adaptive) | Studies B, C |
| V06 | 20 % insiders, p = 0.75, 0.6 m/s (fast current) | Study B |
| AF30 | 30 % insiders, p = 0.75 | Study B |

Study A used seeds 41–50, Study B seeds 211–240 (30 networks per condition), Study C seeds 241–280 (40 per condition). Thresholds were calibrated on clean seeds 12–21.

## From records to scores

1. **Opportunities.** For each forwarding event an observer saw or made, every neighbour heard in the last 60 s that lies in range and inside the per-hop pipe is a *candidate*.
2. **Outcome.** Using only copies the observer decoded within 8 s: **MATCH** (the candidate forwarded this copy), **SILENT** (nothing heard), or **OTHER-UP** (it forwarded another copy; not scored).
3. **O1 vs B-PIPE.** O1 also applies Aqua-Sim-NG's VBF priority test and groups opportunities by the candidate's holding-time rank. B-PIPE, an adapted baseline defined for this study, uses pipe geometry only.
4. **Pair score.** For each observer–neighbour pair, r = (K − Σq)/n, where n counts scored opportunities, K the SILENT ones, and q is the expected silence rate on clean networks. A pair is *judged* if n ≥ 14.

## Node rules

| Rule | How a node's score is formed |
|---|---|
| **R0** (max-pair) | the largest pair score among the observers that judge the node (needs ≥ 1) |
| **R3** (median fusion) | the median pair score (needs ≥ 3 judging observers) |
| **BETA** (count baseline) | the median of (K + 1)/(n + 2): plain silence counts, no expectation model |
| **full7** (exploratory) | R3 minus a prediction of honest R3 from seven observer-side features |
| **CA** (Study C) | an adapted channel-aware subjective-logic score that counts outcomes separately when the observer itself logged a collision, built on Signori et al. 2022 |

A node is flagged when its score exceeds the 95th percentile of honest scores on the clean calibration networks. **Lying observers** (Study B and C, secondary): insiders report every opportunity about honest nodes as SILENT and about insiders as MATCH (worst case), or shift a quarter of their reports (camouflaged).

## Statistics

| Study | Main test | Uncertainty | Decision |
|---|---|---|---|
| **A** | ΔAUC (O1 − B-PIPE) on pairs both methods judge | seed-then-node cluster bootstrap, 10,000 replicates | predeclared six-way rule with minimum meaningful improvement δ = 0.05 |
| **B** | H1: AUC(R3) > AUC(R0) in five conditions; H2: honest scores rise with coverage; H3: the rise shrinks when unheard genuine forwards are counted as heard | network-cluster bootstrap, 10,000 replicates, one-sided | Holm correction over H1 at level 0.025; H2 then H3 in a fixed sequence |
| **C** | nine contrasts: C1 channel state, C2 fusion, C3 R3 vs the comparator's max rule, each in S75, S30 and ENV | network-cluster bootstrap, 10,000 replicates, two-sided | Holm correction at 0.05; smallest effect of interest 0.02 |

**Study A decision rule** (classification uses the exact bounds L and U):

| Verdict | Condition | Meaning |
|---|---|---|
| V1 | L ≥ δ | meaningful improvement shown |
| V2 | 0 < L < δ ≤ U | positive; meaningfulness unresolved |
| V3 | 0 < L and U < δ | positive; meaningful improvement ruled out |
| V4 | L ≤ 0 and U ≥ δ | inconclusive |
| **V5** | **L ≤ 0 and 0 < U < δ** | **meaningful improvement ruled out; a smaller positive effect neither shown nor excluded** |
| V6 | U ≤ 0 | no positive improvement |

**Prespecification.** Each study's plan, code and thresholds were frozen by hash before its data existed; the plans were not lodged with an external registry.
