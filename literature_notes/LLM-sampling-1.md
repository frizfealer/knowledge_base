# Sampling of LLM
* Nucleus sampling is a popular method that samples the smallest set of tokens with a cumulative probability threshold ppp, ensuring $\sum_{x \in V^{(p)}} P(x|x_{1:i-1}) \geq p$ V^(p) is the smallest token set. This approach better mirrors natural human language, which doesn’t always select the highest-probability tokens.
- Unlike beam search or argmax, which yield low perplexity but can produce repetitive and less diverse results, nucleus sampling introduces variability.
- Nucleus sampling also improves on top-k sampling, where the optimal kkk value varies based on entropy. Typically paired with temperature scaling (e.g., lower temperatures for lower entropy), top-k involves a trade-off that can reduce diversity.
## Reference
THE CURIOUS CASE OF NEURAL TEXT DeGENERATION
   