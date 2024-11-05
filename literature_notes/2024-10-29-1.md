# LLM verifier
1. One way to train LLM verifier directly assigns a numerical score to estimate a solution y is correct for a problem x.
	1. Using binary cross-entropy loss and make the positive and negative classes balanced.
2. The paper proposed a direct verifier. Let LLM train on samples (x, $y_+$, I, 'Yes') for positive samples and (x, $y_-$, I, 'No') for negative samples. Where I = = ‘Is the answer correct (Yes/No)?’ This samples are called $D_{verify}$
	1. The paper further propose to train the verification with generation together, e.g. $Loss = L_{sft}(\theta, D_{verify}) + \lambda L_{sft}(\theta, D_{correct})$
	2. $L_{sft}$ means supervised fine-tune loss
	3. $D_{verify}$ means data set with verification dataset as stated above and $D_{correct}$ means only the correct answer (x, $y_+$)

## Reference
Generative Verifiers: Reward Modeling as Next-Token Prediction