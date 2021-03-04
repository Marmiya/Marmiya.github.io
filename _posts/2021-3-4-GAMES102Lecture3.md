---
layout: post
title: GAMES-102 Lec3 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [notes]
---

## Parametric curve fitting

### 1. Tensor product basis function

* **Pros**： simple definition，kinds of product form of unary basis function

* **cons**： the number of basis function and variable. increase sharply as dimension growing

**New solution** : 

Neutral Network

​	Different affine transformations of a unary function(is called activation function) is used to construct "basis function", whose number of basis function is controllable.

### 2. Vector valued function

$$
f:R^1\rightarrow R^m  
$$

The vector valued function can be processed as multiple unary functions, among which every function is independent. 

**Geometry explanation**：

A real number $x$ $\in$ $R^1$ is mapped to a point in m-dimensions space, whose trackage constructs a curve in $R^m$.

Essential dimension is 1.

#### Some example:

* **flat(space) parametric curve**

flat(space) parametric curve can flexibly express non-functional curves

* **Parametric curved surface**

$$
f:R^2\rightarrow R^3
$$



**Geometry Explanation**：

A curved surface which can be determined by two parameters, namely _hyperparametric surface_

 Parametric curved surface can flexibly express ono-functional curved surface.



Dimensionality reduction mapping usually causes information loss, which is irreversible typically.

### 3. Parameterization of dot column 

* Equidistant(uniform) parameterization

$$
t_{i+1}-t_i=const
$$

* Chordal parameterization

$$
t_{i+1}-t_i = ||k_{i+1}-k_i||
$$

* centripetal parameterization

$$
t_{i+1}-t_i=\sqrt{||k_{i+1}-k_i||}
$$

### Supplement:

[Developable surface](https://en.wikipedia.org/wiki/Developable_surface)

 

