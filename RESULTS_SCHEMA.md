# Result files

All files are UTF-8. JSON Lines files hold one finished run per line.

## `results/grid/results.jsonl` (822 runs; notebook Cell 13)

Key: `protocol`, `model`, `seed`, `fold`. Protocols: `HHAR-P-LOSO`, `HHAR-P-LODO`, `HHAR-P-LOSDO`, `HHAR-P2W`,
`LMDHG-seg`, `LMDHG-cont`. Models: `EPIC`, `ViT`, `TCN`, `ResNet1D`, `TinyHAR`, `DeepConvLSTM`, `CoordMind`,
`HARNet5`, `BiLSTM`, `DDNet`, `AGCN`.

| Group | Fields |
|---|---|
| Accuracy | `acc`, `macro_f1`, `majority_baseline` |
| Calibration and conformal sets | `ece`, `temperature`, `coverage`, `target_coverage`, `avg_set`, `cov@a`, `set@a` for a in {0.05, 0.1, 0.2, 0.3} |
| Selective prediction | `answer_rate`, `selective_acc`, `aurc`, `ood_rate`, `answer@a`, `selacc@a` |
| Cost of the exported model | `params_dense/pruned`, `size_mb_dense/pruned`, `flops_dense/pruned`, `flops_ratio`, `cpu_ms_dense/pruned`, `export_max_abs_diff`, `size_mb_int8`, `cpu_ms_int8`, `int8_agreement`, GPU throughput and memory |
| Training | `train_s`, `s_per_epoch`, `peak_gpu_mb_train`, `peak_ram_mb`, `budget`, `wall_s` |

## `results/factorial/factorial.jsonl` (594 runs; Cell 19 and the Kaggle notebook)

Key: `protocol`, `config`, `seed`, `fold`. `config` is `FSDAC:` followed by the on (+) / off (-) state of feature
selection, structural sparsity, group DRO, adversarial invariance and view consistency, or one of the controls
`FS-none`, `FS-alone`, `FS-random`, `FS-filter`, `FS-alone-random`, `FS-alone-filter`. Additional fields:
`F,S,D,A,C` (+1/-1), `fs_method`, `k_target`, `k_ref`, `fixed_groups`, `groups_kept`, `n_groups_kept`, `n_groups`,
`sensors_needed`, `hard_cost_ratio`, `layers_on`, `heads_on`, `neurons_on`, and coverage of the same model under
class-conditional and marginal conformal sets (`cov_class`, `cov_marginal`, `worst_class_cov_*`, `set_*`).
Coverage: LMDHG-seg 3 seeds x 5 folds; HHAR-P-LOSDO seed 0 x 9 folds; HHAR-P2W 3 seeds x 1 fold; 22 configurations each.

## Other files

- `results/grid/wilcoxon_holm.csv`: paired tests of EPIC-HAR against each baseline (Cell 14).
- `results/grid/coverage_gap.csv`: coverage per held-out user, phone model and stream (Cell 16).
- `results/cell7b/<run>/`: per-fold results, summary and per-window predictions (gzip) of the EPIC-HAR runs on
  2.56 s windows (Cell 7b).
- `results/export/export_summary.csv`: ONNX / TorchScript export and exactness (Cell 17).
- `results/audit_power.csv`: detection power of the override audit (Cell 18).
- `results/benchmark/*.csv`: memory, speed and accuracy benchmarks (Cell 11).
