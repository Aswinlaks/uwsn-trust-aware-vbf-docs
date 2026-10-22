# Literature context

Fig. 2 is an **evidence map**, not a performance comparison. For this study and the five supplied papers that report detection-type results, it records:
- the network and evaluation setting;
- the attack model;
- the evidence available to the detector;
- the metrics and values the authors report, under the authors' own names and units;
- comparability with this study.

No study is placed on a numerical axis. This study's own results are in Figs. 1 and 3 on [Results and interpretation](results.md).

![Fig. 2: evidence map, a table with six rows (this study; Liu et al. 2024; Ye and Jiang 2024; Das et al. 2024, AIDPS; Zhang et al. 2023, DOIDS; Khoshvaght et al. 2026, EAQTE) and six columns: paper, network and evaluation setting, attack model, evidence available to the detector, metrics and values reported, and comparability with this study. No values are plotted on an axis.](figures/fig2_literature.svg)

## What each paper reports

| Paper | Metric (authors' name) and definition | Printed values and conditions | Comparability with this study |
|---|---|---|---|
| Liu et al. 2024 [4] | **FDR** = Nnm/(Nnm+Nnn), over all normal nodes; **MDR** = Nmn/(Nmn+Nmm), over all malicious nodes (Eqs. 15–16, p. 9) | Table 8, p. 18; malicious-node ratio 0.20, N = 300; no / mobile / immobile harsh environment: FDR 0.79% / 0.83% / 2.16%; MDR 2.33% / 1.16% / 5.83% | **Partial: definitions only.** Terrestrial network; the detector receives forwarded/received counts from inspection nodes; flagged nodes are removed. FDR's denominator (all normal nodes) differs from our node false-alarm denominator (honest nodes with a judged pair). |
| Ye & Jiang 2024 [9] | **"malicious node detection accuracy"**; formula and denominator not defined in the paper | Table 3, p. 13; gray hole (discard rate 0.4), 20 % malicious nodes, 100 nodes, 150 rounds: 0.871 (no unit printed) | **Not numerically comparable.** The metric is undefined, so the value cannot be equated with any measure in this study. |
| Das et al. 2024, AIDPS [11] | **accuracy, AUC, FPR** of a hybrid classifier over labelled dataset instances | p. 11 (printed p. 1090), testing dataset: accuracy 0.9774, AUC 0.977, FPR 0.023 | **Not comparable.** Instance-level supervised classification, not pair-level attribution by passive observers. |
| Zhang et al. 2023, DOIDS [10] | **TPR, FPR, AUC, detection accuracy rate** (node level) | curves only (Figs. 8, 9, 12); no values extracted | **Not numerically comparable.** No tabulated values; none was read off the curves. |
| Khoshvaght et al. 2026, EAQTE [12] | **detection accuracy rate, false alert rate**, relative to other schemes | relative only, e.g. detection accuracy improved by 7.01% against TUMRL, ARTMM and TMC (p. 1) | **Not numerically comparable.** No absolute rates. |

## How to read it

- **Context, not a ranking.** The networks, attack settings, detector evidence, metric definitions, denominators and protocols all differ. The values cannot support a performance ranking against our experiment, and they do not explain why our methods behave as they do.
- **Different evidence.** The detectors in these papers use evidence that our passive observers do not have: packet counts reported by inspection nodes (Liu et al.), trust models (Ye & Jiang, EAQTE), labelled training instances (AIDPS), or monitoring of a sender-side candidate set (DOIDS).
- **No reproduction.** No prior method was re-run in our setting.

## Rules followed

- Values are copied as printed, with the authors' metric names and units.
- No derived quantity is shown. The extraction record keeps 1 − MDR for Liu et al. for audit only, marked as derived.
- No value was read off a plotted curve.
- For every value, the source page, table and an exact quote are recorded and checked automatically against the PDF. The Liu et al. and Ye & Jiang tables were also checked on rendered page images.

## References (numbering as in the paper)

- [4] L. Liu, Y. Ma, and Y. Wu, "A robust detection scheme against selective forwarding attacks in wireless sensor networks under variable harsh environments," Eng. Appl. Artif. Intell., vol. 138, Art. no. 109392, Dec. 2024, doi:10.1016/j.engappai.2024.109392.
- [9] J. Ye and W. Jiang, "Routing protocol for underwater wireless sensor networks based on a trust model and void-avoided algorithm," Sensors, vol. 24, no. 23, Art. no. 7614, 2024, doi:10.3390/s24237614.
- [10] R. Zhang, J. Zhang, Q. Wang, and H. Zhang, "DOIDS: An intrusion detection scheme based on DBSCAN for opportunistic routing in underwater wireless sensor networks," Sensors, vol. 23, no. 4, Art. no. 2096, 2023, doi:10.3390/s23042096.
- [11] S. Das, A. M. Pasikhani, P. Gope, J. A. Clark, C. Patel, and B. Sikdar, "AIDPS: Adaptive intrusion detection and prevention system for underwater acoustic sensor networks," IEEE/ACM Trans. Netw., vol. 32, no. 2, pp. 1080-1095, Apr. 2024, doi:10.1109/TNET.2023.3313156.
- [12] P. Khoshvaght, M. Alhussein, K. Aurangzeb, E. Yousefpoor, J. Lansky, and M. Hosseinzadeh, "An environment-aware Q-learning-based trust evaluation scheme in underwater acoustic sensor networks (UASNs)," Comput. Stand. Interfaces, vol. 96, Art. no. 104087, Mar. 2026, doi:10.1016/j.csi.2025.104087.
