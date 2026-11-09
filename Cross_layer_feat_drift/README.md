# Test 1: Cross-Layer Feature Drift and Correspondence

## Objective

To investigate whether SAE features learned independently at different transformer layers exhibit consistent activation patterns across adjacent layers of Qwen2.5-3B Base, and whether those correspondences generalize to unseen examples.

## Experimental setup

- **Model:** Qwen2.5-3B Base
- **Transformer layers:** 36
- **SAE architecture:** Top-K sparse autoencoder
- **SAE input dimension:** 2,048
- **SAE latent dimension:** 8,192
- **Top-K:** 32
- **Evaluation dataset:** Controlled linguistic benchmark
- **Validation examples:** 1,536
- **Test examples:** 1,536
- **Candidate features:** 256 per layer
- **Adjacent-layer transitions:** 35
- **Feature matches:** 8,960
- **Permutation iterations:** 499

Feature candidates were selected using validation activations. Hungarian assignment was used to identify one-to-one feature matches between adjacent layers. The selected feature pairs were then evaluated on the held-out test split.

A block-permutation procedure preserved the four-condition structure of each contrast group and shuffled groups within adjective-valence, template, and feature-family strata where available. A global maximum-statistic correction was applied across all 8,960 matched pairs.

## Results

| Metric | Result |
|---|---:|
| Mean validation correlation | 0.4663 |
| Mean test correlation | 0.0892 |
| Median test correlation | 0.0000 |
| Validation–test Pearson correlation | 0.2393 |
| Globally significant feature pairs | 17 |
| Total matched pairs | 8,960 |
| Significant fraction | 0.19% |
| Global maximum-statistic permutation p-value | 0.002 |

The validation–test correlation of 0.2393 indicates weak positive consistency between the strengths of validation-selected matches and their test-set correlations.

Only 17 feature pairs remained significant after experiment-wide correction. These pairs exhibited exceptionally high test correlations, indicating that a small number of strong correspondences persist across the held-out examples.

## Layer-wise observations

The significant pairs were distributed unevenly across the network:

| Region | Transitions | Significant pairs |
|---|---:|---:|
| Early (1–10) | 10 | 11 |
| Middle (11–24) | 14 | 0 |
| Late (25–35) | 11 | 6 |

The middle region exhibited no globally significant feature matches. The late region showed a recovery in mean test correlation relative to the middle layers, while the early region contained the largest number of globally significant pairs.

## Interpretation

The results indicate that cross-layer feature correspondence is sparse and depth-dependent. Although some feature pairs exhibit exceptionally strong activation-profile correlations on unseen data, most validation-selected correspondences do not generalize strongly.

The findings do not establish that features retain semantic identity across layers. Correlation-based correspondence is not sufficient to establish causal feature transformation, splitting, merging, or progressive disentanglement.

SAE reconstruction quality also varies across layers, particularly in the later network. This limits how confidently depth-dependent correspondence patterns can be attributed to the underlying model rather than SAE approximation quality.

## Conclusion

Test 1 provides evidence of a small number of statistically robust cross-layer feature correspondences in Qwen2.5-3B Base. The overall correspondence is weak, with only 0.19% of candidate matches surviving experiment-wide correction.

The results motivate further investigation into feature selectivity and polysemanticity, which are examined separately in Test 2.