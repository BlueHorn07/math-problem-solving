---
title: "Transformations of Random Variable"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Introudciton
- 1-1 Transformation
  - Discrete Case
  - Continuous Case

<hr/>

이번 챕터 "Ch07. Functions of Random Variables"에서는 RV $X$에 어떤 함수 $f(x)$를 씌워 $Y = f(X)$라는 새로운 RV를 만들때, 이 RV $Y$에 대한 분포를 살펴본다. 즉, $f(X)$에 대한 pdf, cdf를 구한다는 말이다.

쉬운 경우부터 조금 복잡한 경우까지 순서대로 살펴볼 것이며, $f(x)$가 1-1 function일 때, $f(X)$가 not 1-1일 때를 살펴본다. 뒷부분에서는 RV의 momemtum을 쉽게 구하는 도구인 \<MGF; Momentum Generating Function\> $M_X(t)$에 대해 살펴본다.

<hr/>

## 1-1 Transformation

### Discrete Case

<span class="statement-title">Example.</span><br>

Let $X$ be a RV with $P(X = \pm 1) = 1/2$.

Let $Y = 3X - 5$, find the pmf of $Y$.

$$
P(Y = y) = \begin{cases}
    1/2 & y=-2 \\
    1/2 & y=-8 \\
    \; 0 & \text{else}
\end{cases}
$$

위의 과정을 좀더 풀어서 살펴보자. 그러면,

$$
\begin{aligned}
P(Y = y) &= P(3X - 5 = y)\\
&= P(f(X) = y) \\
&= P(X = f^{-1}(y))
\end{aligned}
$$

즉, $f(X)$에서 역함수 $f^{-1}$를 이용해 $X$의 pmf로부터 손쉽게 $Y$의 pmf를 유도할 수 있다는 것이다!

$$
P(Y = y) = P(X = f^{-1}(y))
$$

<br/>

<span class="statement-title">Theorem.</span> Discrete Case<br>

1\. Supp. $X$ has pmf $f_X (x)$.

Let $Y=g(X)$ where $g$ is 1-1 function with the inverse $x = g^{-1}(y)$. 

Then,

$$
f_Y (y) = f_X (g^{-1}(y))
$$

<br/>

2\. Supp. $(X_1, X_2)$ has joint pmf $f_{X_1, X_2} (x_1, x_2)$. 

Let $Y_1 := u_1 (X_1, X_2)$ and $Y_2 := u_2 (X_1, X_2)$, and $X_1 := w_1(Y_1, Y_2)$ and $X_2 := w_2 (Y_1, Y_2)$.

Then,

$$
f_{Y_1, Y_2} (y_1, y_2) = f_{X_1, X_2} \left( w_1(y_1, y_2), w_2(y_1, y_2) \right)
$$

즉, $X_1$, $X_2$를 이용해 $Y_1$, $Y_2$를 정의한 식을 잘 풀어서, $Y_1$, $Y_2$를 이용해 $X_1$, $X_2$를 기술한 식 $w_1$, $w_2$를 정의하여 그것으로 pmf를 유도한다는 말이다! 당연한 접근을 수식으로 formal하게 기술한 것 정도라고 생각하면 된다.

<br/>

<span class="statement-title">Example.</span><br>

Let $X \sim \text{Poi}(\lambda)$ and $Y \sim \text{Poi}(\mu)$m, and $X \perp Y$.

Find the distribution of $X + Y$.

<div class="math-statement" markdown="1">

만약 $P(X+Y = 5)$라고 한다면, 이것을 계산하기 위해 $P(X = 0, Y=5)$, $P(X=1, Y=4)$, ..., $P(X=5, Y=0)$의 확률을 구해서 더할 것이다. 이 아이디어를 바탕으로 아래와 같이 식을 전개해보자!

$$
\begin{aligned}
P(X+Y = n) &= \sum^{\infty}_{k=0} P(X=n-k, Y = k) \\
           &= \sum^{\infty}_{k=0} P(X=n-k) P(Y = k) \quad (\text{independence}) \\
           &= \sum^{\infty}_{k=0}  e^{-\lambda} \frac{\lambda^{n-k}}{(n-k)!} \cdot e^{-\mu} \frac{\mu^k}{k!} \\
           &= \frac{e^{-(\lambda + \mu)}}{n!} \sum^{\infty}_{k=0} \frac{n!}{(n-k)!k!} \lambda^{n-k} \mu^k \\
           &= \frac{e^{-(\lambda + \mu)}}{n!} \cdot (\lambda + \mu)^n = e^{-(\lambda + \mu)} \frac{(\lambda + \mu)^n}{n!}
\end{aligned}
$$

즉, $P(X+Y = n)$는 $\text{Poi}(\lambda+\mu)$의 pmf라는 것을 유도할 수 있다! $\blacksquare$

</div>

<div class="math-statement" markdown="1">

We first find the joint pmf of $(X, X+Y)$, and then find th emarginal pmf of $X+Y$.

Let $U = X$, $V = X+Y$, then $X = U$, $Y = V - U$.

