---
layout: post
title: GAMES-102 Lec3 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
tags: [notes]
---

## Cubic Spline Function

### 1. Mechanical interpretation

**Bernoulli-Euler equation**
$$
M(x)=EIk(x)=EI\frac{y''(x)}{(1+(y'(x))^2)^\frac{3}{2}}
$$
Among formula:

$$M(x)$$ : 	Bending moment

$$E$$: 			Elastic Modulus

$$I$$: 			 Geometric moment of inertia

$$k(x)$$: 	   Curvature

**Small disturbance hypothesis**:
$$
y'(x)\ll1(The\ bending\ angle\ is\ not\ greater\ than\ 45^{\operatorname{\omicron}})
$$

$$
M(x)=ax+b
$$

Therefore, the function $$y(x)$$ is a cubic function, in other word, the spline curve is a **piecewise cubic function.**

### 2. Solution ideas

$$
y_i(x)=a_i+b_ix+c_ix^2+d_ix^3
$$

We assume there are $$n + 1$$ points(that means n segments), hence there are $$4n$$ variables.

1. The curve must bypass points, therefore there is $$n+1$$ restrictions.
2. Assuming whole curve is $$C^2$$ continuous, so neighboring segments must meet three conditions: $$C^0$$ continuous, $$C^1$$ continuous and $$C^2$$ continuous, among which there are $$3n-3$$ restrictions.
3. Now we have $$4n-2$$ restrictions.
4. Adding two additional conditions, we can determine a curve.

_Boundary conditions:_

* Free end: specify the value of the second derivative of the curve at the two end points.
* Clamping end: specify the value of the first derivative of two end points.

**Three Bending Moment Equations**

* Tridiagonal matrix  
* The main diagonal is dominant
* There is a unique solution
* Catch-up method

_Simplified calculation skills:_

* Hermite interpolation polynomial
* Lid stone interpolation polynomial

**Limitations of spline functions**

* There must be small disturbances on holiday
* Can’t handle multi-value problems
* Cannot express the space curve well
* No coordinate invariance (geometric invariance)

### 3. Parametric continuity

**Geometric continuity**

$$G^0:$$ indicates two curve have common end points, as same as $$C^0$$.

$$G^1:$$ the tangent direction is continuous.

$$G^2:$$ the curvature is continuous.