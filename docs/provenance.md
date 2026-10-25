# Artifact provenance

Every reported number can be traced to a frozen output identified by its MD5 hash.

## Study A: authoritative outputs (single confirmatory run)

| File | MD5 |
|---|---|
| `result.json` | `cddc4d095206e8fb9ace0db35c62d1c6` |
| `statement.txt` | `31e4c05616e440876056c09239d419ce` |
| `secondary_report.json` | `12339dfe951338d6bb90a34b9503e803` |
| `MANIFEST.md5` (binds the three files above) | `e01e755c1bab5f3451ed395814fd61a4` |

| Frozen protocol item | MD5 |
|---|---|
| Freeze v3 record | `42d019c0da7f948c0f1cd4ae4725ed4e` |
| Freeze v3 list (175 hashed artefacts) | `5f88afc3496ae1225283192b7a98221c` |
| Analysis adapter v3.5 | `6683aa78c30042088a13cee2a8dc3dae` |

## Studies B and C: evaluation outputs

| Study | Item | MD5 |
|---|---|---|
| B | frozen plan | `14b3f0c48390e6ed74e9bc89d5a1d5ec` |
| B | evaluation results | `fb5381dab9af9b7468a79a3d713dd8bb` |
| C | frozen plan | `aa861eecf6751127bc566f32f1883d99` |
| C | recovery amendment record | `173b384450f0797e9878fc4ec71fc97d` |
| C | evaluation results | `1628174ea7e739d58c9a0d0787ab2f0d` |

## Execution history

**Study A**
1. Protocol frozen; simulation of seeds 41–50 and emulation completed.
2. First precheck stopped as a pipeline anomaly before any label was read (a dependency could not be loaded).
3. Dependency fixed and protocol re-frozen; second precheck: ESTIMABLE.
4. Replay guard added and protocol re-frozen (freeze v3).
5. Single integrated run: precheck replay matched, then scoring and evaluation; verdict V5.

**Study B**
1. Plan, models, thresholds and evaluator frozen; pre-run verification gate passed.
2. 210 simulations, all completed and configuration-checked; one evaluation.

**Study C**
1. Plan frozen; behaviour-identity, logging and construct-validity gates passed.
2. The batch was interrupted by accident after 140 of 160 runs, before any analysis.
3. Under a documented recovery amendment, the 20 missing runs were re-executed with their original commands; the interrupted partial outputs were confirmed to be exact prefixes of the re-runs.
4. All 160 runs checked; one evaluation.

No frozen artefact was modified in place; every change was made as a new, recorded version.
