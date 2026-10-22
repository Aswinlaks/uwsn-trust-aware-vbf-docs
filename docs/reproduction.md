# Reproducing the study

> These steps describe how the confirmatory result was produced. A full re-execution would create **new** outputs. The authoritative outputs of this study are never regenerated or overwritten.

## Environment

| Component | Version / identity |
|---|---|
| ns-3 | 3.41, with the project's version of the Aqua-Sim-NG module; the frozen simulator is identified by the file hashes below |
| Scenario | `scratch/uwsn-trustq-attack.cc` (MD5 `aeb769cfd7ce0b69d374681187a245d9`) |
| Scenario binary | MD5 `54e444ed2ade8baf1c5fc3f54be5ad36` |
| Aqua-Sim-NG library | MD5 `871c50fc90cc613513ce25211cc8e450` |
| Run wrapper `analysis/runargs.sh` | MD5 `aee014733175e4b673a75a37dfd6db32` |
| Python | 3.10.12 |
| NumPy | 1.23.5 (the full file footprint is pinned by hash) |

## Steps

1. **Build** ns-3.41 with Aqua-Sim-NG and the project scenario. Confirm that the binary and library hashes match the table above.
2. **Simulate** seeds N = 41…50, once each:
   `runargs.sh <out>/run_N --run=N --routing=trustq --priorityScale=0 --attackerFraction=0.2 --dropProbability=0.75`
3. **Emulate** the O1 and B-PIPE opportunity tables from each run's own trace records (an offline step, once).
4. **Calibrate:** the frozen calibrations come from clean development seeds 12–21. They are inputs, not recomputed.
5. **Analyse** once with the frozen analysis adapter:
   - the label provider runs in an isolated process;
   - the precheck is recomputed and must equal the recorded reference before any calibration loads;
   - then scoring, the primary interval and verdict, and the secondary report.
6. **Verify** that the output directory holds exactly `result.json`, `statement.txt`, `secondary_report.json` and `MANIFEST.md5`, and that the manifest verifies (`md5sum -c MANIFEST.md5`).

## Notes

- **Re-running is not the same as reproducing these outputs.** Re-running from step 2 regenerates traces, so it is a replication with the same frozen code, not a reproduction of these outputs. It must use a new, empty output location.
- **What a public reader cannot run yet.** Until the team releases the confirmatory pipeline, steps 3–5 depend on code and calibration files that are not in the public repository:
  - the B-PIPE emulator;
  - the analysis adapter;
  - the B-PIPE calibration and threshold record.

  A public reader can rebuild the simulator, run step 2, and, once the output files are released, verify their hashes.
- **What is never published:** labels and ground truth. See the repository documentation for what is released and what is withheld.
- **Figures.** They are regenerated from the frozen values by the paper's figure script. It needs matplotlib; the authors ran 3.8.4 in an isolated folder.
