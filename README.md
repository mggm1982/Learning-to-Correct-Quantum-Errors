# CWS Project: Learning to Correct Quantum Errors

**Shreeyam Bangera**, Department of Physics, IIT Roorkee.

A compact 3D convolutional neural network decodes the error alarms (syndromes) of the surface code. It beats correlated minimum-weight perfect matching on simulated data at all 18 test settings, and on real Google Sycamore hardware data on all 8 test folds.

| Item | Where |
| :---- | :---- |
| Code and associated libraries | `code.zip`: Python scripts, notebooks, `requirements.txt`, README |
| Training data | `training data/` (train \+ validation splits, circuits, manifest) |
| Testing data | `testing data/` (d3, d5 and out-of-distribution test sets) |
| Presentation (.pptx), VideoPPT (.mp4) and video script | `presentation/` |
| Preprint-ready article | `preprint/` (PDF \+ LaTeX source) |
| Results (tables and figures) | `results/` |
| Declaration of consent | `Declaration_Shreeyam_Bangera.pdf` |

## Headline numbers

- **Simulation:** 6–46 % fewer logical errors than correlated MWPM at all 18 settings (paired McNemar p \< 0.03).  
- **Real hardware:** 13.03 % logical error rate vs 13.57 % for correlated MWPM, better on all 8 folds.

Reproduce: unzip `code.zip` here, `pip install -r code/requirements.txt`, then `cd code/src && python run_all.py`. This takes about 50 min on 2× T4 GPUs.