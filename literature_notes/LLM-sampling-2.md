## entropy sampling
* Real sampling proposes to use a external model to estimate the asymptotic entropy, that is the inherent entropy of a sentence given the model size. If the difference between the current entropy and predicted asymptotic entropy is high, the model is likely to hallucinate and we reduces threshold p in top-p sampling
* Model is trained to infer the entropy given context and model size. If model size becomes infinity, the entropy is defined as inherent entropy.
* Also the paper shows sampling is a trade-off between diversity and factuality [ref](Factuality enhanced language models for open-ended text generation.).
## Reference
REAL Sampling: Boosting Factuality and Diversity of Open-Ended Generation via Asymptotic Entropy
https://github.com/amazon-science/llm-asymptotic-decoding?tab=readme-ov-file
Factuality enhanced language models for open-ended text generation