## Entropy sampling EDT

This paper proposed a method called entropy-based dynamic temperature sampling. This method is based on top-p (p=.95), and set temperature based on the entropy of next tokens, by
$T = T_0 * N^{\frac{\theta}{Entropy}}$. T_0 = 0.8, N = 0.7, and theta is a hyperparameter.
## Reference
EDT: Improving Large Language Models’ Generation by Entropy-based Dynamic Temperature Sampling