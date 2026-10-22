# Methodology

## Experimental design

| Item | Value |
|---|---|
| Nodes | 100 (1 fixed sink, 99 mobile sensors; meandering-current mobility) |
| Volume | 3000 × 3000 × 2500 m |
| Traffic | 10 sources; 80-byte packets; 0.033 packets/s; 2–2900 s; runs of 3000 s |
| Physical / MAC | 1000 m range-limited propagation; broadcast MAC |
| Routing | HH-VBF, pipe width 400 m (trust influence disabled) |
| Attack | 20 % malicious insiders; drop probability 0.75 |
| Calibration seeds | 12–21 (clean, development) |
| Confirmatory seeds | 41–50 (held out; generated once after the freeze) |

## Methods

**O1 and B-PIPE share:**
- inputs, freshness rule, exclusions, range and pipe tests, hearing filter;
- outcome rule (causal 8 s bound), score form, the judging rule n ≥ 14, and the evaluation.

**Outcome of an opportunity.** It uses only copies of the packet the observer decoded from the candidate no later than 8 s after the event:
- **SILENT** if there is none;
- **MATCH** if the first copy carries an upstream position within 25 m of the expected upstream;
- **OTHER-UP** otherwise (the candidate forwarded for a different upstream). OTHER-UP opportunities are not scored.

**Score.** The per-pair score is r = (K − Σ q)/n, where K counts SILENT outcomes, n counts scored opportunities, and q is the clean expected silence rate of each opportunity's stratum.

**Labels.** These are applied by the evaluator only, after scoring:
- an **active dropper** is a malicious node with at least one recorded drop in that run;
- **inactive malicious** nodes (no drop) belong to neither class and are excluded.

**What O1 adds:**
- the Aqua-Sim VBF priority test (α ≤ 1.5);
- the HH-VBF hold-time-rank strata.

B-PIPE is an adapted baseline defined for this study, not an established or published protocol; the comparison tests these two components **jointly**.

**Prespecification:** the protocol was frozen by hash before the confirmatory data existed; it was not lodged with an external registry.

## Statistics

- **Estimand:** ΔAUC = AUC(O1) − AUC(B-PIPE) on the **common judged set** (pairs both methods judge). It is described as "conditional discrimination on the pairs both methods judge".
- **AUC:** weighted Mann–Whitney statistic, active-dropper pairs versus honest pairs, ties counted ½. It can be read as the probability that a random dropper pair scores higher than a random honest pair (Hanley & McNeil, *Radiology* 1982).
- **Interval:** seed-then-node cluster bootstrap with one shared draw sequence (PCG64, seed 12345), conditional on resamples containing both classes.
  - B = 10,000 valid replicates; draw cap N = 10,098 (from ε = 0.005 and γ = 1e-9).
  - Replicates are exact rationals, and percentiles are taken by exact linear interpolation.
  - A floating-point cross-check must agree within 1e-12.
- **Precheck:** the exact probability that a resample lacks a class must not exceed ε = 0.005; otherwise the result is NOT ESTIMABLE.

## Decision rule (predeclared; δ = 0.05)

| Verdict | Condition | Meaning |
|---|---|---|
| V1 | L ≥ δ | meaningful improvement shown |
| V2 | 0 < L < δ ≤ U | positive; meaningfulness unresolved |
| V3 | 0 < L and U < δ | positive; meaningful improvement ruled out |
| V4 | L ≤ 0 and U ≥ δ | inconclusive |
| **V5** | **L ≤ 0 and 0 < U < δ** | **meaningful improvement ruled out; positive effect neither shown nor excluded** |
| V6 | U ≤ 0 | no positive improvement |

Classification uses the exact, unrounded bounds.

## Secondary measures (descriptive)

- **Thresholds:** each method has its own thresholds, the nearest-rank 95th percentiles of its own clean development scores. They are set **separately at pair level and at node level**. A unit is flagged if its score is strictly greater than the threshold.
- **False-alarm rates:** pair and node level, each with a separate marginal 95 % interval.
- **Node-level detection:** an active dropper with no judged pair counts as missed.
- **Pair-level true-detection rate (TDR).**

Detection and TDR are counts and point estimates only; the frozen protocol defines no intervals for them.
