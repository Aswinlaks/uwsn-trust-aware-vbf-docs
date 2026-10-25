# Architecture

![Architecture: (1) simulation in ns-3.41 with Aqua-Sim-NG; (2) each node keeps only its own records; (3) an offline emulator turns each observer's records into opportunities; (4) pair scores and node rules; (5) the evaluator applies labels after scoring. Ground truth from the simulator goes only to the evaluator.](figures/architecture.svg)

## The five layers

| Layer | What happens | Main components |
|---|---|---|
| **1. Simulation** | 100 nodes run HH-VBF under a meandering-current mobility model; some nodes are selective-forwarding insiders. The channel has no ambient noise, so every lost packet is a collision. | ns-3.41, Aqua-Sim-NG, the project's `AquaSimTrustQVBF` routing module, scenario `scratch/uwsn-trustq-attack.cc` |
| **2. Node records** | Each node keeps only what it could know itself: headers it decoded, its own transmissions and its own position. | simulation trace files |
| **3. Passive observer** | An offline emulator turns each observer's records into *opportunities*: moments when a neighbour was expected to forward. Each opportunity ends as MATCH (forward heard), SILENT, or OTHER-UP (forwarded another copy; not scored). | opportunity emulator; O1 adds the VBF priority test and hold-time rank |
| **4. Scoring** | Each observer–neighbour pair gets a score; node rules combine the pairs that judge a node. | pair score r = (K − Σq)/n; node rules R0, R3, BETA, CA |
| **5. Evaluator** | Ground truth is applied only now, after scoring, to compute AUC, detection and false alarms with uncertainty intervals. | evaluator with network-cluster bootstrap and Holm correction |

## How a study is run

Each study follows the same fail-closed sequence:

```
freeze the plan, code and thresholds by hash
  → simulate the networks in the plan once (fresh seeds)
  → emulate every observer's opportunity tables once
  → check run integrity and configuration
  → run the evaluation exactly once
```

**Gates.** Any integrity, configuration or guard failure was defined in advance to stop a study before analysis. Study C additionally passed behaviour-identity and construct-validity gates before any test run.
