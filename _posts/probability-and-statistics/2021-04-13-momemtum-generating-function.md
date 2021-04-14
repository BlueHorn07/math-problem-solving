---
title: "Momemtum Generating Function"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- moment and MGF
- Examples
  - MGF of BIN
  - MGF of POI
  - MGF of NegBIN & Geo
  - MGF of Gamma & Exp
  - MGF of Normal
- Uniqueness Theorem for MGF
- MGF with Independence

<hr/>

## Moment Generating Function


<span class="statement-title">Definition.</span> moment<br>

We call $E[X^k]$ as the \<$k$-th moment\> of $X$.

<span class="statement-title">Remark.</span><br>

1\. Moments can be infinite.

2\. Moments may not be defined.

하지만, 정규 수업에서는 위의 사례들을 다루지는 않는다!

<br/>

<span class="statement-title">Definition.</span> MGF; Moment Generating Function<br>

The \<moment generating function\> of $X$ is given by

$$
M_X(t) := E[e^{tX}]
$$

Q. Why is this called the "moment" generating function?

A. Because it generates moments!

Note that

$$
\frac{d}{dt} e^{tX} = X e^{tX}
$$

and then,

$$
\begin{aligned}
\frac{d}{dt} M_X(t) &= \frac{d}{dt} E[e^{tX}] \\
        &= E \left[ \frac{d}{dt} e^{tX}\right] \\
        &= E \left[ X e^{tX}\right]
\end{aligned}
$$

위의 식 $\dfrac{d}{dt} M_X(t)$에서 우리가 $t=0$을 대입한다면, 우리는 손쉽게 moment를 얻을 수 있다!

$$
\left. \frac{d}{dt} M_X(t) \right|_{t=0} = \left. E \left[ X e^{tX}\right] \right|_{t=0} = E[X]
$$

마찬가지로 

$$
\frac{d^k}{dt^k} e^{tX} = \frac{d^{(k-1)}}{dt^{(k-1)}} X e^{tX} = X \frac{d^{(k-1)}}{dt^{(k-1)}} e^{tX} = \cdots = X^k e^{tX}
$$

인 사실을 이용하면, $k$-th moment $E[X^k]$도 쉽게 구할 수 있다!!

$$
\left. \frac{d^k}{dt^k} M_X(t) \right|_{t=0} = \left. E \left[ X^k e^{tX}\right] \right|_{t=0} = E[X^k]
$$

<hr/>

<span class="statement-title">Example.</span><br>

Let $X \sim \text{BIN}(n, p)$, then find its MGF.

$$
\begin{aligned}
M_X(t) &= E[e^{tX}] \\
    &= \sum_k e^{tk} f(k) \\
    &= \sum^n_{k=0} e^{tk} \cdot \binom{n}{k} p^k q^{n-k} \\
    &= \sum^n_{k=0} \binom{n}{k} \cdot \left( p \cdot e^t \right)^k q^{n-k} \\
    &= \left( p \cdot e^t + q \right)^n
\end{aligned}
$$

위의 MGF를 통해 직접 $E[X]$를 구해보면,

$$
\left. \frac{d}{dt} M_X(t) \right|_{t=0} = \left. n \cdot p \cdot \left( p \cdot e^t + q \right)^{n-1} \right|_{t=0} = np
$$

<br/>

<span class="statement-title">Example.</span><br>

Let $X \sim \text{Poi}(\lambda)$, find its MGF.

$$
\begin{aligned}
M_X(t) &= E[e^{tX}] \\
    &= \sum^{\infty}_{k=0} e^{tk} \cdot e^{-\lambda} \frac{\lambda^{k}}{k!} \\
    &= e^{-\lambda} \cdot \sum^{\infty}_{k=0} \frac{\left(e^t \lambda \right)^k}{k!} \\
    &= e^{-\lambda} \cdot \exp \left( \lambda e^t\right) = \exp (\lambda(e^t - 1))
\end{aligned}
$$

이게 위의 MGF를 이용해 $E[X]$를 구해보자!

$$
\begin{aligned}
\left. \frac{d}{dt} \exp (\lambda(e^t - 1)) \right|_{t=0} &= \left. \left( \frac{d}{dt} \lambda(e^t - 1) \right) \cdot \exp (\lambda(e^t - 1)) \right|_{t=0} \\
&= \left. \lambda \cdot \exp (\lambda(e^t - 1)) \right|_{t=0} \\
&= \lambda \cdot \exp (\lambda(1 - 1)) = \lambda \cdot 1 \\
&= \lambda
\end{aligned}
$$

<span class="statement-title">Example.</span><br>

Let $X \sim \text{NegBIN}(k, p)$, find its MGF.

