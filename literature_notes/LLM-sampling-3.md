## entropy sampling
Locally Typical Sampling samples the tokens that  have information content (-log2(prob)) that is close to the conditional entropy of the next token
Conditional entropy of the next token
$$ H(p(\cdot| y_{<t})) = -\sum_{y_t \in V}p(y_t | y_{<t}) log p(y_t | y_{<t})$$
Note the distance of token information content to the next token entropy is measuring how far away this token is from the mean entropy. This method put a upper bound how how far you can sample from.
## ref
Locally Typical Sampling