---
status: proposed
---
**Date time:** 2026-06-14T12:00

## Hypothesis
Two bonds are more usefully judged "similar" by how their prices/yields *move together* (return co-movement) than by how close their *levels* are. If this holds, a similarity model keyed on co-movement predicts a target bond's price more accurately than the current same-level model — because bonds that track each other carry mutual predictive signal that level-proximity alone misses.

## Current vs. proposed
- **Current:** the similarity model treats two bonds as similar when their price/yield **levels** are close. Similarity = proximity in level space.
- **Proposed:** treat two bonds as similar when their **movements** are correlated over time — co-movement of returns / yield changes. Similarity = correlation in change space.

## Test
- **Confirms:** on held-out bonds, a co-movement similarity metric produces lower price-prediction error (MAE/RMSE) than the same-level metric on the *same* prediction task, and the edge survives out-of-sample and across market regimes.
- **Refutes:** co-movement similarity matches or underperforms same-level on prediction error — or its apparent edge disappears once level is controlled for (i.e. co-movement adds nothing beyond what level already captures).
- **Discriminating evidence:** an ablation that isolates the two signals on one prediction task — *level-only* vs. *co-movement-only* vs. *both* — so you can tell whether co-movement adds incremental information or merely proxies level. A win for *both* over *level-only* is the load-bearing result.

## Status notes
- 2026-06-14: Proposed, untested. Salvaged from a 2024-01 scratch capture of the same-level-vs.-similar-moving idea (a fleeting note now retired). Restated here as a defensible bet rather than discarded as half-formed.

## Related notes
None yet — no permanent note in the slipbox or literature layer is a genuine conceptual neighbour. (The `t3*` bond cards concern portfolio allocation, a different domain from this pricing-model question; the originating fleeting note is transient and is not a valid link target.)