$$
\begin{aligned}
M_X(t) &= \sum^{\infty}_{x=k} e^{tx} \cdot \binom{x-1}{k-1} p^{k} q^{x-k} \\
    &= \left(\frac{p}{q}\right)^k \cdot \sum^{\infty}_{x=k} \binom{x-1}{k-1} \left( e^t q \right)^{x} \\
\end{aligned}
$$

위의 식에서 $y = x-k$를 대입하자.

$$
\begin{aligned}
\left(\frac{p}{q}\right)^k \cdot \sum^{\infty}_{x=k} \binom{x-1}{k-1} \left( e^t q \right)^{x} &= 
\left(\frac{p}{q}\right)^k \cdot \sum^{\infty}_{y=0} \binom{y+k-1}{k-1} \left( e^t q \right)^{y+k} \\
&= \left(\frac{p}{q}\right)^k \cdot \left( e^t q \right)^k \sum^{\infty}_{y=0} \binom{y+k-1}{k-1} \left( e^t q \right)^y \\
&= (p \cdot e^t)^k \cdot \sum^{\infty}_{y=0} \binom{y+k-1}{k-1} \left( e^t q \right)^y
\end{aligned}
$$

이때, $\binom{y+k-1}{k-1}$에 대해 아래의 식이 성립한다.

$$
\binom{y+k-1}{k-1} = \left( -1 \right)^y \cdot \binom{-k}{y}
$$

위의 식을 대입하면,

$$
\begin{aligned}
(p \cdot e^t)^k \cdot \sum^{\infty}_{y=0} \binom{y+k-1}{k-1} \left( e^t q \right)^y 
&= (p \cdot e^t)^k \cdot \sum^{\infty}_{y=0}  \left( -1 \right)^y \cdot \binom{-k}{y} \left( e^t q \right)^y \\
&= (p \cdot e^t)^k \cdot \left( 1 - q\cdot e^t \right)^{-k} \\
&= \left( \frac{p \cdot e^t}{1 - q\cdot e^t} \right)^k \qquad \text{for} \quad 1 - q \cdot e^{t} > 0
\end{aligned}
$$

만약 $k=1$이라면, RV $X$가 Geometric Distribution을 따르게 되므로, Geo의 MGF는 아래와 같다는 사실을 알 수 있다.

$$
M_X (t) = \frac{p \cdot e^t}{1 - q\cdot e^t} \qquad \text{for} \quad 1 - q \cdot e^{t} > 0
$$

<span class="statement-title">Example.</span><br>

Let $X \sim \text{Gamma}(\alpha, \beta)$, find its MGF.

우리는 논의의 편의를 위해 $Y \sim \text{Gamma}(\alpha, 1)$를 먼저 살펴볼 것이다. <small>($Y$에 대해 $\beta Y = X$이기 때문!)
</small>

$$
\begin{aligned}
M_Y(t) &= E[e^{tY}] \\
    &= \int^{\infty}_0 e^{tx} \cdot \frac{1}{\Gamma(\alpha)} \cdot x^{\alpha-1} e^{-x} \; dx\\
    &= \frac{1}{\Gamma(\alpha)} \cdot \int^{\infty}_0 x^{\alpha-1}\cdot e^{-(1-t)x} \; dx \\
\end{aligned}
$$

이때, 위의 식에서 $\beta = \dfrac{1}{1-t}$로 두면, 유도 과정 중에 감마 분포에 대한 적분이 있기 때문에 손쉽게 과정을 진행할 수 있다.

$$
\begin{aligned}
\frac{1}{\Gamma(\alpha)} \cdot \int^{\infty}_0 x^{\alpha-1}\cdot e^{-(1-t)x} \; dx 
&= \frac{1}{\Gamma(\alpha)} \cdot \int^{\infty}_0 x^{\alpha-1}\cdot e^{-\frac{x}{1/(1-t)}} \; dx \\
&= \frac{1}{(1-t)^{\alpha}} \cdot \cancelto{1}{\int^{\infty}_0 \frac{1}{\Gamma(\alpha) \cdot \frac{1}{(1-t)^{\alpha}}} \cdot x^{\alpha-1} \cdot e^{-\frac{x}{1/(1-t)}} \; dx} \\
&= \frac{1}{(1-t)^{\alpha}} \qquad \text{for} \quad t < 1
\end{aligned}
$$

이제, $X = \beta Y$의 관계식을 이용해 $X$의 MGF를 구하면

$$
\begin{aligned}
M_X(t) = E[e^{tX}] = E[e^{t\beta Y}] = \frac{1}{(1-\beta t)^{\alpha}} \qquad \text{for} \quad \beta t < 1 \quad (=t < \lambda)
\end{aligned}
$$

