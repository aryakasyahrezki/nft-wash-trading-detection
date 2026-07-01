# NFT Wash Trading Detection with Temporal Graph Networks

Code for the paper:  
**"Detecting NFT Wash Trading with Temporal Graph Networks: A Comparison of Class Imbalance Handling Strategies"**

Aryaka Syahrezki, Stephen Christopher, Andry Chowanda, Franz Adeta Junior  
Binus University, 2025

## Overview

This repository contains the experimental code for our paper. We model NFT
transactions as a continuous-time dynamic graph and compare five class imbalance
handling strategies within a memory-based Temporal Graph Network (TGN).

## Dataset

We use the publicly available Simiotic Ethereum NFT Dataset.  
Download from: https://www.kaggle.com/datasets/simiotic/ethereum-nfts  
See `data/README.md` for setup instructions.

## Notebooks

Run in order:
| Notebook | Description |
|----------|-------------|
| `01_preprocessing.ipynb` | Filter sales, remove burn addresses |
| `02_heuristic_labeling.ipynb` | Apply 4 wash trading heuristic rules |
| `03_feature_engineering.ipynb` | Compute temporal edge features |
| `04_graph_construction.ipynb` | Build graph and chronological split |
| `05_tgn_training.ipynb` | Train TGN with 5 imbalance strategies |

## Results

| Strategy               | ROC-AUC   | PR-AUC    | F1₀.₅     | F1\*      |
| ---------------------- | --------- | --------- | --------- | --------- |
| No handling (baseline) | **0.930** | **0.706** | 0.722     | **0.736** |
| Weighted BCE           | 0.913     | 0.606     | 0.407     | 0.680     |
| Class-Balanced         | 0.928     | 0.705     | **0.738** | 0.719     |
| Focal Loss             | 0.927     | 0.657     | 0.499     | 0.694     |
| Asymmetric Loss        | 0.922     | 0.688     | 0.725     | 0.731     |

Full results: `results/results.json`

## Experiments

`experiments/attention_tgn/` contains our probe of the full attention-based
TGN architecture. Results were lower (PR-AUC ~0.666) compared to the
memory-only baseline.

## Requirements

pip install -r requirements.txt

## Citation

If you use this code, please cite our paper:

@inproceedings{syahrezki2025nft,
title={Detecting NFT Wash Trading with Temporal Graph Networks:
A Comparison of Class Imbalance Handling Strategies},
author={Syahrezki, Aryaka and Christopher, Stephen and
Chowanda, Andry and Junior, Franz Adeta},
year={2025}
}
