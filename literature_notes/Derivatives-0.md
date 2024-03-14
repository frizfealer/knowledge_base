### Derivative of f(x) at x = a
1. Informal definition: the slope of the tangent line to the function f(x) at the point x=a
2. formal defintion
	1. $f'(x)  = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$, $f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$
	2. $f'(a) = \lim_{ x \to a }\frac{f(x)-f(a)}{x-a}$

#### Differentiability and Continuity
If a function is differentiable at x = a, then it is continuous at x = a <-> If a function is not continuous at x = a, then it is not differentiable at x = a

#### Derivative rules
1.  $\frac{\partial}{\partial x} A = 0$
2. $\frac{\partial}{\partial x} Af(x) = A f'(x)$
3. $\frac{\partial}{\partial x} [f(x) + g(x)] = f'(x) + g'(x)$
4. Power rule: $f(x) = x^n, n \neq 0$.  $f'(x) = n x^{(n-1)}$
5. Product rule: $\frac{\partial}{\partial x} [f(x)g(x)] = f'(x)g(x) + f(x)g'(x)$
6. Quotient rule: $\frac{\partial}{\partial x} \frac{f(x)}{g(x)} = \frac{f'(x)g(x) - f(x)g'(x)}{g^2(x)}$
7. $\frac{\partial}{\partial x} e^x = e^x$
8. $\frac{\partial}{\partial x} \ln x = \frac{1}{x}$
9. $\frac{\partial}{\partial x} sin(x) = cos(x)$
10. $\frac{\partial}{\partial x} cos(x) = -sin(x)$
11. $\frac{\partial}{\partial x} tan(x) = sec^2(x)$
12. $\frac{\partial}{\partial x} cot(x) = -csc^2(x)$
13. $\frac{\partial}{\partial x} sec(x) = tan(x)sec(x)$
14. $\frac{\partial}{\partial x} csc(x) = -cot(x)csc(x)$