---
title: axis-aligned trees combine features only by stacking splits
---

**Date time:** 2026-06-14
## Contents
Decision and gradient-boosted trees split on one feature at a time with axis-aligned thresholds, so they cannot directly represent a relationship that spans features in one split — a difference $x_1-x_2$, a ratio, or an interaction. Approximating a diagonal boundary like "$x_1-x_2 > c$" forces the tree to stack many staircase splits, which is sample-inefficient and prone to overfitting:

```
boundary  x1 - x2 = c  is ONE diagonal cut (uses both features):

    x2
    ↑          ╱
    |   A    ╱
    |      ╱
    |    ╱     B
    +──────────→ x1

an axis-aligned tree has only horizontal / vertical cuts,
so it must STAIRCASE toward that line (never exact):

    x2
    ↑      __
    |  A  |
    |   __|
    | _|      B
    +──────────→ x1
```

Precomputing the combination as its own feature (e.g. the difference of two ordinals) hands the model a single axis to threshold, turning structure it otherwise cannot see into one split. The general move: engineer the cross-feature combinations — differences, ratios, interactions — that axis-aligned splits cannot recover on their own.

## References

## Related notes
[[[t4a]ordinal-encode a categorical only when its order is genuine]] — sibling: both follow from trees splitting only along the feature axes you supply; this card is about *combining* axes, t4a about *ordering* a single one
