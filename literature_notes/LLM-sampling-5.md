## Entropy sampling: Mirostat
Mirostat sampling controls the target cross-entropy $\tau$, and learning rate $\mu$, so it adaptively changes the k in top-k sampling to be cross to target cross-entropy of the generated tokens. It has several assumptions.
1. It assumes the words follow Zipf's distribution
2. It assumes the natural language is a stochastic process that is stationary ergodic, ;therefore perplexity approximates the true cross entropy between the distance between the generated distribution and the true distribution. Note we don't have the true distribution in the test time.
## Ref
MIROSTAT: A NEURAL TEXT DECODING ALGORITHM THAT DIRECTLY CONTROLS PERPLEXITY