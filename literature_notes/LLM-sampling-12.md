## Contrastive sampling
* This paper proposes a CD sampling method - contrastive search 
* This algorithm includes two hyperparameters k (k in topk) and alpha, that argmax the following function
$$\text{argmax}_{v \in V^k}\{ (1-\alpha) \times p(v|x_{<t}) - \alpha \times (\max s(h_v, h_{x_j}): 1 \leq j \leq t - 1)) \}$$
* The first term is the probability of that token. The second term is the self-similarity term between the hidden state of token v and the previous generated token.
* This is based on the assumption that LLM is isotropy, that is evenly-distributed in the embedding space. If it is not the self-similarity term becomes large.
* An empirical study on contrastive search shows contrastive search is better than contrastive decoding.


## Ref
Contrastive Search Is What You Need For Neural Text Generation
An Empirical Study On Contrastive Search And Contrastive Decoding For Open-ended Text Generation