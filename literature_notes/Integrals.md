## Definite Integral
1. $\int_a^b f(x)dx$ : the area under f(x) between x equals [a, b]
2. Riemann sum: using finite $\Delta x$  to approximate the area under f(x) between [a, b], where $\Delta x = \frac{b-a}{n}$
	1. Left Riemann sum: $\sum_{i=1}^{n} f(x_{i-1}) \Delta x$
	2. Right Riemann sum: $\sum_{i=1}^{n} f(x_{i}) \Delta x$
	3. Midpoint Riemann sum: $\sum_{i=1}^{n} f(x_{i-1} + \frac{\Delta x}{2}) \Delta x = \sum_{i=1}^{n} f(\frac{x_{i-1} + x_{i}}{2})\Delta x$
	4. Trapezoidal Riemann sum: $\sum_{i=1}^{n} \frac{f(x_{i-1})+f(x_{i})}{2} \Delta x$
3. Writing definite integral as Riemann sum $\int_a^b f(x)dx = \lim_{\Delta n \to \infty} \sum_{i=1}^{n} f(x_{i}) \Delta x$ (Can think $dx$ as an infinite small $\Delta x$)
4. 