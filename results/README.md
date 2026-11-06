# Results

## tables/
| File | Contents |
|---|---|
| `results_test.csv` | Logical error rate per (d, p): MWPM, correlated MWPM, 3 CNN seeds (plus mean and std), CNN ensemble, hybrid, and decoder speed |
| `mcnemar.csv` | Paired McNemar tests on identical shots: CNN ensemble or hybrid vs MWPM or correlated MWPM |
| `results_ood.csv` | Out-of-distribution test (measurement/reset noise ×5) |
| `results_hardware.csv` | Google Sycamore, per patch and fold: our decoders, matching, and Google's published decoders |
| `v1_ablation_results_test.csv` | Preliminary run, including the MLP ablation (same test data) |
| `ensemble_d5_p0.006_probs.npz` | CNN-ensemble probabilities and labels, used for the ROC, calibration and post-selection figure |
| `run_info.json` | Runtime, hardware, seeds and parameter counts |

## figures/ (PDF and PNG)
| File | Shows |
|---|---|
| `ler_vs_p` | Error rate vs physical noise |
| `vs_corr` | Gain over correlated MWPM |
| `threshold` | Error suppression with code size, incl. the MLP ablation |
| `hardware` | Results on real Sycamore data |
| `classifier` | ROC, calibration and post-selection |
| `ood` | Unseen-noise test |
| `syndrome` | One example input |

## Model weights
The trained weights are not included in this folder, to keep it small. Running `code/src/train.py` regenerates them into `results/model_weights/`, and they are available from the authors on request.

## Key numbers
- **Simulation:** the CNN ensemble beats correlated MWPM at all 18 settings (6–46 % fewer errors). All 36 paired tests give p < 0.03.
- **Hardware:**

| Decoder | Error rate |
|---|---|
| MWPM | 15.06 % |
| Correlated MWPM | 13.57 % |
| **CNN (ours)** | **13.03 %**, better on all 8 folds |
| Google belief matching | 12.88 % |
| Google tensor network | 12.45 % |
