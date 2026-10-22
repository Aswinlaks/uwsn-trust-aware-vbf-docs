# Code and repository

> **Status:** the public code repository does **not** exist yet. No code has been published, and no licence has been applied. Its URL will be added only once the team has made a release decision.

## What the code consists of

| Part | Content |
|---|---|
| Simulation scenario | `scratch/uwsn-trustq-attack.cc`: 100 nodes, HH-VBF, selective-forwarding insiders |
| Routing module | the project's `AquaSimTrustQVBF` routing in the Aqua-Sim-NG module for ns-3.41, used in HH-VBF mode |
| Passive observer | `observer.py`, `geom.py` and the clean calibration of O1 |
| Evaluator | the frozen evaluator: AUC and cluster bootstrap |
| Confirmatory pipeline | the O1 / B-PIPE opportunity emulator, the analysis adapter, the exact-rational evaluation and the secondary report. Developed outside the repository and frozen by hash (freeze v3) |
| Documentation | README, reproduction guide, dependencies, outputs, limitations and a public-release checklist (prepared, not yet published) |

## Release status

| Item | Status |
|---|---|
| Release scope (which frozen pipeline files are published) | **PENDING**: team decision |
| Licence | **HOLD**: the Aqua-Sim-NG upstream README states "All rights reserved", and some module files carry no licence notice. No licence is applied until the rights are resolved |
| Aqua-Sim-NG version used | the project's Aqua-Sim-NG library and scenario are identified by MD5 hash in [Reproducing the study](reproduction.md) |
| Environment-specific paths | some frozen files record local absolute paths. Published copies would be parameterised and labelled as derived copies of the frozen originals |
| Repository URL | **PENDING** |

## Never published

- ground truth and labels (simulator metadata listing malicious nodes, drop logs);
- raw simulation traces and the emulated opportunity tables;
- local machine paths and session material;
- the literature PDFs.

See [Reproducing the study](reproduction.md) for the steps that produced the confirmatory result, and [Artifact provenance](provenance.md) for how each artefact is identified by hash.
