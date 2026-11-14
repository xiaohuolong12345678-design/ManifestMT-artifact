# ManifestMT Artifact

Companion artifact for the manuscript **"Are Equivalent Dependency Declarations Equivalent? Attributing Resolution Divergence in Python's Package Ecosystem"** (submitted to *Software: Practice and Experience*).

## Contents

`artifact.zip` contains:

- **`harness/`** — the ManifestMT end-to-end pipeline:
  - `harvest.py` — PyPI manifest harvester (corpus construction, URL-bearing/oversize exclusions)
  - `mrs.py` — six metamorphic-relation families with executable preconditions over a frozen index snapshot
  - `runner.py`, `resolvers.py`, `replay.py` — differential execution across resolvers (uv, pip-tools, Poetry, PDM), clean-environment replay classification
  - `impact.py` — E2 test-suite impact arm (perturbation environments, paired execution)
  - `drift.py` — E3 drift prober (synthetic null-future releases, four declaration policies)
  - `fetch_meta.py` — package metadata fetch utilities
- **`analyze.py`, `make_tables.py`** — analysis and table/figure generation; every number in the paper is produced programmatically from the raw result files, with assertions pinning the divergence set (e.g., the single E1 divergence case is asserted to be `pygoss`/MR5/uv).
- **`data/`**, **`out/`** — raw result files (JSONL) and generated summaries behind every table and figure (`rq1_e1a`, `e1b`, `e3`, Pareto figure).
- **`paper/tables/`, `paper/figs/`** — generated LaTeX tables and figures.

## Reproduction

1. Create a Python 3.13 virtualenv with the pinned resolvers (uv 0.12.7, pip-tools 7.6.1, Poetry 2.4.2, PDM 2.29.0; CPython 3.13.9) and a local PEP 503 index snapshot.
2. Run `runner.py` (E0/E1), `rerun_e1b.py` (replication), `impact.py` (E2), `drift.py` (E3).
3. Run `analyze.py` then `make_tables.py` to regenerate all tables, figures, and summary JSONs.

## Data availability

All raw results (JSONL), summary JSONs, and generated tables in this repository are the exact inputs from which every number in the manuscript is generated programmatically. The frozen index snapshot metadata are included.

## License

MIT (code). Data released under CC-BY 4.0.