이제 위의 식을 이용해 Exponential Distribution의 MGF도 구할 수 있는데,

$$
M_X(t) = \frac{1}{1-\beta t} \qquad \text{for} \quad \beta t < 1 \quad (=t < \lambda)
$$

<span class="statement-title">Example.</span><br>

Let $Z \sim N(0, 1)$, then find its MGF.

$$
\begin{aligned}
M_Z (t) &= E[e^{tZ}] \\
    &= \int^{\infty}_{-\infty} e^{tx} \cdot \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}} \; dx \\
    &= \int^{\infty}_{-\infty} \frac{1}{\sqrt{2\pi}} \cdot e^{tx} \cdot e^{-\frac{(x-t)^2 + 2xt - t^2}{2}} \; dx \\
    &= \int^{\infty}_{-\infty} \frac{1}{\sqrt{2\pi}} \cdot e^{-\frac{(x-t)^2}{2}} \cdot e^{tx} \cdot e^{-\frac{2xt-t^2}{2}} \; dx \\
    &= e^{t^2 / 2} \cdot \cancelto{1}{\int^{\infty}_{-\infty} \frac{1}{\sqrt{2\pi}} \cdot e^{-\frac{(x-t)^2}{2}}  \; dx} \\
    &= e^{t^2 / 2}
\end{aligned}
$$

이제 $X \sim N(\mu, \sigma^2)$으로 일반화하면, $X = \sigma Z + \mu$이므로

$$
\begin{aligned}
M_X(t) &= E[e^{tX}] = E[e^{\sigma t z + \mu t}] \\
&= e^{\mu t} \cdot E[e^{\sigma t z}] \\
&= e^{\mu t} \cdot e^{\sigma^2t^2 / 2} \\
&= \exp \left( \mu t + \frac{\sigma^2 t^2}{2}\right)
\end{aligned}
$$

<hr/>

<span class="statement-title">Remark.</span><br>

If $X$ has the mgf $M_X(t)$, then $Y = aX + b$ has the mgf 

$$
M_Y (t) = e^{bt} \cdot M_X(at)
$$

<br/>

<hr/>

mgf는 미분만 하면 momentum을 쉽게 구할 수 있다는 장점도 있지만, \<Uniqueness Theroem\>이라는 아래의 정리에 의해 두 RV이 동일한 분포를 가지는 것을 보장하는 조건이 되기도 한다.

<span class="statement-title">Theorem.</span> Uniqueness Theorem<br>

If $M_X(t) = M_Y(t)$ for all $t \in (-\delta, \delta)$ for some $\delta > 0$,

then $X$ and $Y$ have the same distribution.

따라서, 두 RV이 동일한 분포를 가지는지 확인하려면, 두 RV의 mgf를 확인해보면 된다!

<br/>

<span class="statement-title">Example.</span><br>

Q. Let $X$ be a random variable with $M_X(t) = \dfrac{1}{1-2t}$ for $t < \frac{1}{2}$. What is the distribution of $X$?

A. $X \sim \text{Exp}(\lambda = 2)$

<br/>

<span class="statement-title">Example.</span><br>

Q. How about $M_X(t) = \dfrac{1}{2} e^t + \dfrac{1}{2} e^{-t}$ for $t \in \mathbb{R}$?

A. 

$$
\begin{aligned}
M_X(t) &= E[e^{tX}] \\
    &= \sum e^{tX} \cdot f(x) \\
    &= \sum_x e^{tX} \cdot P(X = x) \\
    &= e^{1\cdot x} \cdot P(X = 1) + e^{-1\cdot x} \cdot P(X = -1) \\
    &= e^{x} \cdot \frac{1}{2} + e^{-x} \cdot \frac{1}{2}
\end{aligned}
$$

이때, 아래와 같은 분포를 가지는 RV $Y$가 있다고 가정하자.

$$
f(y) := \begin{cases}
    1/2 & \text{if} \quad x \pm 1 \\
    0 & \text{else}
\end{cases}
$$

이때, $Y$의 mgf는 $M_Y(t) = \dfrac{1}{2}e^t + \dfrac{1}{2}e^{-t}$이다.

위에서 언급한 \<Uniqueness Theorem for MGF\>에 의해 $X$와 $Y$는 동일한 분포를 가진다. $\blacksquare$

<br/>
<hr/>

If $X \perp Y$, then 

$$
M_{X+Y} (t) = M_X(t) \cdot M_Y(t)
$$

In general, if $X_1, X_2, \dots, X_n$ are independent,, then 

$$
M_{X_1 + \cdots + X_n}(t) = M_{X_1} (t) + \cdots + M_{X_n} (t) = \sum^n_{i=1} M_{X_i} (t)
$$

<br/>

<span class="statement-title">Example.</span> Tow Independent BIN<br>

