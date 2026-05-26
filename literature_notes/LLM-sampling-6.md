## Diverse sampling: priority Sampling
This sampling method aims to generate a set of unique samples with high probabilities. Like beam search, it keeps track of the top-k high probability of the possible solutions. In addition, it also uses the prefix saved in the branch that has not been used yet; so in the next search, it will generates tokens according to the saved prefix that is new.

## Ref
Priority Sampling of Large Language Models for Compilers