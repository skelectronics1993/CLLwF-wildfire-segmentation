# CLLwF: Continual Learning without Forgetting for Multi-Domain Wildfire Image Segmentation

This repository contains the code accompanying the paper:

**"Continual Learning without Forgetting for Multi-Domain Wildfire Image Segmentation: A CLLwF Framework with Replay and Feature Distillation"**
Sujeet Kumar and Rajarshi Bhattacharya, Department of Electronics and Communication Engineering, National Institute of Technology Patna, India.
Submitted to *Journal of Applied Remote Sensing* (SPIE).

## Overview

CLLwF learns two heterogeneous wildfire segmentation domains sequentially without forgetting the first:
- **T1 — Boreal Forest Fire** (foreground: smoke plume)
- **T2 — FLAME** (foreground: flame front)

The method combines, on a shared ResNet-50 / FPN backbone with dynamically added per-task heads:
1. Learning without Forgetting (LwF) logit distillation,
2. intermediate feature distillation on the deepest encoder feature map, and
3. a compact experience-replay buffer.

## Repository contents

- `CLLwF_Wildfire_Colab.ipynb` — main training and evaluation notebook (Google Colab, GPU/T4). Resume-safe: checkpoints and results are cached to Google Drive so finished runs are skipped on re-run.

## Datasets (publicly available)

This work uses two public datasets; no new data were created:
- **Boreal Forest Fire** — Pesonen et al., *Scientific Data* (2025). [reference 8 in the paper]
- **FLAME** — Shamsoshoara et al., *Computer Networks* (2021). [reference 9 in the paper]

Please obtain the datasets from their original publications and place them in your Google Drive as described in the notebook's configuration cell.

## How to run

1. Open the notebook in Google Colab.
2. Mount Google Drive and set the dataset paths in the CONFIG cell.
3. Run the cells top to bottom. Checkpoints are written to `CLLwF_checkpoints/` and results to `CLLwF_results/` in your Drive.

## Reproducibility

Random seeds are fixed and cuDNN is set to deterministic mode. The architecture self-test in the notebook verifies the per-task head has 147,970 parameters and the fused decoder map has 128 channels, matching the paper.

## Citation

If you use this code, please cite the paper (citation details will be added upon publication).

## Contact

For questions, contact the corresponding author: Sujeet Kumar (sujeetk.phd24.ec@nitp.ac.in).
