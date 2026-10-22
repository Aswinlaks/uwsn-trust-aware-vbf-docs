# Passive attribution of selective forwarding in HH-VBF: O1 vs B-PIPE

> **Status:** documentation of a final-year research project (reporting v3). The research paper draft is not published on this site.

## What this project studies

In underwater acoustic sensor networks that use **hop-by-hop vector-based forwarding (HH-VBF)**, each relay decides privately whether to forward a packet. A passive neighbour can only see its own records. A silent neighbour may be **dropping packets on purpose** (selective forwarding), but it may equally have:
- never received the packet;
- forwarded a different copy;
- forwarded unheard;
- been suppressed by a better-placed relay.

So **silence alone never proves that a particular relay dropped a particular packet** (see [Problem](problem.md)).

This project studies the limits of such passive attribution with one narrow, testable question:

> **Given identical observer-local inputs, does conditioning a passive observer on HH-VBF-specific eligibility rules add pair-level discrimination over a generic per-hop pipe-geometry expectation?**

## Objectives

1. **Explain the problem.** Show why, in HH-VBF, a passive observer (a node that uses only what it overhears) cannot treat a neighbour's silence as proof that the neighbour dropped a packet.
2. **Answer one narrow question.** Test whether adding HH-VBF-specific eligibility rules (the O1 observer) improves pair-level discrimination, that is, how well a score separates dropping neighbours from honest ones, over a generic pipe-geometry baseline (B-PIPE), when both use identical observer-local inputs.
3. **Test it under a fixed plan.** Freeze the protocol, code and dependencies by hash before the ten held-out simulation seeds are analysed once. Then classify the result with a predeclared decision rule, with a minimum meaningful improvement of δ = 0.05.
4. **Report supporting results descriptively.** Report false-alarm and detection results for both methods without letting them change the primary verdict.
5. **Place the work in context.** Compare this study's setting and evidence with a supplied set of related papers through a source-traceable evidence map, without ranking unlike metrics.
6. **Make the results checkable.** Document the frozen pipeline and its output hashes, so that the reported numbers can be verified.

## The two methods compared

| Method | What it is |
|---|---|
| **O1** | The project's passive observer. It expects a neighbour to forward only if the neighbour is in range, inside the per-hop pipe, **and** satisfies the Aqua-Sim VBF priority test. Its expectations are stratified by HH-VBF hold-time rank. |
| **B-PIPE** | An adapted baseline defined for this study (not an established or published protocol). It is the same pipeline **without** the priority test and the rank strata, which leaves generic pipe geometry only. |

## The answer (confirmatory run, ten held-out seeds)

![Primary result: ΔAUC = +0.0019 with 95% interval from −0.0234 to +0.0321; the interval contains 0 and lies 0.0179 below δ = 0.05.](figures/fig1_primary.svg)

| | |
|---|---|
| ΔAUC (O1 − B-PIPE), on the 1,806 pairs both judge | **409/210816 ≈ +0.0019** |
| 95 % percentile cluster-bootstrap interval | **[−0.0234, +0.0321]** |
| Minimum meaningful improvement (predeclared) | δ = 0.05; U lies 0.0179 below it |
| Frozen verdict | **V5:** an improvement of at least 0.05 is ruled out; a smaller positive effect is neither shown nor excluded |

**Read this carefully.** V5 is an operational classification under a predeclared rule. It does **not** mean the methods are equivalent, that O1 has no benefit, or that O1 is worse. Also, with ten seed clusters, the interval's nominal 95 % coverage has **not** been established.

See [Results and interpretation](results.md), [Literature context](literature.md), [Scope and future work](scope.md) and [Limitations](limitations.md).
