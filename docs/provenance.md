# Artifact provenance

## Authoritative outputs (single confirmatory run)

| File | MD5 |
|---|---|
| `result.json` | `cddc4d095206e8fb9ace0db35c62d1c6` |
| `statement.txt` | `31e4c05616e440876056c09239d419ce` |
| `secondary_report.json` | `12339dfe951338d6bb90a34b9503e803` |
| `MANIFEST.md5` (binds the three files above) | `e01e755c1bab5f3451ed395814fd61a4` |

## Frozen protocol

| Item | MD5 |
|---|---|
| Freeze v3 record (`PROTOCOL_FREEZE_RECORD.md`) | `42d019c0da7f948c0f1cd4ae4725ed4e` |
| Freeze v3 manifest (`FINAL_FREEZE_MANIFEST.md`) | `7f6451ca15522eb0dd310bc074de5493` |
| Freeze v3 list (175 hashed artefacts) | `5f88afc3496ae1225283192b7a98221c` |
| Analysis adapter v3.5 | `6683aa78c30042088a13cee2a8dc3dae` |
| Analysis configuration v6 | `72477fe2ad230b9104fa1ae1c8be304c` |

## Decision records (all frozen)

| Record | Content |
|---|---|
| D01 | ε, γ and the draw cap |
| D02 | analysis definition: estimand, δ, interval, verdicts, display |
| D03 | seed plan and its provenance limitation |
| D04 | operational choices |
| D05, D06, D06A | secondary reporting |
| D07 | output contract |
| D08 | residual risk R-1 and its operating rule |
| D09, D10 | one-use precheck checkpoints (attempt 1: stopped with a pipeline anomaly at the label provider; attempt 2: ESTIMABLE) |
| D11 | the single integrated run |

## Execution history (confirmatory)

1. **Freeze v1:** the protocol was frozen.
2. **Simulation:** completed for seeds 41–50.
3. **Emulation:** completed; the D08 operating rule was satisfied.
4. **Precheck attempt 1:** stopped as a pipeline anomaly before any label was read; a dependency could not be loaded.
5. **Fix and re-freeze:** a pinned-dependency fix was made, and the protocol re-frozen (freeze v2).
6. **Precheck attempt 2:** ESTIMABLE.
7. **Replay guard and re-freeze:** a precheck-reference guard was added, and the protocol re-frozen (freeze v3).
8. **Integrated run:** precheck replay matched, then scoring and evaluation. **Outcome V5.**

Each change was made as a new version under review. No frozen artefact was modified in place.

## Verification correction (recorded)

**Postflight v1:** the post-run verification script v1 compared the adapter's relative code-hash keys as absolute paths, so one check failed.

**Postflight v2:** v2 corrects only that path mapping and also re-hashes each file on disk. All of its checks passed.

**Scope:** the correction does not touch the run, its outputs or any evaluation rule.
