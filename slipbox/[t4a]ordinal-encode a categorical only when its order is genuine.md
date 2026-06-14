---
title: ordinal-encode a categorical only when its order is genuine
---

**Date time:** 2026-06-14
## Contents
A tree splits a feature with a threshold on its axis, so encoding a categorical as an ordinal integer forces every split to respect that imposed order — a split can only peel off a prefix or suffix of the coded sequence. When the category is genuinely ordered (low/medium/high), this is a gift: the model captures the order with few splits and does not waste capacity rediscovering it. When the category is nominal, the imposed order is arbitrary and gets in the way; native categorical handling does better, because it orders categories at each split by their accumulated gradient/Hessian statistics (a data-driven order) rather than by an arbitrary code. So reach for ordinal encoding only when the order means something; otherwise let the model group the categories itself.

## References
- [XGBoost — Categorical Data](https://xgboost.readthedocs.io/en/stable/tutorials/categorical.html) — partition-based splits order categories by gradient statistics, the data-driven alternative to a fixed ordinal code
- [LightGBM — Features](https://lightgbm.readthedocs.io/en/latest/Features.html) — categories sorted per split by accumulated sum_gradient/sum_hessian; optimal-partition result from Fisher (1958)

## Related notes
[[[t4]axis-aligned trees combine features only by stacking splits]] — shares the root: both are consequences of axis-aligned splitting; t4 covers cross-feature combinations, this covers a single categorical's axis order
