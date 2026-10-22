# Problem statement and research question

## Background

**The attack.** Selective forwarding, or grey-hole behaviour, is a recognised insider attack in underwater networks (Zhu et al., IEEE COMST 2024).

**Watchdog monitoring and its limits.** A watchdog overhears whether neighbours forward packets. It can fail under several conditions (Marti et al., MobiCom 2000):

- ambiguous collisions;
- receiver collisions;
- limited transmission power;
- false misbehaviour;
- collusion;
- partial dropping.

## Why HH-VBF makes it harder

| How the next hop is chosen | What the observer must do |
|---|---|
| In **sender-selected** opportunistic routing, the sender knows its prioritised candidates and expects their acknowledgements (Salehi et al., Wireless Networks 2016). | — |
| In **HH-VBF** (Nicolaou et al., OCEANS 2007), relays inside a per-hop pipe self-select using a holding time computed from their own position. | Infer which neighbour *should* have forwarded, from possibly stale positions. |

## Why silence is not proof of a drop

When the observer expects a neighbour to forward and records nothing, these events look the same to it:

- the neighbour never decoded the copy;
- it acted on a different upstream copy;
- it forwarded, but the observer did not hear it;
- it was suppressed by a better-placed relay, or was ineligible from its true (not last-known) position;
- it dropped the packet.

A node that never transmits has no neighbour entry at any observer at all. A passive observer can therefore estimate only a *tendency* to be silent beyond what is expected, over many opportunities.

**Development diagnostic** (seed 1, drop probability 0.75; development data, **not** the confirmatory run):

| Cause of a recorded silence | Share of valid silent opportunities |
|---|---|
| candidate never decoded the copy | 37 % |
| candidate acted on a different upstream copy | 32 % |
| candidate forwarded, but the observer did not hear it | 20 % |
| drop by the candidate | 5.7 % (209 of 3,679) |
| ineligibility and suppression | not itemised |

In separate development runs, 64.0 % of drops were observable by a passive peer at drop probability 0.75. At drop probability 1.0, 34 of 42 active malicious nodes were never observable.

## Research question

> **Given identical observer-local inputs, does conditioning a passive observer on HH-VBF-specific eligibility rules add pair-level discrimination over a generic per-hop pipe-geometry expectation?**

This question is about the limits of passive attribution in receiver-driven HH-VBF. It asks how much of a passive observer's attribution ability comes from HH-VBF-specific eligibility conditioning, rather than from generic geometric expectation.

The question is tested with a single, prespecified primary comparison: O1 against B-PIPE.

## What the project does not claim

- **No new detector** is proposed.
- **No superiority** is claimed, nor equivalence, nor priority ("first") over prior work.
- **No generalisation** is claimed beyond the simulated scenario.
- **Synthetic software tests are not research findings.** The pipeline's software tests verified the code on synthetic fixtures only.
