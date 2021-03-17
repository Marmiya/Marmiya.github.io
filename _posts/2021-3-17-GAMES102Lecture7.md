---
layout: post
title: GAMES-102 Lec7 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/discretesurface.png
tags: [notes]
---

## Curve Fairing & Discrete Curves & Triangular Mesh

### 1. Curve Fairing

What is fairing curve?

![Curve fairing](/assets/img/curvefairing.png)

**Tangent vector** to curve $$C(t)=(x(t),y(t))$$ is

$$
T=C'(t)=\frac{dC(t)}{dt}=[x'(t),y'(t)]
$$

**Unit length tangent vector**

$$
\vec{T}=\vec{C}(t)=\frac{[x'(t),y'(t)]}{\sqrt{x'(t)^2+y'(t)^2}}
$$

**Curvature**
$$
k(t)=\frac{x'(t)y''(t)-y'(t)x''(t)}{(x'(t)^2+y'(t)^2)^\frac{3}{2}}
$$
Curvature is **independent** of parameterization.

#### 'New Definition' of Curve Fairing

A curve is fairing, if:

* It is $$C^{1+l}(l>0)$$ continuous.
* The number of turning points of itself is less.
* The number of turning points of its curvature is less.
* The amplitude of its curvature is less.

### 2. Discrete Curves

#### Different expression of curves

* Explicit function curve
* Implicit function curve (Level set)
* Parameterization curve
* Subdivision curve

#### Why discretion?

* For rendering
  * Rasterization of line and round.
* For computing
  * Solve the intersection of lines and the solution of polynomials.

* For manufacturing
  * The tool path only can follow straight lines and arcs.

#### Discretion of Curve: Sampling

**Nyquist-Shannon sampling theorem**

**Bezier Curve Discretion Theorem:**

* The distance between curve and chord is less than control points and chord.
* Given error, we can estimate the layer of discretion.

![Bezier Discretion][/assets/img/bezierdiscretion.png]

#### Computation of Discrete Curve

* If there is continuous expression, we can compute by that.
* If no continuous expression:
  * Difference method: use difference form to approximate differential properties.
  * Fitting method: use smooth function to fit properties.

* Tylor Expand

#### Coordinates of  barycentric

![](/assets/img/corofbc.png)

### 3. Triangular mesh

Meshes:

* Boundary edge: adjacent to exactly one face
* Regular edge: adjacent to exactly two faces
* Singular edge: adjacent to more than two faces

Closed mesh: mesh with no boundary edges

Manifold mesh: mesh with no singular edges
