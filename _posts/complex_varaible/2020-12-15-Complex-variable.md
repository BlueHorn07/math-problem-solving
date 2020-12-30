---
title: "MATH210 - Applied Complex Variables"
layout: post
use_math: true
tags: ["Complex Variable"]
hidden: true
---

<br>

#### Complex functions

<div class="statement" markdown="1">

<span class="statement-title">Cauchy-Riemann Equation</span>

$f(z) = u(x, y) + i v(x, y)$ is **<u>analytic</u>** in a domain $D$<br>
iff the first partial derivatives of $u$ and $v$ satisfy

$$
\begin{aligned}
  u_x &= v_y \\
  u_y &= -v_x
\end{aligned}
$$

</div>

<div class="statement" markdown="1">



IF $f(z) = u(x, y) + i u(x, y)$ is **<u>analytic</u>** in a domain $D$, THEN both $u$ and $v$ are **<u>harmonic functions</u>**.

<span class="statement-title">Laplace's Equations and Harmonic functions</span>

A real valued function $H(x, y)$ is harmonic in a domain $D$, IF it satisfies Laplace equations:

$$
H_{xx} + H_{yy} = 0
$$

</div>

- Triangle inequality
- $n$-th root of $z$
- Complex Limit & Continuity & Derivative
- Analytic Functions
- Cauchy-Riemann Equation
  - Laplace's Equation & Harmonic functions
- Elementary complex functions
  - Exponential functions; $\exp z$
  - Trigonometric functions; $\cos z$, $\sin z$, $\tan z$
  - Hyperbolic functions; $\cosh z$, $\sinh z$
  - Logarithm; $\log z$
  - Power functions; $z^c$

#### Contour Integrals

<div class="statement" markdown="1">

<span class="statement-title">Cauchy-Goursat Theorem</span>

Let $f(z)$ be an **<u>analytic</u>** function in a domain $D$. THEN, 

$$
  \oint_{C} f(z) dz = 0
$$

for any simple closed curve $C$ whose interior is contained in $D$.

</div>

<div class="statement">

<span class="statement-title">Cauchy's Integral Formula</span>

$$
  f(z_0) = \frac{1}{2\pi i} \oint_{C} \frac{f(z)}{z-z_0} dz
$$

// 함숫값 $f(z_0)$를 적분을 통해 구할 수 있다는 의미를 가진다.

</div>

- Length of Curve; $\lvert C \rvert$
- primitive function
- Bounds for integrals: ML-inequality
- Cauchy-Goursat Theorem
  - Cauchy's proof (feat. Green's theorem)
  - Goursat's proof
- Cauchy’s Integral Formula
- Applications
  - Liouville’s Theroem

#### Power Series

<div class="statement" markdown="1">

<span class="statement-title">Talyor Series</span>

If $f(z)$ is **<u>analytic</u>** at $z_0$, and $f(z)$ is analytic through the disk $\lvert z-z_0 \rvert < R_0$.

THEN, $f(z)$ has a power series representation

$$
f(z) = \sum^{\infty}_{n=0} a_n (z-z_0)^n \quad (\lvert z-z_0 \rvert < R_0)
$$

where

$$
a_n = \frac{f^{(n)}(z_0)}{n!} = \frac{1}{2\pi i} \oint_{C} \frac{f(z)}{(z-z_0)^{n+1}} dz
$$

</div>

<div class="statement" markdown="1">

<span class="statement-title">Laurent Series</span>

Supp. that a function $f(z)$ is analytic throughout a domain $D$ containing an annular region $R_1 \le \lvert z-z_0 \rvert \le R_2$. THEN, $f(z)$ can be represented as the Laurnet series


$$
f(z) = \sum^{\infty}_{n=0} a_n (z-z_0)^n + \sum^{\infty}_{n=1} \frac{b_n}{(z-z_0)^n} \quad (R_1 \le \lvert z-z_0 \rvert < R_2)
$$

The coefficient of the Laurent series are given by

$$
a_n = \frac{1}{2\pi i} \oint_{C} \frac{f(w)}{(w-z_0)^{n+1}} dw \quad \textrm{and} \quad b_n = \frac{1}{2\pi i} \oint_{C} f(w)(w-z_0)^{n-1} dw
$$

</div>

- Convergence Tests
  - ratio test
  - root test
- Uniformly Convergent
  - $g_n(x) = x^n$ on $[0, 1]$ doesn't uniformly converge.

<div class="img-wrapper">
  <img src="https://solitaryroad.com/c453/ole5.gif">
</div>

- Talyor Series
- Laurent Series

#### Residue

<div class="img-wrapper">
  <img src="https://mathworld.wolfram.com/images/eps-gif/Contour_750.gif">
</div>

- [Residue Theorem]({{"2020/11/30/Residue-Thm.html" | relative_url}})
- [singular points & poles]({{"2020/11/30/singulars-poles.html" | relative_url}})
- [Formulas for residue]({{"2020/12/01/formulas-for-residue.html" | relative_url}})
- [Applications to real integrals]({{"2020/12/02/Applications-to-real-integrals.html" | relative_url}}); integral with $\cos$, $\sin$ / improper integral

#### Complex Transformation
- [Linear Transformation]({{"2020/12/14/Linear-Transformation.html" | relative_url}})
- [Linear Fractional Trnasformation]({{"2020/12/15/Linear-Fractional-Trenasformation.html" | relative_url}})
- Conformal mapping
  - $w = \sin z$
- Laplace's Equation