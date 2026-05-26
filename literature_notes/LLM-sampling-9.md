## Entropy sampling: Adaptive decoding
This paper introduces adaptive decoding, that adaptively controls the truncated set based on entropy
1. It computes confidence, which is the negative normalized entropy
2. In decoding, it has two sets: known and unknown set. At first all tokens are in the unknown set. 
3. Then it tries to include the token that has the largest probability into the known set, and computes the changes in confidence.
4. If the changes in confidence is large enough (a hyperparameter epsilon), then it includes the tokens to the set, and goes back to step 3. Else, it breaks
5. Sampling from this known set, like top-k sampling.

## Ref
Improving Open-Ended Text Generation via Adaptive Decoding
