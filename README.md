# Holding Out the Person and the Device

Code, logged results and analysis scripts for the paper

> **Holding Out the Person and the Device: Budgeted Activity Recognition and a Factorial Study of What Each Component Contributes.**
> *Authors*.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24325989.svg)](https://doi.org/10.5281/zenodo.24325989)
<!-- replace XXXXXXX with the concept DOI after the first Zenodo release -->

EPIC-HAR is an activity recogniser for phones and wearables. It places the choice of input feature groups and of
network structure (heads, neurons, layers) under one FLOPs budget using Hard-Concrete gates, folds the gates into a
smaller network that computes the same function, trains for the worst-served subject and for missing sensors, and
releases predictions through a conformal decision layer with an audited human-review loop. The paper also
introduces the LOSDO protocol (leave one subject *and* one phone model out) and a 2^(5-1) factorial study of what
each component contributes.

## What is in this repository

| Folder | Contents |
|---|---|
| `notebooks/EPIC_HAR_framework.ipynb` | The complete framework: data loading, model, training, decision layer, baselines, experiment grid, statistics, component study. Runs on Google Colab. |
| `notebooks/EPIC_HAR_kaggle_factorial.ipynb` | The HHAR part of the component study on Kaggle's two T4 GPUs, no uploads needed. |
| `src/cells/` | The notebook's cells as plain Python files (easier to read and diff). `src/build_notebook.py` rebuilds the notebook from them. |
| `kaggle/` | Worker and launcher used by the Kaggle notebook, and the script that builds it. |
| `docs/` | Reproduction guide, dataset access, result-file schema. |


## Re-running the experiments

See [`docs/REPRODUCE.md`](docs/REPRODUCE.md) for which notebook cells produce which table and figure, the settings
used, and the expected run times. In short:

1. Open `notebooks/EPIC_HAR_framework.ipynb` in Google Colab with a GPU runtime.
2. Run Cells 1-6 (definitions) and 2b (data). HHAR is downloaded automatically; LMDHG must be obtained from its
   authors (see [`docs/DATA.md`](docs/DATA.md)).
3. Run the cells listed for the result you want. All long runs are resumable: they log each finished run and skip it when restarted.

The experiments used deterministic GPU kernels and seeds 0, 1 and 2. Same-seed runs on other GPU models or library
versions can still differ slightly; the paper reports the size of these differences.

## Datasets

The datasets are **not** redistributed here.

- **HHAR**: Stisen et al., UCI Machine Learning Repository, CC BY 4.0. Downloaded by the notebook.
- **LMDHG**: Boulahia et al. Request it from the dataset authors and place it as described in `docs/DATA.md`. Or downloaded from: https://www-shadoc.irisa.fr/english-leap-motion-dynamic-hand-gesture-lmdhg-database/.

## Citation

If you use this code or the LOSDO protocol, please cite the paper and the archived software (see `CITATION.cff`;
GitHub shows a "Cite this repository" button).

## Licence

Code: MIT (see `LICENSE`)`: CC BY 4.0.
