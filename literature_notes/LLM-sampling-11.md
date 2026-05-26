## Contrastive sampling
* The first paper uses the idea that small LM generates error tokens with higher probability compared to the large LM.
* It then contrasts the probability distribution of large LM from small LM by
	* $\text{argmax}_{\text{next token}} (\log p_{exp}(\text{next token}) - \log p_{ama}(\text{next token}))$
	* Where $p_{exp}$ is the large LM and $p_{ama}$ is the small LM
	* To avoid the case where both large and small LM makes correct prediction and makes the constrastive distribution small, the paper proposes to first truncate the probability distribution on the $p_{exp}$ so the implausible tokens are removed first. This is done by masking out all tokens with probability smaller than $\alpha \times \max p_{exp}(\text{next token})$
* The second paper further includes another hyperparameter that controls the difference between expert and amateur probabilities. $(1+\beta) \log p_{exp}(\text{next token}) - \beta \log p_{ama}(\text{next token})$
## Ref
Contrastive Decoding: Open-ended Text Generation as Optimization
CONTRASTIVE DECODING IMPROVES REASONING IN LARGE LANGUAGE MODELS