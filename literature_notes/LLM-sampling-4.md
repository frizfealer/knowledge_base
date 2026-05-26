## Min-p sampling
Setting a fixed threshold for probability cannot adapt to cases with different levels of uncertainty.
Min-p scales the probability by the maximum probability of the token so the probability threshold is dynamically set for each cases.
Step
1. Set $p_{max} = max_{v \in V} P(v|x_{1:t-1})$
2. $p_{scaled} = p_{base} \times p_{max}$
3. Let $p_{scaled}$ be the probability threshold for top-p sampling.
## Ref
Turning Up the Heat: Min-p Sampling for Creative and Coherent LLM Outputs