# Architecture

## Simulation layer

- **Simulator:** ns-3.41 with Aqua-Sim Next Generation (Martin, Rajasekaran, Peng, WUWNet '17).
- **Scenario:** a project scenario (`scratch/uwsn-trustq-attack.cc`).
- **Routing:** the project's `AquaSimTrustQVBF` module in HH-VBF mode, with all trust influence on forwarding disabled for this study.
- **Attackers:** selective-forwarding insiders, 20 % of the non-sink nodes, dropping won packets with probability 0.75.

## Observation layer (offline, end of run)

Each node's own trace records are turned into **opportunity tables**, one per observer, by an offline emulator. Both methods share one pipeline:

```
observer O's own decoded headers + own transmissions + own position
   └─► forwarding events (U forwards packet (s,p) at t0)
         └─► candidates X: fresh (≤ 60 s), in range (≤ 1000 m), in pipe (≤ 400 m), heard by O
               ├─ O1 only:  Aqua-Sim VBF priority test (α ≤ 1.5) + hold-time rank strata
               └─ outcome:  MATCH / SILENT / OTHER-UP   (causal bound t ≤ t0 + 8 s)
   └─► per pair (seed, O, X): score r = (K − Σ q_stratum) / n ;  judged iff n ≥ 14
```

- **Expected clean silence rates** (`q`) are calibrated on clean development runs.
- **Labels** (honest / active dropper) are applied only by the evaluator, after scoring.

## Confirmatory execution pipeline (staged, fail-closed)

```
freeze (hashed protocol, code, dependencies)
  → simulation (seeds 41–50, once)
  → emulation of both observers' opportunity tables (once)
  → label-only precheck (P(undefined) vs ε)  — recorded as the reference
  → integrated run:
        emulation-integrity gate
        → label provider (isolated child process, pinned NumPy)
        → precheck replay  ==  recorded reference ?   ── no ──► PIPELINE ANOMALY (nothing scored)
        → calibration → scoring → primary interval + verdict → secondary report
```

**Gates.** Each stage needed its own approval reference in a versioned configuration. Any integrity or guard failure was predefined to stop the run without a research result.
