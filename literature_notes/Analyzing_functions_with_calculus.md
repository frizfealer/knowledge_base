## Extreme value theorem
* If a function is continuous over a close interval a and b, then there exist an absolute maximum value and an absolute minimum value over the interval.
* That is there exist numbers c and numbers d in $[a, b]$ such that: $$ f(c) \ge f(x) \ge f(d) , \forall x \in [a, b] $$
## Critical points
Candidates to maximum or minimum points. Criteria are:
* $f'(x) = 0$ or $f'(x)$ is undefined.
* $f(x)$ is defined.

## Finding global maximum for a function f 
* Compute critical points, $c_1, \dots, c_n$
* If we are looking for a closed interval [a, b]
	* Compute function values of $c_1, \dots, c_n, a, b$. And see which one is the largest.
* Else if we are looking for a function with open domain (a, b)
	* Compute sign of derivative between critical points, e.g

| Interval       | sign of f(x) |
| -------------- | ------------ |
| (a, $c_1$)     | -            |
| ($c_1$, $c_2$) | -            |
| ($c_2$, b)     | +            |
In this example, there is a global minimum at c2 and no maximum at b. If closed on b there exist a global maximum on b.

## Concavity
* Concave downward: slope is decreasing -> $f'(x)$ is decreasing -> $f''(x)$ < 0
* Concave upward: slope is increasing -> $f'(x)$ is increasing -> $f''(x)$ > 0
* Inflection point, candidate of concavity changes. Concretely, these are the condition.
	* $f''(x) = 0$ or $f''(x)$ is undefined.
	* $f''(x)$ switches sign around x (switching between different concavities).

Second derivate Test
1. $f'(x) = 0$
2. $f''(x) > 0$, local minimum. $f''(x) < 0$, local maximum