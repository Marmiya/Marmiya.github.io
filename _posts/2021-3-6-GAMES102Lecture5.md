---
layout: post
title: GAMES-102 Lec5 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/bezier.png
tags: [notes]
---

## Bezier Curve and B-spline Curve

### 1. Two Form of Modeling

* **Reconstruction**
  * Reserve Engineering: Shape already, "guess" it.
  * Sampling$$\rightarrow$$ Fitting: Function space should be abundant(enough express ability).
  * **Algebra view**: _{a,b,c}_ as the combination coefficient of basis function.

* **Design**
  * Free design: Born out of thin air or from a simple shape.
  * Interactive editing: Should have good geometric intuitiveness.
  * **Geometric view:** Basis function {$$t^2,t,1$$} as the combination coefficient of control points. 

### 2. Bernstein Basis Function

Bernstein basis function of degree n:
$$
B=\{B_o^{(n)},B^{(n)}_1,...,B^{(n)_n} \}
$$

$$
B_{i}^{(n)}(t)=\left( {\begin{array}{*{20}{c}}
n\\
1
\end{array}} \right)t^i(1-t)^{n-i}=B^{(degree)}_{i-th\  basis\ function}
$$
**Symmetry**: 
$$
B^{(n)}_i(t)=B^n_{n-i}(1-t)
$$
$$B^{(n)}_{i}(t)$$ reaches the maximum value when $$t=\frac{i}{n}$$.

**Characteristic** :

* Positivity, Convex hull

* Can express each other with power function base.

* Recurrence formula:
  $$
  B^n_i(t)=(1-t)B^{n-1}_i(t)+tB^{(n-1)}_{i-1}(1-t)
  $$

* End points interpolation

* Tangents of end points have same direction:
  $$
  f'(0)=3[P_{1}-P_o]
  \\
  f'(1)=3[P_{n-1}-P_n]
  $$

* 2-order tangent of end points is relative to 3 points:
  $$
  f''(0)=n(n-1)[P_2-2P_1+P_0]\\
  f''(1)=n(n-1)[P_n-2P_{n-1}+P_{n-2}]
  $$

**De Casteljau**

[De Casteljau algorithm](https://en.wikipedia.org/wiki/De_Casteljau%27s_algorithm)