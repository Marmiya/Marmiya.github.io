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

![Chaykin angle method](/assets/img/chaykin.png)

