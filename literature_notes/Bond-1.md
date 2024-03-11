## Modified Duration
## Contents
Modified duration is a measure of price sensitivity. It is the percentage derivative of price with respect to yield (YTM)

The formula is
$$ \text{ModD}(y) = -\frac{1}{V} \times \frac{\partial V}{\partial y} $$
Where y = YTM, V =  present value of all cash payments from the asset

#### The relationship to Macauley duration
$$ V(y_k) = \sum_{i=1}^n PV_i = \sum_{i=1}^n \frac{CF_i}{(1 + y_k/k)^{k*t_i}}$$
Taking the derivative of this ($\frac{\partial V(y_k)}{\partial y_k}$), we can find the relation to MacD as
$$ ModD = \frac{MacD}{1 + \frac{y_k}{k}}$$
Implication: 
1. The higher the MacD, the more price sensitivity
2. The higher the YTM, the less the price sensitivity
	1. This is because the higher income from a higher YTM can absorb some of the impacts of rate changes.
	2. When yields are higher, future cash flows are discounted more heavily, reducing their present value and, by extension, the bond's sensitivity to interest rate changes.
## Reference
https://en.wikipedia.org/wiki/Duration_(finance)

