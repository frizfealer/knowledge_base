## Definite Integral
1. $\int_a^b f(x)dx$ : the area under f(x) between x equals [a, b]
2. Riemann sum: using finite $\Delta x$  to approximate the area under f(x) between [a, b], where $\Delta x = \frac{b-a}{n}$
	1. Left Riemann sum: $\sum_{i=1}^{n} f(x_{i-1}) \Delta x$
	2. Right Riemann sum: $\sum_{i=1}^{n} f(x_{i}) \Delta x$
	3. Midpoint Riemann sum: $\sum_{i=1}^{n} f(x_{i-1} + \frac{\Delta x}{2}) \Delta x = \sum_{i=1}^{n} f(\frac{x_{i-1} + x_{i}}{2})\Delta x$
	4. Trapezoidal Riemann sum: $\sum_{i=1}^{n} \frac{f(x_{i-1})+f(x_{i})}{2} \Delta x$
3. Writing definite integral as Riemann sum $\int_a^b f(x)dx = \lim_{\Delta n \to \infty} \sum_{i=1}^{n} f(x_{i}) \Delta x$ (Can think $dx$ as an infinite small $\Delta x$)
## Fundamental Theory of Calculus
1. Given f(x) is continuous on [a, b]. Let $F(x) = \int_a^x f(t) dt$, where x in [a, b]. Then F is uniformly continuous on [a, b] and are differentiable on (a, b) and $F'(x) = f(x)$. We call F is an antiderivative of f.
	1. Every continuous f has an antiderivative F.
	2. Connection between derivatives and Integrals.
2. If f(x) is continuous on [a, b] and F(x) is any antiderivative of f(x) then, $\int_a^b f(x)dx = F(b) - F(a)$
3. $F(x) = \int_1^{sin(x)} (2t-1) dt$. What is $F'(x)$?
	 * Let $h(x) = \int_1^x (2t-1) dt, g(x) = sin(x)$, then $F(x) = h(g(x))$. $F'(x) = (2sin(x)-1)cos(x)$.

## Properties of definite integrals
1. if function f(x) is above x-axis, and a < b, then $\int_a^b f(x)dx$ is positive. If function f(x) is below x-axis and a<=b then $\int_a^b f(x)dx$ is negative.
2. $\int_c^c f(x)dx = 0$
3. $\int_a^b cf(x)dx = c \int_a^b f(x)dx$
4. $\int_a^b f(x)dx = - \int_b^a f(x)dx$
5. $\int_a^b (f(x) + g(x))dx = \int_a^b f(x) + \int_a^b g(x)$
6. Given a <= c <= b, $\int_a^b f(x)dx = \int_a^c f(x)dx + \int_c^b f(x)dx$
7. $F(x) = \int_x^{x^2} \frac{cost}{t} dt, F'(x)=?$
	1. $F(x) = \int_x^c \frac{cost}{t}dt + \int_c^{x^2}\frac{cost}{t}dt$
	2. $F'(x) = - \frac{cosx}{x} +\frac{cosx^2}{x} 2x$
