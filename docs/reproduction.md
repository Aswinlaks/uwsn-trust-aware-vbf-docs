# Reproducing the study

> These steps describe how the results were produced. Running them again creates **new** outputs: it is a replication with the same frozen code, not a recreation of the recorded outputs, which are never overwritten.

## Environment

| Component | Version / identity |
|---|---|
| ns-3 | 3.41, with the project's version of the Aqua-Sim-NG module |
| Scenario | `scratch/uwsn-trustq-attack.cc` (MD5 `aeb769cfd7ce0b69d374681187a245d9`) |
| Scenario binary | MD5 `54e444ed2ade8baf1c5fc3f54be5ad36` |
| Aqua-Sim-NG library | MD5 `871c50fc90cc613513ce25211cc8e450` |
| Run wrapper `analysis/runargs.sh` | MD5 `aee014733175e4b673a75a37dfd6db32` |
| Python / NumPy | 3.10.12 / 1.23.5 |

## Steps

1. **Build** ns-3.41 with Aqua-Sim-NG and the project scenario, and check the hashes above.
2. **Simulate** each network in the plan once with the wrapper:
   `runargs.sh <out>/run_N --run=N --routing=trustq --priorityScale=0` plus the condition's options:

   | Condition | Extra options |
   |---|---|
   | S75 | `--attackerFraction=0.2 --dropProbability=0.75` |
   | S30 | `--attackerFraction=0.2 --dropProbability=0.3` |
   | ENV | S75 options plus `--ns3::AquaSimTrustQVBF::AttackMode=1` |
   | V06 | S75 options plus `--ns3::McmMobilityModel::VelocityScale=0.6` |
   | AF30 | `--attackerFraction=0.3 --dropProbability=0.75` |
   | CL03 / CL06 | none / `--ns3::McmMobilityModel::VelocityScale=0.6` |

3. **Emulate** each observer's opportunity tables from the run's own records (offline, once).
4. **Score** with the frozen thresholds (calibrated on clean seeds 12–21; inputs, not recomputed).
5. **Evaluate once** with the frozen evaluator of the study, and verify the output manifest (`md5sum -c`).

## Study-specific notes

- **Study A** (seeds 41–50, S75) used a staged pipeline: an isolated label provider, a precheck that had to match its recorded reference, then scoring and the verdict.
- **Study B** (seeds 211–240, all seven conditions) and **Study C** (seeds 241–280; CL03, S75, S30, ENV) each froze their plan, models, thresholds and evaluator code by hash before the simulations.
- **Study C** used a separate copy of the simulator with a logging-only patch that records undecodable arrivals; 13 validation re-runs confirmed that it leaves every other output byte-identical.
- **Never published:** labels and ground truth, raw traces and opportunity tables.
