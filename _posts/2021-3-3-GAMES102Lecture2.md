---
layout: post
title: GAMES-102 Lec2 NOTES
subtitle: NOTES
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [notes]
---

## Data fitting

Finding fitting function is application-drive and domain-drive.  

### Methodology

* Where to find?
  * Determine the expression form of function (function set, space).
  * Let combination coefficient of basis function to be determined.

* Which one?
  * Fitting model(minimize problem).
  * Statistical model.

* How to find?
  * Resolve the stagnation point of loss function.
  * Transform to the equation set of coefficient .
    * If equation set is underdetermined, then revise the model.

### Polynomial interpolation

* [Vandermonde matrix](https://en.wikipedia.org/wiki/Vandermonde_matrix)
* [Lagrange interpolation](https://en.wikipedia.org/wiki/Lagrange_polynomial) and [Newton interpolation](https://en.wikipedia.org/wiki/Newton_polynomial#:~:text=In%20the%20mathematical%20field%20of,given%20set%20of%20data%20points.)

Flaws:

* System matrix dense.
* Depending on basis function, matrix may be ill-conditioned, which is difficult to solve.

[**System condition number**](https://en.wikipedia.org/wiki/Condition_number)

Vandermonde matrix's condition number grows exponentially as the number of data.

#### Solution:

Use orthogonal polynomial basis

How to get? [Gram-Schmidt Orthogonalization.](https://en.wikipedia.org/wiki/Gram%E2%80%93Schmidt_process)

### Polynomial approximation

Least squares approximation

### [Bernstein polynomial](https://en.wikipedia.org/wiki/Bernstein_polynomial)

#### why Bernstein is good?

* positivity, weighted
* Variation reduction
* Recursive linear solution method
* Subdivision

### RBF

Known as Gauss function in low level.