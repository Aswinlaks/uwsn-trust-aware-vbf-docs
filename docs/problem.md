# Problem statement and research question

## Background

**The attack.** Selective forwarding, or grey-hole behaviour, is a recognised insider attack in underwater networks (Zhu et al., IEEE COMST 2024). A compromised relay forwards most packets but drops some of the ones it should relay.

**Watchdog monitoring and its limits.** A watchdog node overhears whether its neighbours forward packets. It can misjudge a neighbour, for example when collisions hide a forward from the watchdog (Marti et al., MobiCom 2000). Separating deliberate drops from ordinary loss is a long-standing problem (Shila et al. 2010; Ren et al. 2016).

## Why HH-VBF makes it harder

| How relays are chosen | What a passive observer can know |
|---|---|
| In **sender-selected** opportunistic routing, the sender names its prioritised candidates and expects their acknowledgements (Salehi et al. 2016). | Who was expected to forward. |
| In **HH-VBF** (Nicolaou et al. 2007), every node inside a per-hop pipe decides for itself, using a holding time computed from its own position. Nodes that overhear a better-placed forward may legitimately stay silent. | Only an estimate, from possibly out-of-date positions. |

## Why silence is not proof of a drop

When an observer expects a neighbour to forward and records nothing, these events look the same to it:

- the neighbour never decoded the packet;
- it acted on a different copy of the packet;
- it forwarded, but the observer did not hear it;
- it was suppressed by a better-placed relay;
- it dropped the packet.

A passive observer can therefore only estimate a neighbour's *tendency* to be silent beyond what is expected, over many opportunities.

**Development diagnostic** (seed 1, drop probability 0.75; development data, not a confirmatory result):

| Cause of a recorded silence | Share |
|---|---|
| candidate never decoded the copy | 37 % |
| candidate acted on a different upstream copy | 32 % |
| candidate forwarded, but the observer did not hear it | 20 % |
| drop by the candidate | 5.7 % |

## Research questions

**Main question (Study A):**

> **Does HH-VBF-specific eligibility help a passive observer attribute selective forwarding, compared with generic pipe geometry?**

**Follow-up questions:**

- **Study B:** does aggregating the evidence of all observers that judge a node beat the rule that trusts its single most suspicious observer? How do honest-node scores depend on how many observers judge them?
- **Study C:** how does this aggregation compare with an adapted channel-aware trust model built on Signori et al. (IEEE IoT J 2022)?

## What the project does not claim

- **No new detector** and no new trust model. Multi-observer aggregation, channel-state weighting and collision-aware loss estimates are established ideas.
- **No claim of outperforming** published methods, and no equivalence claims.
- **No generalisation** beyond the simulated scenario.
