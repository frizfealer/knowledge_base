### Derivative of f(x) at x = a
1. Informal definition: the slope of the tangent line to the function f(x) at the point x=a
2. formal defintion
	1. $f'(x)  = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$, $f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$
	2. $f'(a) = \lim_{ x \to a }\frac{f(x)-f(a)}{x-a}$

### Differentiability and Continuity
If a function is differentiable at x = a, then it is continuous at x = a <-> If a function is not continuous at x = a, then it is not differentiable at x = a

### Derivative rules
1.  $\frac{\partial}{\partial x} A = 0$
2. $\frac{\partial}{\partial x} Af(x) = A f'(x)$
3. $\frac{\partial}{\partial x} [f(x) + g(x)] = f'(x) + g'(x)$
4. Power rule: $f(x) = x^n, n \neq 0$.  $f'(x) = n x^{(n-1)}$
5. Product rule: $\frac{\partial}{\partial x} [f(x)g(x)] = f'(x)g(x) + f(x)g'(x)$
6. Quotient rule: $\frac{\partial}{\partial x} \frac{f(x)}{g(x)} = \frac{f'(x)g(x) - f(x)g'(x)}{g^2(x)}$
7. Chain rule: $\frac{\partial}{\partial x} f(g(x)) = f'(g(x))g'(x) = \frac{\partial f(g(x))}{\partial g(x)} \frac{\partial g(x)}{\partial x}$
8. Inverse function: $f(g(x)) = x$, then $g'(x) = \frac{1}{f'(g(x))}$
9. frequently-used derivatives:
	1. $\frac{\partial}{\partial x} e^x = e^x$
	2. $\frac{\partial}{\partial x} \ln x = \frac{1}{x}$
	3. $\frac{\partial}{\partial x} sin(x) = cos(x)$
	4. $\frac{\partial}{\partial x} cos(x) = -sin(x)$
	5. $\frac{\partial}{\partial x} tan(x) = sec^2(x)$
	6. $\frac{\partial}{\partial x} cot(x) = -csc^2(x)$
	7. $\frac{\partial}{\partial x} sec(x) = tan(x)sec(x)$
	8. $\frac{\partial}{\partial x} csc(x) = -cot(x)csc(x)$
	9. $\frac{\partial}{\partial x} a^x = a^x \ln a$
	10. $\frac{\partial}{\partial x}\log_{a}x = \frac{1}{(\ln a) x}$
	11. $\frac{\partial}{\partial x}sin^{-1}x = \frac{1}{\sqrt{1-x^2}}$
	12. $\frac{\partial}{\partial x}cos^{-1}x = -\frac{1}{\sqrt{1-x^2}}$
	13. $\frac{\partial}{\partial x}tan^{-1}x = \frac{1}{1+x^2}$

### L'Hôpital's rule

LHopital's rule is useful when there is a undetermined form of function when evaluating limits, e.g. $\frac{0}{0}, \frac{\infty}{\infty}$
It says, if the limit $\lim_{x \to c} \frac{u'(x)}{v'(x)}$ exists, then the two limits are equal:
$$\lim_{x \to c} \frac{u(x)}{v(x)} = \lim_{x \to c} \frac{u'(x)}{v'(x)}$$

### Reference
https://www.khanacademy.org/math/differential-calculus/dc-diff-intro
https://www.khanacademy.org/math/differential-calculus/dc-chain
