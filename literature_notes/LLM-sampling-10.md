## Evaluation
* This paper proposes a way to evaluate different truncating sampling methods, that is independent of LLM models
* It builds the prefix trees that can be used to compute Recall and Risk.
	* Recall, the number of truncated set divided by the number of the correct set 
	* Risk is the number of truncated set divided by the number of the correct set if it is larger than one.
	* We then can measures recall at a fixed level of risk.
	* The results shows adaptive decoding is the best in tradeoff. between risk and recall.
## Ref
Balancing Diversity and Risk in LLM Sampling: How to Select Your Method and Parameter for Open-Ended Text Generation