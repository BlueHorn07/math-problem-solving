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

이 포스트의 목표는 <big>"Every PID is UFD."</big>를 보이는 것이다.

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

본격적으로 증명을 하기 전에 몇가지 명제를 먼저 증명하자. 명제를 증명하기 위해 필요한 바탕이 꽤 많으니 집중해서 한다.

<br>

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

<span class="statement-title">Theorem 23.20</span><br>

<div class="statement" markdown="1">

If $F$ is a Field,

then every non-constant polynomial $f(x) \in F[x]$ can be factored into a **<u>product of irreducible poylnomials</u>**.

This factorization is unique up to orerding and associates.

</div>

<span class="statement-title">proof</span><br>
<details>
<div class="math-statement" markdown="1">

Let $f(x) \in F[x]$ be a non-constant polyno-.

If $f(x)$ is 'not' irreducible, then $f(x) = g(x)h(x)$ for some lower degress polynomials.

If $g(x)$ and $h(x)$ are irreducible, we stop here.

If not, at least one of them factors into lower degress polno-s.

Continuing this process, then we get 

$$
f(x) = p_1 (x) p_2 (x) \cdots p_r (x)
$$

<br>

(Uniqueness) 

Supp. $f(x) = p_1 (x) \cdots p_r (x) = q_1 (x) \cdots q_s (x)$.

$p_1(x)$는 $f(x)$를 divide 하므로 식의 우변을 divide한다. 따라서 $p_1 (x)$는 적어도 하나의 $q_i (x)$를 divide한다. 


<div class="statement" markdown="1">

사실 위의 사실은 irreducibility의 정의를 확장한 것이다. 

irreducible polyno- $f(x)$에 대해 $f(x) \mid r(x) s(x)$라면, $f(x) \mid r(x)$ 또는 $f(x) \mid s(x)$이다.

이것을 두 개 polyno-의 product가 아니라 $s$개 polyno-의 product로 확장시켜 적용한 것이 위의 명제다.

</div>

$p_1 (x) \mid q_i (x)$가 성립한다고 가정하자. 이때, $q_i (x)$가 irreducible polynomial이기 때문에 $p_1 (x) = u_1 q_i (x)$이다. (for some unit $0 \ne u_1 \in F[x]$)

이때, Polynomial Field에서는 곱에 대한 교환법칙이 성립하므로 논의의 편의를 위해 $q_i (x)$를 $q_1 (x)$로 두자. $p_1 (x) = u_1 q_1 (x)$

이제 factorization $p_1 (x) \cdots p_r (x) = q_1 (x) \cdots q_s (x)$에 위의 관계식을 적용하고 소거하자. 그러면

$$
\begin{aligned}
  p_1 (x) \cdots p_r (x) &= q_1 (x) \cdots q_s (x)$ \\
  (u_1 q_1 (x)) \cdots p_r (x) &= q_1 (x) \cdots q_s (x) \\
  u_1 \cdots p_r(x) &= 1 \cdots q_s (x)
\end{aligned}
$$

(논의의 편의상 $r < s$라고 가정하자. 반대로 잡아도 상관은 없다.)

이 과정을 반복하면,

$u_1 \cdots u_r = 1 \cdots q_{r+1} (x) \cdots q_s (x)$가 된다.

이때에 위의 식이 성립하기 위해선 우변의 polyno- 부분이 없어야 하므로 $r = s$가 되어야 한다.

따라서 irreducible polyno- $f(x)$의 factorization은 ordering과 associates에 대해 unique 하게 존재한다. $\blacksquare$

</div>
</details>

<br>
<hr>

#### Ascending Chain Condition (ACC)

이번에는 **집합론**에서도 등장하는 명제를 다룬다. 생각보다 중요한 명제다.

<span class="statement-title">Lemma 45.9</span><br>
<div class="statement" markdown="1">

$R$: commutative ring + unity.

Let $N_1 \subseteq N_2 \subseteq \cdots $ be an ascending chain of ideals $N_i$ in $R$.

Then, $N = \cup_i N_i$ is an Ideal in $R$.

</div>

<span class="statement-title">proof.</span><br>
<details>
<div class="math-statement" markdown="1">

Let $a, b \in N$. 

Then, there are ideals $N_i$ and $N_j$ in ideal chain, with $a \in N_i$ and $b \in N_j$.

Now either $N_i \subseteq N_j$ or $N_i \supseteq N_j$.

Let's assume $N_i \subseteq N_j$, so both $a$ and $b$ are in $N_j$.

This implies $a \pm b$ and $ab$ are also in $N_j$, and also be in $N$.

Take $a = 0$, then $0 \in N$, and $b \in N$ implies $-b \in N$.

Thus $N$ be a sub-ring of $R$.

<br>

"Check $N$ is an ideal."

For $a \in N$, $r \in R$, we must have $a \in N_i$ for some $N_i$.

Since $N_i$ is an ideal, $ar = ra \in N_i$, and also in $\cup_i N_i = N$.

Therefore, $N$ is an Ideal. $\blacksquare$

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

