---
title: "Unique Factorization Domain - 1"
layout: post
use_math: true
tags: ["Modern Algebra1"]
---

### 서론
2020-2학기, 대학에서 '현대대수1' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr>

<span class="statement-title">Definition 1.</span> Unique Factorization Domain<br>

<div class="statement" markdown="1">

An **integral domain** in which every non-zero elt has a **<u>unique factorization</u>**; i.e. unique decomposition as the product of prime elements (or irreducible elements).

※ Note: In UFD, every irreducible element is a prime element.

</div>

- [MathWorld/Unique Factorization Domain](https://mathworld.wolfram.com/UniqueFactorizationDomain.html)

<br>

<span class="statement-title">Definition.</span> Associates<br>

<div class="statement" markdown="1">

$a$ and $b$ are associates when $a \mid b$ and $b \mid a$.

$a \mid b \implies b = ax$

$b \mid a \implies a = by$

$a = by = (ax)y = axy$

따라서 $xy = 1$

</div>

<span class="statement-title">Definition 2.</span> Unique Factorization Domain<br>

<div class="statement" markdown="1">

- Every $a \in D$ ,which is non-zero & not a unit, can be written as product of irreducibles.
- This decomposition is **unique up to reordering**, and **up to associates**.

Assume that two decomposition $a = p_1 \cdots p_n = q_1 \cdots q_m$ (all $p_i$, $q_i$ are irreducibles)

Then, $n=m$, and there exist a permutation $\sigma \in S_n$ s.t. $p_i = q_{\sigma(i)}$ are **associates** for all $i=1, ..., n$.

</div>

- [herzig's note](https://www.math.toronto.edu/~herzig/UFDs.pdf)