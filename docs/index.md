# Multi-Observer Passive Attribution of Selective Forwarding Attacks in HH-VBF-Based Underwater Acoustic Sensor Networks

> Final-year project 23CSE498 · Group 103 · Department of Computer Science and Engineering, Amrita Vishwa Vidyapeetham, Coimbatore.

## What this project studies

Underwater acoustic sensor networks pass data to a sink over several hops. A compromised relay can quietly drop packets it should forward; this is called **selective forwarding**.

In **hop-by-hop vector-based forwarding (HH-VBF)**, relays select themselves: each node inside a virtual pipe decides privately whether to forward. A neighbour that stays silent may therefore be behaving correctly. It may never have received the packet, a better-placed relay may have forwarded first, or its forward may simply not have been heard. Silence alone is never proof of a drop (see [Problem](problem.md)).

This project measures how well **passive neighbours**, which only overhear traffic, can still attribute dropping to the right nodes. Every result is checked against simulator ground truth.

## Problem statement

> **Does HH-VBF-specific eligibility help a passive observer attribute selective forwarding, compared with generic pipe geometry?**

The answer led to two follow-up questions: does combining the evidence of several observers help, and why do some honest nodes look suspicious?

## Objectives

1. Explain why a neighbour's silence is ambiguous evidence in HH-VBF.
2. Test, under an analysis plan fixed in advance, whether HH-VBF eligibility rules help a single observer more than generic pipe geometry (**Study A**).
3. Test on fresh networks whether combining all observers of a node beats relying on its most suspicious observer (**Study B**).
4. Measure how honest-node scores depend on how many observers judge them, and how much collisions explain (**Study B**).
5. Compare the approach with an adapted channel-aware trust model (**Study C**).
6. Keep every reported number traceable to frozen, hash-verified outputs.

## Key results

![Study B: median fusion versus the maximum-pair rule, change in AUC with 95% intervals for five attack conditions; four are significant, the adaptive attacker is inconclusive.](figures/fig2_fusion.svg)

| Study | Question | Result |
|---|---|---|
| **A** | Do HH-VBF eligibility rules help a single observer? | **No meaningful gain.** ΔAUC = +0.0019, 95 % interval [-0.0234, +0.0321]; a gain of 0.05 or more is ruled out. |
| **B** | Does combining observers (median) beat the most suspicious observer (maximum)? | **Yes, in four of five attack conditions:** AUC improved by +0.051 to +0.075. In the standard condition, the share of active droppers detected rose from 4.8% to 52.0%. Against an adaptive attacker the result is inconclusive. |
| **B** | Why do some honest nodes look suspicious? | Honest scores rise with the number of observers (mean correlation +0.416). Collisions that hide genuine forwards explain a replicated part of this rise (+0.274). |
| **C** | How does fusion compare with channel-aware trust? | Adding collision-state evidence to median fusion gave a small further gain (+0.014 to +0.031 in AUC). Our fusion rule was not shown to outperform the comparator's maximum rule. |

All findings come from one simulated scenario. Details: [Results and interpretation](results.md); boundaries: [Scope](scope.md) and [Limitations](limitations.md).

## Pages

- [Problem and research question](problem.md)
- [Architecture](architecture.md) and [Methodology](methodology.md)
- [Results and interpretation](results.md) and [Literature context](literature.md)
- [Reproducing the study](reproduction.md), [Code and repository](repository.md) and [Artifact provenance](provenance.md)
- [Team and progress](team.md)
