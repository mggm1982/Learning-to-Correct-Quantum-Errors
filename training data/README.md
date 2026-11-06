# Data

All data are simulated with **Stim 1.16**: a rotated surface code, Z-basis memory experiment with d rounds, under circuit-level depolarizing noise of strength *p*. That noise acts after every gate, on idle data qubits each round, and on every measurement and reset. Base seed 42; `code/src/data.py` regenerates every file bit-for-bit. The test sets are in the sibling folder `testing data/`.

| Folder | Files | Shots | Noise *p* | Use |
|---|---|---|---|---|
| `train/` | `train_d3.npz`, `train_d5_part1.npz`, `train_d5_part2.npz` | 2,000,000 (d=3); 4,000,000 (d=5, in 2 parts) | mix of 0.2, 0.4, 0.6, 0.8, 1.0 % | training |
| `val/` | `val_d3.npz`, `val_d5.npz` | 100,000 each | same mix | picking the best epoch only |
| `../testing data/d3/`, `../testing data/d5/` | `test_d{d}_p{p}.npz` | 200,000 per file | 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.8, 1.0, 1.2 % | final results (different random seeds; 4 noise levels never seen in training) |
| `../testing data/ood_measurement_x5/` | `ood_d{d}_p{p}_measbias5.npz` | 200,000 per file | 0.4, 0.8 % with measurement/reset noise ×5 | robustness to unseen noise |
| `circuits/` | `circuit_d{d}_p0.005.stim` | — | — | the exact Stim circuit (change *p* to regenerate) |

**File format** (`.npz`):
- `det`: detection events, bit-packed along axis 1
- `obs`: 1 if the logical qubit flipped, else 0
- `n_det`: number of detectors (24 for d=3, 120 for d=5)
- `corr_mwpm_pred` (train/val only): the correlated-MWPM decision, used as an input by the hybrid decoder

```python
import numpy as np
z = np.load("../testing data/d5/test_d5_p0.006.npz")
det = np.unpackbits(z["det"], axis=1)[:, :int(z["n_det"])]   # (200000, 120) zeros/ones
obs = z["obs"]
```
`code/src/data.py` also provides `load_split(data_dir, "train", 5)`, which joins the two d=5 parts.

Real-hardware data are **not** redistributed here. They are Google's (Zenodo 10.5281/zenodo.6804040) and are downloaded by `code/src/hardware.py`.
License for this folder: CC BY 4.0.