따라서, $U$, $V$에 대한 pmf는

$$
\begin{aligned}
f_{U, V} (u, v) &= f_{X, Y} (u, v-u) \\
                &= f_X (u) f_Y(v-u) \quad (\text{independence}) \\
                &= e^{-\lambda} \frac{\lambda^u}{u!} \cdot e^{-\mu} \frac{\mu^{v-u}}{(v-u)!} \\
                &= e^{-(\lambda + \mu)} \frac{\lambda^u}{u!} \frac{\mu^{v-u}}{(v-u)!}
\end{aligned}
$$

$U$, $V$에 대한 joint pmf를 구했으니, 이번에는 $V$에 대한 marginal pmf를 구해보자.

$$
\begin{aligned}
f_V (v) &= \sum_u f_{U, V} (u, v) \\
        &= \sum_u e^{-(\lambda+\mu)} \frac{\lambda^u}{u!} \frac{\mu^{v-u}}{(v-u)!} \\
        &= e^{-(\lambda+\mu)} \sum_u \frac{\lambda^u}{u!} \frac{\mu^{v-u}}{(v-u)!} \\
        &= \frac{e^{-(\lambda+\mu)}}{v!} \sum_u \frac{v!}{u!(v-u)!} \lambda^u \mu^{v-u} \\
        &= \frac{e^{-(\lambda+\mu)}}{v!} \cdot (\mu + \lambda)^v \\
        &= e^{-(\lambda+\mu)} \frac{(\mu + \lambda)^v}{v!}
\end{aligned}
$$

즉, $V = X+Y$에 대한 pmf는 결국 $\text{Poi}(\lambda + \mu)$인 것이다! $\blacksquare$

</div>

<hr/>

### Continuous Case

<span class="statement-title">Theorem.</span><br>

Let $X$ be a continuous RV with pdf $f_X (x)$.

Let $Y := g(X)$ wgere $g$ is 1-1 with inverse $x = h(y)$.

Then,

$$
f_Y (y) = f_X (h(y)) \cdot \left| h'(y) \right|
$$

<span class="statement-title">Example.</span><br>

1\. Let $X \sim N(\mu, \sigma^2)$ and let $Y := \dfrac{X - \mu}{\sigma}$.

Then,

$$
\begin{aligned}
f_Y (y) &= f_X (h(y)) \cdot \left| h'(y) \right| \\
        &= \frac{1}{\sqrt{2\pi} \sigma} \cdot \exp \left({- \frac{(h(y)-\mu)^2}{2\sigma^2}}\right) \cdot \left| \sigma \right|\\
        &= \frac{1}{\sqrt{2\pi} \cancel{\sigma}} \cdot \exp \left( - \frac{(\cancel{\sigma} y + \cancel{\mu} - \cancel{\mu})^2}{2\cancel{\sigma^2}} \right) \cdot \cancel{\sigma} \\
        &= \frac{1}{\sqrt{2\pi}} \cdot \exp \left( - y^2 / 2\right)
\end{aligned}
$$

2\. Let $X \sim \text{Gamma}(\alpha, 1)$, and let $Y := \beta X$.

**Claim**: $Y \sim \text{Gamma}(\alpha, \beta)$

$$
y = \beta x \iff x = \frac{y}{\beta} = h(y)
$$

and

$$
f_X (x) = \frac{1}{\Gamma(\alpha)} x^{\alpha - 1} e^{-x}
$$

then,

$$
\begin{aligned}
f_Y (y) &= f_X (h(y)) \cdot \left| h'(y) \right| \\
        &= \frac{1}{\Gamma(\alpha)} h(y)^{\alpha - 1} e^{-h(y)} \cdot \left| \frac{1}{\beta} \right| \\
        &= \frac{1}{\Gamma(\alpha) \beta} \cdot \left( \frac{y}{\beta}\right)^{\alpha-1} e^{-y/\beta} \\
        &= \frac{1}{\Gamma(\alpha) \beta^{\alpha}} \cdot y^{\alpha-1} e^{-y/\beta}
\end{aligned}
$$

따라서, $X \sim \text{Gamma}(\alpha, 1)$에서 $Y = \beta X$의 transformation을 취하면, $Y \sim \text{Gamma}(\alpha, \beta)$의 분포를 얻는다.

<br/>

3\. Let $\theta \sim \text{Unif}(-\pi/2, \pi/2)$, and let $X = \tan \theta$.

Find the pdf of $X$.

$$
h(x) = \arctan x \quad \text{and} \quad h'(x) = \frac{1}{1+x^2}
$$

위의 규칙에 맞춰 $X$의 분포를 유도해보면,

$$
\begin{aligned}    
f_X (x) &= f_\theta (h(x)) \cdot \left| h'(x) \right| \\
        &= \cancelto{\frac{1}{\pi}}{f_\theta (\arctan x)} \cdot \frac{1}{1+x^2} \quad (\text{Uniform distribution})\\
        &= \frac{1}{\pi} \frac{1}{1+x^2} 
\end{aligned}
$$

위와 같은 분포를 \<Cauchy Distribution\>라고 한다.
