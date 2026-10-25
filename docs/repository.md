# Code and repository

**Repository:** [github.com/chethana100/uwsn](https://github.com/chethana100/uwsn)

The repository contains the simulation platform (ns-3.41 with the Aqua-Sim-NG module) and the project's analysis code.

## What the repository contains

| Path | Content |
|---|---|
| `scratch/uwsn-trustq-attack.cc` | the project scenario: 100 nodes, HH-VBF routing, selective-forwarding insiders, meandering-current mobility |
| `src/aqua-sim-ng/` | the Aqua-Sim-NG module (git submodule), including the project's `AquaSimTrustQVBF` routing used in HH-VBF mode |
| `analysis/runargs.sh` | the wrapper used to run every simulation |
| `analysis/stageE/e1/` | the passive observer (`observer.py`, `geom.py`) |
| `analysis/studies/` | the analysis code of Studies A, B and C, copied exactly as run, with a list of the hashes of the frozen originals |
| `project/` | installation guide, reproduction steps, methodology, architecture, results and limitations |

## How to use it

1. Follow `project/INSTALL.md` to clone the repository with its submodule and build ns-3.41.
2. Run any network of any condition with the commands in `project/REPRODUCING.md` (also on [Reproducing the study](reproduction.md)).
3. Read `analysis/studies/README.md` to see which script produced which result.

## Licence

ns-3 is distributed under the GNU General Public License version 2 (`LICENSE` in the repository). The Aqua-Sim-NG module keeps its own upstream terms.

## Not published

- ground truth and labels (insider lists, drop logs);
- raw simulation traces and opportunity tables;
- the research paper and the literature PDFs.

See [Artifact provenance](provenance.md) for how each output is identified by hash.
