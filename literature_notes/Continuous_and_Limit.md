## Continuous function and limits of function
### limits
* For a function f, limit at a exist iff 
	1. $\lim_{x \to a-} f(x)$ exists
	2. $\lim_{x \to a^+ }f(x)$ exists
	3. $\lim_{x \to a^+ }f(x) = \lim_{x \to a-} f(x)$
* If limit at a exist for a function f, we can write $\lim_{x \to a} f(x) = c, c \in \mathbb{R}$
* Limit of combined function
	* $\lim_{x \to c} (f(x) + g(x)) = \lim_{x \to c} f(x) + \lim_{x \to c} g(x)$
	* $\lim_{x \to c} (f(x) - g(x)) = \lim_{x \to c} f(x) - \lim_{x \to c} g(x)$
	* $\lim_{x \to c} (f(x) g(x)) = \lim_{x \to c} f(x) \times \lim_{x \to c} g(x)$
	* $\lim_{x \to c} (\frac{f(x)}{g(x)}) = \frac{\lim_{x \to c} f(x)}{\lim_{x \to c} g(x)}$
	* $\lim_{x \to c} kf(x) = k \lim_{x \to c} f(x)$
* Limit of composite function
	* $\lim_{x \to c} f(h(x)) = f(\lim_{x \to c} h(x))$. 
	*  $lim_{x \to c} h(x)$ = L needs to be exist, 
	* and f continuous at L 
	* Even if we cannot apply the theorem, it does not mean the limit does not exist. We need to plug in the left and right limit of h to f to make sure if the limit exists.
* Finding limits
* ![[Pasted image 20240302101638.png]]
## Squeeze theorem
* Theorem useful in finding limits.
* If we want to find $\lim_{x \to c} f(x)$ and we know g(x) <= f(x) <= h(x) around c and $\lim_{x \to c} g(x) = \lim_{x \to c} h(x) = d$, then $\lim_{x \to c} f(x) = d$
* Using squeeze theorem, we can find $\lim_{x \to 0} \frac{sin(x)}{x} = 1$  

### Continuity
* Function f is continuous at c iff $\lim_{x \to c} f(x) = f(c)$
* Function f is continuous at interval $[a, b]$ iff it is continuous at interval $(a, b)$, such that
	1. $\lim_{x \to a^+ }f(x)$ = f(a)
	2. $\lim_{x \to b^- }f(x)$ = f(b)
	3. f(x) is continuous over (a, b)

## Intermediate value theorem 
* Theorem to check if existing a value in a continuous function.
* Given f(x) is continuous over interval $[a, b]$, where $f(a) = y_1, f(b) = y_2$, for any value $y_3$ between $y_1$ and $y_2$, there exists some c between  $[a, b]$  such that $f(c) = y_3$
## Reference
https://www.khanacademy.org/math/differential-calculus/dc-limits
