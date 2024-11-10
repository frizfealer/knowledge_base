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

## Properties of indefinite integrals
1. $\int x^n dx = \frac{x^{n+1}}{n+1} + C$, n != -1
2. $\int [f(x) + g(x)] dx = \int f(x)dx + \int g(x)dx$
3. $\int c f(x)dx = c \int f(x)dx$
## Indefinite integrals of common functions
1. $\int \frac{1}{x}dx = ln|x|$
2. $\int a^x dx = \frac{a^x}{ln(a)} + C$
3. Others: check derivatives
	1. $\int \frac{1}{\sqrt{a^2-x^2}}dx = arcsin(\frac{x}{a}) + C$
	2. $\int \frac{1}{a^2+x^2}dx = \frac{1}{a}arctan(\frac{x}{a}) + C$
## Integration with U-substitution 
If we let u = $x^2$, then
$\frac{d}{dx}[u] = \frac{d}{dx}[x^2]$
$\frac{du}{dx} = 2x$
$du = 2xdx$
1. u-substitution is about reversing the chain rule.
2. u-substitution helps us take a messy expression and simplify it by making the inner function the variable.
## integration using long division
1. $\int \frac{x-5}{-2x+2}dx = \int (-\frac{1}{2} + \frac{2}{x-1})dx$
2. $\int \frac{1}{5x^2 -30x +65} dx = \frac{1}{20} \int \frac{1}{(\frac{x-3}{2})^2 + 1}dx$. Let u = $\frac{1}{2}x - \frac{3}{2}$
## Integrating using trigonometric identities
1. If power is odd, we can separate one out and substitute the rest
	1. E.g. $\int cos^3(x)dx=\int cos^2(x)cos(x)dx = \int (1-sin^2(x))cos(x)dx$
2. If power is even, we can use the following formula to reduce the power
		1. $sin^2(x) = \frac{1}{2}(1-cos(2x))$
		2. $cos^2(x) = \frac{1}{2}(1 + cos(2x))$
		3. E.g.  $sin^4(x)$
## Trigonometric substitution
Pattern
1. $\sqrt{a^2-x^2}$ : let $x=asin\theta$. E.g. $\int \frac{1}{\sqrt{4-x^2}}dx$
2. $a^2 + x^2$: let $x=atan\theta$ E.g. $\frac{1}{36+x^2}dx$
3. $x^2 - a^2$: let $x=asec\theta$ E.g. $\frac{\sqrt{x^2 - 4}}{x}$
5. Refer to the arcsin, arctan equation under `Indefinite integrals of common functions`
## Integration by part
1. $\int f(x)g'(x) dx = f(x)g(x) - \int f'(x)g(x)dx$
2. example
	1. $\int x cos(x)dx = xsinx - \int 1 \times sin(x) dx$
	2. $\int ln(x)dx$
	3. $\int x^2 e^x dx$, $\int e^x cos(x) dx$ need to apply integration by part twice.
## Integration with partial fractions
1. $\int \frac{x-5}{(2x-3)(x-1)}dx = \int(\frac{-7}{2x-3} + \frac{4}{x-1})dx$

## Improper integral
1. $\int_{1}^{\infty} \frac{1}{x^2}dx = \lim_{n \to \infty} -\frac{1}{x} |^{n}_{1}$
2. $\int_{1}^{\infty} \frac{1}{x}dx = \lim_{n \to \infty} \ln|x| |^{n}_{1}$

