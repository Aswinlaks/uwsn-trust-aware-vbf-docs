# Limitations

| Limitation | Status |
|---|---|
| **Interval coverage:** with ten seed clusters, the nominal coverage of the percentile cluster-bootstrap interval has not been established | unresolved |
| **Seed provenance (D03, verbatim):** "The confirmatory run indices appear in no inspected local artifact, but they could not be proven globally unused, because an earlier 40-seed batch is undocumented. No outcome from them existed in, or informed, this project before the freeze." | accepted limitation |
| **Residual pipeline risk R-1 (D08):** a rare double failure in emulation recording could leave an output tree indistinguishable from a successful one. It was mitigated by an operating rule, which was satisfied in this run. | accepted; mitigated, **not eliminated** |
| **External validity:** one simulator; one topology family, density, mobility, traffic pattern, attacker fraction and drop probability; offline, end-of-run analysis | unresolved |
| **Construct validity:** B-PIPE is an adapted baseline; the two O1 components are tested jointly; labels come from simulator logs | inherent to the design |
| **Calibration:** thresholds come from clean development runs; the held-out false-alarm rates are descriptive and do not validate the calibration | descriptive only |
| **Detection / TDR:** no intervals or tests under the frozen protocol | by design |
| **Per-method AUCs:** not among the frozen outputs | not reported |
| **Software verification:** the pipeline's tests used synthetic fixtures; they verify code behaviour, not research claims | by design |
| **Literature:** a curated corpus, not a systematic database search. Fig. 2 is an evidence map: literature values are the authors' printed numbers, not reproductions, and are not placed on a common scale with ours | unresolved |
