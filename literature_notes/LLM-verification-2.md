LLM semantic entropy
1. This paper proposes to use semantic entropy to determine if the LLM's confabulation.
2. Confabulation is the case where LLM generates incorrect or fabricated information that look reasonable and relevant , without any intent to deceive.
3. The semantic entropy is to compute entropy over semantic-similar clusters of sequence.
	1. First it makes LLM generates multiple answers.
	2. Then  it clusters the answers into semantic similar clusterings.
	3. Then it computes entropy over these clusterings, this is semantic entropy
	4. If the entropy is high, then the LLM is likely confabulate.

## Ref
Detecting hallucinations in large language models using semantic entropy