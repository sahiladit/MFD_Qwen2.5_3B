# Mapping Feature Drift: Cross-Layer Correspondence and Polysemanticity in Qwen2.5-3B

This repository contains the implementation and experimental analysis for our research on feature representations in **Qwen2.5-3B** using Sparse Autoencoders (SAEs).

The study investigates how SAE features correspond across transformer layers and explores their activation behavior across different contexts.

## Experiments

The project is divided into two experiments:

- **Experiment 1 – Cross-Layer Feature Correspondence:** Studies feature relationships between neighboring transformer layers using activation correlations and statistical matching.
- **Experiment 2 – Feature Characterization and Polysemanticity:** Examines feature activation patterns, contextual diversity, clustering, and intervention behavior.

## Model Configuration

- **Base Model:** Qwen2.5-3B
- **Architecture:** 36 Transformer Layers
- **Residual Dimension:** 2048
- **SAE Latent Dimension:** 8192
- **Activation Selection:** Top-K (K = 32)

## Repository Structure

```text
MFD_Qwen2.5_3B/
├── Experiment_1/
├── Experiment_2/
└── README.md
```

## Research Paper

**Title:** Mapping Feature Drift: Cross-Layer Correspondence and Polysemanticity in Qwen2.5-3B

**Author:** Sahil Adit

## Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- Sparse Autoencoders
- Scikit-learn
- NumPy and Pandas