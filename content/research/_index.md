---
title: ""
date: 2024-07-29
type: "page"  # If using Hugo Academic's page type system
---

My research primarly focuses on optimal transport problems and their link with subfields of optimization, such as stochastic, online, and convex optimization. The goal is to design efficient algorithms with the best computational and statistical complexity.

## Preprints

#### - Fast and Large-Scale Unbalanced Optimal Transport via its Semi-Dual and Adaptive Gradient Methods
- **Authors:** F. Genans
- **Short abstract:** In Unbalanced Optimal Transport (UOT), we investigate the entropically regularized semi-dual objective. We prove the convergence rates of SGD and ASGD in both stochastic and semi-discrete settings. For the discrete case, we introduce a smoothness-adaptive Nesterov accelerated gradient descent scheme. We establish its global convergence rate and demonstrate an enhanced local convergence of $\mathcal{O}(\log(1/\delta)/\sqrt{\varepsilon})$ to achieve $\delta$-accuracy.
- **Link:** [PDF](./Preprint_AdaptiveGD_UOT.pdf)

  
#### - Geometry-Aware Optimal Transport: Fast Intrinsic Dimension and Wasserstein Distance Estimation
- **Authors:** F. Genans, O. Wintenberger
- **Short abstract:** We introduce a fast estimator for the one-sample Wasserstein discretization error that avoids the need for an OT solver. Building on this, we propose a resolution-dependent intrinsic dimension estimator for probability measures. Finally, we derive a new OT Richardson extrapolation estimator for the OT distance utilizing this intrinsic dimension.
- **Link:** [PDF](./Geometry_Aware_OT.pdf)

## Publications

#### - [NeurIPS 2025 - Spotlight] Stochastic Optimization in Semi-Discrete Optimal Transport: Convergence Analysis and Minimax Rate
- **Authors:** F. Genans, A. Godichon-Baggioni, F-X Vialard, O. Wintenberger
- **Short abstract:** We prove that Stochastic Gradient Descent can efficiently approximate the OT map in the semi-discrete setting, even in an online fashion, establishing the first minimax convergence guarantees for a broad class of cost functions and non-compact measures in this setting.
- **Link:** [PDF](./StoSDOT_Minimax_NeurIPS25.pdf)


#### - [NeurIPS 2025] Decreasing Entropic Regularization Averaged Gradient for Semi-Discrete Optimal Transport
- **Authors:** F. Genans, A. Godichon-Baggioni, F-X Vialard, O. Wintenberger
- **Short abstract:** We introduce DRAG, a stochastic algorithm for semi-discrete Optimal Transport that decreases entropic regularization during training. This yields unbiased estimates and faster convergence than fixed-regularization methods, with both theory and experiments confirming its efficiency.
- **Link:** [PDF](./DRAG_NeurIPS25.pdf)
  
