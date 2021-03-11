---
layout: post
title: GAMES-102 Lec6 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/subdivision.png
tags: [notes]
---

## NURBS & SubdivisionCurves & ImplicitCurves & SplineSurface

### 1. Rational Curve

**Problem**: 

Bezier curve can't express arc.

#### Rational Bezier Curve

$$
f^{hom}(t)=\sum_{i=0}^{n}B^{(d)}_i(t)\pmb{p}_i,\pmb{p}_i\in R^{n+1}
$$

$$
f^{(eucl)}(t)=\frac{\sum_{i=0}^nB^{(d)}_i(t)(p_i^{(1)}...p_i^{(n)})}{\sum_{i=0}^nB^{(d)}_i(t)p_i^{(n+1)}}
$$

$$
f^{(eucl)}(t)=\frac{\sum_{i=0}^nB^{(d)}_i(t)\omega_i\pmb{p}_i}{\sum_{i=0}^nB^{(d)}(t)\omega_i }
$$

The larger weight coefficient is, the less the distance between curve and point.

### 2. Subdivision Curve

Two Steps:

* Topology Rule: Adding new points, combining new polygon(splitting).
* Geometry Rule: Moving vertexes, Weighted average(averaging).

Two types:

* Approximating.
* Interpolation.

**Chaykin angle method:**

![Chaykin angle method](/assets/img/chaikin.png)

Necessary conditions of convergence:

* The max Eigenvalues is 1.

**Interpolation subdivision**

![4 points interpolation subdivision](/assets/img/4pointsinterpolation.png)
$$
\pmb{p}'_{2i+1}=\frac{\pmb{p}_i+\pmb{p}_{i+1}}{2}+\alpha(\frac{\pmb{p}_i+\pmb{p}_{i+1}}{2}-\frac{\pmb{p}_{i-1}+\pmb{p}_{i+2}}{2})
$$

### 3. Implicit Curve

**Implicit Function Theorem:**

* Given a differentiable function:
  $$
  f:R^n\supseteq D\rightarrow R,f(x^{(0)})=0,\frac{\vartheta}{\vartheta x_n}f(x^{(0)})=\frac{\vartheta}{\vartheta x_n}f(x_1^{(0)},...,x_n^{(0)})\neq 0
  $$

* Within an 𝜀‐neighborhood of $$x^{(0)}$$ we can represent the zero level set of 𝑓 completely as a heightfield function g:

  $$g:R^{n-1}\rightarrow R$$, such that for $$x-x^{(0)}<\varepsilon$$, we have: $$f(x_1,...,x_{n-1},g(x_1,...,x_{n-1}))=0$$ and $$f(x_1,...,x_n)\ne 0$$ everywhere else.

* The heightfield is a differentiable $$(n-1)$$ ‐manifold and its surface normal is the colinear to the gradient of f.

We know a closed curve, how to construct its expression?

* General case 
  * Non‐zero gradient at zero crossings
  *  Otherwise arbitrary 

* Signed implicit function: 
  * sign( 𝑓): negative inside and positive outside the object (or the other way round, but we assume this orientation here) 
* Signed distance field (SDF) 
  * |𝑓|= distance to the surface 
  * sign( 𝑓): negative inside, positive outside
* Squared distance function 
  * $$𝑓 = (distance to the surface)^2$$

**Draw of Implicit Curve**

Marching Cubes:

![Marching cubes](/assets/img/marchingcubes.png)

### 4. Spline Surface

**Tensor product surface**

![Tensor product surface](/assets/img/splinesurface.png)
$$
f(u,v)=\sum_{i=1}^n\sum_{j=1}^nb_i(u)b_j(v)\pmb{p}_{i,j}
$$
**Bezier Surface**

![Bezier Surface](/assets/img/beziersurface.png)
$$
f(u,v)=\sum_{i=0}^d\sum^d_{j=0}B_i^{(d)}(u)B_j^{(d)}(v)\pmb{p}_{i,j}
$$
