[README.md](https://github.com/user-attachments/files/33484924/README.md)
# HyperGen: Learning Structure-Aware Spectral Flows for Hypergraph Generation

This repository contains the PyTorch implementation of *“HyperGen: Learning Structure-Aware Spectral Flows for Hypergraph Generation”*, a framework for hypergraph generation.

## Environment Requirements
Environment Requirements

Code is tested with Python 3.8 and CUDA 11.7. Key requirements:

python>=3.8
torch>=1.13.1
torch_geometric>=2.3.1
numpy>=1.24.4
scikit_learn>=1.3.2
networkx>=3.1
matplotlib>=3.7.5
tqdm>=4.67.1
scipy>=1.10.1
pandas>=2.0.3

Install dependencies with:
```bash
pip install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torch-geometric==2.3.1 \
torch-scatter==2.1.0 torch-sparse==0.6.16 torch-cluster==1.6.0 torch-spline-conv==1.2.2 \
numpy scipy scikit-learn networkx matplotlib pandas tqdm
```

## Dataset

- [Dataset](https://www.cs.cornell.edu/~arb/data/)

## Training Scripts
### 1. All experiments (training, generation, and evaluation) are conducted through a single entry script:
```bash
# Default run
python main.py
```

## Command Line Arguments
```
--config          Path to config.yml file (default: ./config.yml)
--dataset         Dataset name (overrides config.yml dataset field)

# =========================
# Training Hyperparameters
# =========================
--num_epochs      Number of training epochs (default: 400)
--lr              Learning rate (default: 1e-3)
--device          Device to use [cuda, cpu] (default: cuda if available)

# =========================
# Flow Matching Dynamics
# =========================
--n_steps         Number of integration steps in CFM (default: 20)
--dt              Time step size for Euler integration (default: 0.05)
--noise_scale     Stochastic noise scale in diffusion process (default: 0.2)
--sigma_base      Base noise for interpolation between Z0 and Z1 (default: 0.2)

# =========================
# Spectral Encoding / Decoding
# Spectral Encoding / Decoding
# =========================
--k_low           Number of low-frequency eigencomponents (default: 16)
--k_high          Number of high-frequency eigencomponents (default: 16)

# =========================
# Peierls Phase Model
# =========================
--phi_mode        Phase type [learnable, random, peierls_structured] (default: learnable)
--phi_scale       Magnitude of Peierls phase (default: 0.1)

# =========================
# Loss Weights
# =========================
--lambda_amp      Weight for edge amplitude reconstruction loss (default: 1.0)

# =========================
# Reproducibility
# =========================
--seed            Random seed (default: 42)
```

