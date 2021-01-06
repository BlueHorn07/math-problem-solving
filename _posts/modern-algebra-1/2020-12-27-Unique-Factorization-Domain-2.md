---
title: "Unique Factorization Domain - 2"
layout: post
use_math: true
tags: ["Modern Algebra1"]
---

### 서론
2020-2학기, 대학에서 '현대대수1' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

UFD의 첫번째 포스트는 [이곳]({{"2020/12/27/Unique-Factorization-Domain-1.html" | relative_url}})에서 볼 수 있습니다.

<hr>

이 포스트의 목표는 PID가 UFD임을 보이는 것이다.

그 전에 PID에서 만족하던 성질과 UFD에서 만족하던 성질을 나열해보자. 둘다 Irreduciblility와 Primality가 동치다.

<br>

<span class="statement-title">Properties.</span> PID<br>

- For a Field $F$,  Every $F[x]$ is PID.
- Irreducible element $\equiv$ Prime element

<br>

<span class="statement-title">Properties.</span> UFD<br>

- Irreducible element $\equiv$ Prime element

<br>
<hr>

본격적으로 증명을 하기 전에 아래의 명제를 먼저 증명하자.

<span class="statement-title">Proposition.</span><br>
<div class="statement" markdown="1">

$D$: Integral Domain

$\implies$ $D[x]$: Integral Domain

</div>

<span class="statement-title">proof.</span><br>
<details>
<div class="math-statement" markdown="1">

Integral Domain임을 보이기 위해 zero-divisor가 없음을 보여야 한다.

그래서 $f(x), g(x) \in D[x]$에 대해 $f(x)g(x) = 0$이라면, $f(x) = 0$ 또는 $g(x) = 0$임을 보여야 한다.

Let two non-zero polynomial $f(x), g(x) \in D[x]$.

$$
\begin{aligned}
  f(x) = \sum^{n}_{i=0} a_i x^i \quad (a_n \ne 0)\\
  g(x) = \sum^{m}_{i=0} b_i x^i \quad (b_m \ne 0)
\end{aligned}
$$

then, for $f(x)g(x)$, the cofficient of term $x^{n+m}$ is $a_n b_m \ne 0$.

Therefore $f(x)g(x)$ never be zero.

This means $D[x]$ is an Integral Domain. $\blacksquare$

</div>
</details>

<br>
<hr>

<span class="statement-title">Theorem.</span><br>

<div class="statement" markdown="1">

Every PID is UFD.

</div>

<br>
<hr>





<span class="statement-title">Theorem.</span> Fundamental Theorem of Arithmetic<br>





<br>

