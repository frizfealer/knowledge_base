## Contrastive sampling
DOLA has several interesting ideas
* It uses the early exit predictions, that are the predictions from the early transformer layer. Because each transformer layer is combined with residual link, each transformer layer does not have dramatic changes compared to its predecessor.
* It uses the idea that lower-level information usually encoded in the early layer, while the topmost layer encodes knowledge. Based on this idea, it proposed a contrastive algo between the higher layer and lower layer.
* The algo is very similar to CD, except the amateur is replaced with the lower layer predictions.
* It uses validation set to select the a lower layer that has the maximum distance (here is Jenson-Shanon divergence).

## Ref
DOLA: DECODING BY CONTRASTING LAYERS IMPROVES FACTUALITY IN LARGE LANGUAGE MODELS