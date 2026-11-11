# Experiment 2: Feature Characterization and Polysemanticity Analysis

This experiment investigates the contextual behavior of features learned by Sparse Autoencoders (SAEs) trained on **Qwen2.5-3B**. It examines whether selected SAE features exhibit consistent activation patterns across different contexts and explores their potential semantic diversity through clustering and intervention-based analysis.

The experiment is part of the research project:

**Mapping Feature Drift: Cross-Layer Correspondence and Polysemanticity in Qwen2.5-3B**

---

## 1. Objective

The primary objectives of this experiment are:

- Characterize SAE features based on their activation patterns.
- Identify features exhibiting potentially diverse contextual responses.
- Examine contextual groupings using unsupervised clustering.
- Evaluate the consistency of candidate features across different text corpora.
- Investigate the behavioral effects of feature interventions.

The goal is to understand how individual SAE features respond to different linguistic and semantic contexts.

## 2. Experimental Setup

| Parameter | Configuration |
|---|---|
| Base model | Qwen2.5-3B |
| SAE architecture | Sparse Autoencoder |
| SAE latent dimension | 8192 |
| Activation selection | Top-K |
| Top-K value | 32 |
| Feature candidates examined | 576 |
| Contexts evaluated | 23,040 |
| Contexts after deduplication | 23,036 |

The analysis uses SAE activations extracted from the selected transformer layers of Qwen2.5-3B.

## 3. Feature Characterization

An initial screening process classified the examined features into three groups:

| Classification | Number of features |
|---|---:|
| Strong candidates | 10 |
| Provisional candidates | 69 |
| Unsupported candidates | 497 |
| **Total** | **576** |

These classifications represent different levels of evidence from the initial feature analysis. They should not be interpreted as definitive proof of monosemanticity or polysemanticity.

## 4. Contextual Analysis

Selected features were evaluated across a collection of text contexts to investigate their activation behavior.

The analysis examines whether features respond consistently to related contexts or exhibit activation across multiple contextual groups.

### Clustering Methodology

Contextual representations were analyzed using:

1. TF-IDF vectorization.
2. Dimensionality reduction using Singular Value Decomposition (SVD).
3. K-Means clustering.

This approach provides an exploratory view of contextual groupings based on textual features.

## 5. Cross-Corpus Validation

A separate validation experiment examined whether candidate features maintained similar behavior across two different text corpora:

- 500 WikiText articles.
- 500 C4 documents.

The validation compared 79 candidate features against 79 control features.

### Results

| Metric | Candidate features | Control features |
|---|---:|---:|
| Mean silhouette score | 0.05831 | 0.05852 |
| Mean stability | 0.87656 | 0.87087 |

No candidate feature demonstrated a validated cross-corpus replication under the experiment's evaluation criteria.

These results indicate that the observed contextual groupings did not establish a clear advantage for candidate features over controls.

## 6. Feature Intervention Analysis

Intervention experiments were conducted to investigate whether modifying selected feature activations influenced model output behavior.

The analysis included feature ablation and comparisons of output distributions.

### Observations

| Measurement | Candidate features | Control features |
|---|---:|---:|
| Mean Jensen-Shannon divergence | 3.19 × 10⁻⁵ | 5.19 × 10⁻⁶ |
| Top-1 output changes | 1/30 | 0/20 |

The intervention results are exploratory. Candidate and control interventions were not evaluated using a fully paired same-input design; therefore, these measurements should not be interpreted as definitive causal evidence.

## 7. Key Findings

The experiment provides several observations:

- A relatively small subset of the examined features emerged as strong or provisional candidates.
- Contextual clustering did not demonstrate a meaningful separation between candidate and control groups.
- Cross-corpus validation did not establish replicated candidate behavior.
- Feature interventions produced small output-distribution changes, with limited observed top-1 changes.

Overall, the results highlight the difficulty of establishing stable semantic interpretations for individual SAE features.

## 8. Limitations

The following limitations should be considered:

- Contextual clustering relies on TF-IDF, SVD, and K-Means rather than semantic embedding representations.
- Cross-corpus validation did not produce confirmed replications.
- Intervention comparisons were not fully paired across identical inputs.
- The observed activation patterns do not independently establish distinct semantic functions.
- Candidate classifications are exploratory and depend on the experimental evaluation criteria.

## 9. Reproducibility

The implementation, experimental scripts, and associated resources are maintained in this repository.

For reproducibility, use the same Qwen2.5-3B model configuration, SAE checkpoints, evaluation contexts, and analysis settings used in the original experiments.

Refer to the corresponding scripts and configuration files in this repository for implementation-specific execution instructions.