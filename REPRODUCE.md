# Reproducing the results

Two levels of reproduction are possible.

## Level 1: regenerate every number, table and figure from the logs (no GPU, ~5 min)

```bash
pip install -r requirements.txt
```

## Level 2: re-run the experiments

Open `notebooks/EPIC_HAR_framework.ipynb` in Google Colab (GPU runtime). Every session starts with
**Cells 1, 2, 2b, 3, 4, 5, 6**. Long runs are resumable: restart the runtime, run the same cells again, and they
skip what is already logged.

| Paper result | Cells to run | Settings | Time (one T4) |
|---|---|---|---|
| LODO vs LOSDO (Tables on protocol, LOSDO pairs, fairness, cost; Fig. LOSDO pairs) | 7b, then 8, 9, 11 | as in the notebook | ~1 h |
| Comparison with baselines, protocol gap, missing gyroscope, trust (Tables grid HHAR/LMDHG, stats, sensor, trust; Pareto and sensor figures) | 12, then 13, then 14 and 16 | `GRID_EPOCHS = None`, `GRID_MAX_FOLDS = None`, seeds 0–2; one protocol per session | ~35 h in total |
| Component study: feature-selection controls, effects, decomposition, hypothesis scorecard | 12, 13 (`RUN_GRID = False`), 19, then 20 | same settings as the grid; `FACT_PROTOCOLS` per session | LMDHG-seg ~1 h; P2W ~6 h; LOSDO ~8.5 h per seed |
| Component study on Kaggle (HHAR part) | `notebooks/EPIC_HAR_kaggle_factorial.ipynb` | Accelerator: GPU T4 x2; Internet on; Save & Run All | ~8 h, one background run |
| Export and exactness | 17 | | minutes |
| Override audit and its power | 9, 18 | | minutes |

The runs in the research used deterministic kernels (`cfg.deterministic = True`). Same-seed runs on a different GPU
model or library version may still differ; the research's component study reports how far its re-run of the grid
configuration differed from the grid (largest difference on one LOSDO fold).

## Rebuilding the notebooks from source

```bash
python src/build_notebook.py      # notebooks/EPIC_HAR_framework.ipynb from src/cells/*.py
python kaggle/build_kaggle.py     # notebooks/EPIC_HAR_kaggle_factorial.ipynb
```
