## entropy sampling
* This paper proposed a framework that the LM is a combination of natural language distribution and uniform distribution.
* Therefore, it believes we should only samples the tokens with probability that is relatively high, that is words with high probability should not be truncated, and when all words in the distribution have low probability, only words with low probability relative to the rest should be truncated.
* It selects the words with probability >= eta, where eta = min(epsilon, sqrt(epsilon)*exp(entropy of current token))
* It acknowledges that if we want the correct answer, the top-p will give more precise answer. Eta threshold usually returns a too large sets that can have false positive words.

## Ref
Truncation Sampling as Language Model Desmoothing