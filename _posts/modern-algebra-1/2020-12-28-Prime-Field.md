---
title: "Prime Field"
layout: post
use_math: true
tags: ["Modern Algebra1"]
---

### 서론
2020-2학기, 대학에서 '현대대수1' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr>

<span class="statement-title">Theorem.</span><br>

<div class="statement" markdown="1">

$R$: Ring + unity

$$
\begin{aligned}
    \phi: \mathbb{Z} &\longrightarrow R \\
            n &\longmapsto n \cdot 1 = 1 + \cdots + 1
\end{aligned}
$$

then, $\phi$ is ring homomoprhism.

</div>

<br>

<span class="statement-title">Corollary.</span><br>

<div class="statement" markdown="1">

$R$: Ring + unity

$\textrm{Char}(R) = n > 1$

1\. $R$ contains sub-ring $H$ s.t. $H \cong \mathbb{Z}_n$

2\. If $\textrm{Char}(R) = 0$, then $R$ contains sub-ring $H$ s.t. $H \cong \mathbb{Z}$.

</div>

<br>

<span class="statement-title">Theorem.</span><br>

<div class="statement" markdown="1">

Let $F$ be a Field.

Then, $\textrm{Char}(F) = p$ or $\textrm{Char}(F) = 0$.

So, 

1\. $\textrm{Char}(F) = p$ $\implies$ $\mathbb{Z}_p \cong H \le F$.

2\. $\textrm{Char}(F) = 0$ $\implies$ $\mathbb{Q} \cong H \le F$.

$\mathbb{Z}_p$와 $\mathbb{Q}$ 모두 Field다!!

즉, Field의 $\textrm{Char}(F)$를 통해 내부에 어떤 **sub-field**을 가지고 있는 대략적으로 확인할 수 있다는 말이다!

</div>

<br>

<span class="statement-title">Definition.</span><br>

<div class="statement" markdown="1">

$\mathbb{Z}_p$ and $\mathbb{Q}$ are called a "**<u>Prime Field</u>**".

</div>