Let $X \sim \text{BIN}(n, p)$ and $Y \sim \text{BIN}(m, p)$, and $X \perp Y$.

Then, 

$$
X+Y \sim \text{BIN}(n+m, p)
$$

<div class="math-statement" markdown="1">

$$
\begin{aligned}
M_{X+Y}(t) &= M_X(t) \cdot M_Y(t) \quad (X \perp Y) \\
    &= (pe^t + q)^n \cdot (pe^t + q)^m \\
    &= (pe^t + q)^{n+m}
\end{aligned}
$$

위의 mgf는 곧 $\text{BIN}(n+m, p)$의 mgf와 동일하다. $\blacksquare$

</div>

<br/>

<span class="statement-title">Example.</span> Two Independent Poi<br>

Let $X \sim \text{Poi}(\lambda)$ and $Y \sim \text{Poi}(\mu)$, and $X \perp Y$.

Then, 

$$
X+Y \sim \text{Poi}(\lambda + \mu)
$$

<div class="math-statement" markdown="1">

$$
\begin{aligned}
M_{X+Y}(t) &= M_X(t) \cdot M_Y(t) \quad (X \perp Y) \\
    &= \exp \left( \lambda (e^t - 1) \right) \cdot \exp \left( \mu (e^t - 1) \right) \\
    &= \exp \left( (\lambda + \mu) (e^t - 1) \right)
\end{aligned}
$$

위의 mgf는 곧 $\text{Poi}(\lambda + \mu)$의 mgf와 동일하다. $\blacksquare$

</div>

<br/>

<span class="statement-title">Example.</span> Two Independent NegBIN<br>

Let $X \sim \text{NegBIN}(r_1, p)$ and $Y \sim \text{NegBIN}(r_2, p)$, and $X \perp Y$.

Then, 

$$
X+Y \sim \text{NegBIN}(r_1 + r_2, p)
$$


<br/>

<span class="statement-title">Example.</span> Two Independent Normal<br>

Let $X \sim N(\mu_1, \sigma_1^2)$ and $Y \sim N(\mu_2, \sigma_2^2)$, and $X \perp Y$.

Then, 

$$
X+Y \sim N(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)
$$

<div class="math-statement" markdown="1">

$$
\begin{aligned}
M_{X+Y}(t) &= M_X(t) \cdot M_Y(t) \quad (X \perp Y) \\
    &= \exp \left( \mu_1 t + \frac{\sigma_1^2 t^2}{2} \right) \cdot \exp \left( \mu_2 t + \frac{\sigma_2^2 t^2}{2} \right) \\
    &= \exp \left( (\mu_1 + \mu_2) t + \frac{(\sigma^2 + \sigma_2^2) t^2}{2} \right)
\end{aligned}
$$

위의 mgf는 곧 $N(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$의 mgf와 동일하다. $\blacksquare$

</div>

<br/>

<span class="statement-title">Example.</span> Two Independent Gamma<br>

Let $X \sim \text{Gamma}(\alpha_1, \beta)$ and $Y \sim \text{Gamma}(\alpha_2, \beta)$, and $X \perp Y$.

Then, 

$$
X+Y \sim \text{Gamma}(\alpha_1 + \alpha_2, \beta)
$$

위의 사실을 이용하면, $\text{Exp}$와 $\chi^2$에 대해서도 two independent 경우를 논할 수 있다!

1\. If $X \sim \text{Exp}(\beta)$, $Y \sim \text{Exp}(\beta)$ and $X \perp Y$. Then,

$$
X + Y \sim \text{Gamma}(2, \beta)
$$

※ $\text{Exp}(\beta) = \text{Gamma}(1, \beta)$

<br/>

2\. If $X \sim \chi^2(n)$, $Y \sim \chi^2(m)$ and $X \perp Y$. Then,

$$
X + Y \sim \chi^2(n+m)
$$

※ $\chi^2(n) = \text{Gamma}(n/2, 2)$

<br/>

<span class="statement-title">Example.</span><br>

Let $X \sim \text{Exp}(\lambda)$, $Y \sim \text{Exp}(\mu)$ and $X \perp Y$.

Then, 

$$
Z = \min(X, Y) \sim \text{Exp}(\lambda + \mu)
$$
 
<hr/>

여기까지가 정규수업의 중간고사 시험 범위이다. 개인적으로 논리를 전개하는 부분은 식을 잘 정리하고, 문제를 잘 모델링하는 부분을 충분히 연습하면 될 것 같다. 다만, 각 분포의 정의와 형태가 조금씩 헷갈려서 시험 전에 모든 분포를 빠짐없이 다 기술할 수 있는지 백지(白紙)에 체크해보면 좋을 것 같다.
