# Literature context

## What is already known

- **Drops versus ordinary loss.** Watchdogs can misjudge neighbours when collisions hide forwards (Marti et al. 2000). Channel-aware detection estimates a node's normal loss from channel quality and medium-access collisions (Shila et al. 2010; Ren et al. 2016).
- **Several observers.** Guard-based local monitoring isolates a node only when enough guards accuse it, and the false-alarm probability caused by collisions has been analysed for different numbers of guards (Khalil et al. 2007, 2010, 2011). Collaborative watchdogs share detections (Hernandez-Orallo et al. 2015).
- **Underwater overhearing trust.** Signori et al. (2021, 2022) weight overheard behaviour by an inferred channel state, for a single observer with flooding routing. Donegà et al. (2024, 2026) show that aggregating opinions from several nodes corrects false positives caused by bad channels.
- **Opportunistic routing.** In sender-driven opportunistic routing, the expected acknowledgements of each candidate can be computed from link quality and candidate priority (Salehi et al. 2016).

## Closest work and this study

| Work | Routing | Evidence and aggregation | Attackers | Evaluation |
|---|---|---|---|---|
| Signori et al. 2022 | flooding | channel-state-weighted overhearing; one observer | one dropper | analysis; 20 topologies × 50 runs |
| Donegà et al. 2026 | flooding | channel-based first-hand + weighted-mean second-hand | one dropper, slandering | 100 runs averaged; sea trial |
| Zhang et al. 2025 | sender-named next hop | HMM channel state; one observer | 2 of 20 nodes | 10 repetitions |
| Shila et al. 2010 | AODV paths | link loss vs normal loss (channel + MAC) | path droppers | 36 routers, 10 runs |
| Ren et al. 2016 | sender-driven | loss vs normal loss; reputation propagation | compromised nodes | 100 nodes |
| Khalil et al. 2007, 2011 | sender-driven | guards; quorum of alerts | insiders | analysis; ns-2 |
| Salehi et al. 2016 | sender-driven opportunistic | priority-aware expected acknowledgements | droppers | simulation |
| **This study** | **receiver-driven HH-VBF** | **opportunity-conditioned silence; median over observers** | **20–30 % insiders, lying observers** | **prespecified; fresh networks; per-network false alarms; ground truth** |

## Where this work fits

Multi-observer aggregation, channel-state weighting and collision-aware loss estimates are established ideas, and this project does not claim them. What we did not find in the literature reviewed is an evaluation of multi-observer passive attribution in **receiver-driven vector-based routing**, with many insiders, lying observers, per-network false alarms and a ground-truth breakdown of honest silence. The review was targeted, not a systematic database search, and the reported values of other studies are not comparable with ours.

## Key references

- S. Marti et al., "Mitigating routing misbehavior in mobile ad hoc networks," ACM MobiCom, 2000.
- D. M. Shila, Y. Cheng, T. Anjali, "Mitigating selective forwarding attacks with a channel-aware approach in WMNs," IEEE Trans. Wireless Commun., 2010.
- J. Ren, Y. Zhang, K. Zhang, X. Shen, "Adaptive and channel-aware detection of selective forwarding attacks in wireless sensor networks," IEEE Trans. Wireless Commun., 2016.
- I. Khalil, S. Bagchi, "Stealthy attacks in wireless ad hoc networks: Detection and countermeasure," IEEE Trans. Mobile Comput., 2011.
- A. Signori, F. Campagnaro, I. Nissen, M. Zorzi, "Channel-based trust model for security in underwater acoustic networks," IEEE Internet Things J., 2022.
- F. Donegà et al., "A collaborative system for reputation-based security in underwater acoustic networks," IEEE Trans. Commun., 2026.
- M. Salehi et al., "Towards a novel trust-based opportunistic routing protocol for wireless networks," Wireless Networks, 2016.
- N. Nicolaou et al., "Improving the robustness of location-based routing for underwater sensor networks," IEEE OCEANS, 2007.
