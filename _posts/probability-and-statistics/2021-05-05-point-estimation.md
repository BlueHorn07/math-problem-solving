---
title: "Point Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Introduction to Estimation
- Point Estimation
  - unbiased estimator
  - the most efficient estimator of $\theta$
  - MSE of an estimator

<hr/>

<div class="statement" markdown="1">

"\<**Statistics**\> is the area of science which can make inferences from data set."

</div>

<div class="statement" markdown="1">

"\<**Statistical inference**\> means making generalization about the <u>population properties</u> <u>based on a random sample</u>."

</div>

Supp. someone gave you some data set $\\{ x_1, \dots, x_n \\}$ and it is known that this data set is taken from a normal random sample $X_i \sim N(\mu, 1)$.

Q. You are asked to estimate $\mu$. What ca be a good estimate of $\mu$ from the sample?

A. $\bar{X}$, sample mean

why? by LLN, $\bar{X} \rightarrow \mu$ as $n \rightarrow \infty$.

이때, $\bar{X}$의 경우, true parameter $\mu$에 대해 $\mathbb{R}$에 속하는 어떤 하나의 값을 주게 된다. 이런 형태의 estimation을 \<**point estimation**\>이라고 한다.

We may provide some interval which $\mu$ sits with some "high confidence".

ex) $P\left( \mu \in (a, b) \right) \approx 0.99 \quad \text{or} \quad 0.95$.

이런 형태의 estimation을 \<**interval estimation**\>이라고 한다.

💥 Note: For true distribution $N(\mu, \sigma^2)$, $\mu$, $\sigma$ are <span class="half_HL">unknown, but not random</span>!!

<hr/>

### Point Estimation

Let $X_1, \dots, X_n$ be a random sample and $X_i \sim f(x; \theta)$ for some pdf(or pmf), and let $x_1, \dots, x_n$ be sample points.

A \<point estimation\> of some population parameter $\theta$ is <span class="half_HL">a single value $\hat{\theta}$ of statistic $\hat{\Theta}$</span>.

💥 이때, $\hat{\Theta}$는 estimator이며, Random Variable이다.

<br>

<span class="statement-title">Example.</span><br>

Let $X_1, X_2, \dots, X_n$ be a random sample taken from $N(\mu, \sigma^2)$.

Q1\. What ca be a point estimator of $\mu$?

A1. sample mean, $\bar{X} = \dfrac{X_1 + \cdots + X_n}{n}$.

<br/>

Q2. How about a point estimator of $\sigma^2$?

A2. sample variance, $\displaystyle S^2 = \dfrac{1}{n-1} \sum^n_i (X_i - \bar{X})^2$ where $E[S^2] = \sigma^2$

or $\displaystyle \hat{S}^2 = \dfrac{1}{n} \sum^n_i (X_i - \bar{X})^2$ where $E[\hat{S}^2] = \dfrac{n-1}{n} \sigma^2$.

Q3. 두 estimator 중 어떤 것이 더 좋은가?

A3. 두 estimator의 \<bias\>를 비교해보자!

<br/>

<span class="statement-title">Definition.</span> unbaised estimator 🔥<br>

A statistic $\hat{\Theta}$ is called an \<**unbiased estimator**\> if

$$
E[\hat{\Theta}] = \theta \quad \text{for all} \quad \theta
$$

$E[\hat{\Theta} - \theta]$ is the bias of $\hat{\Theta}$ related to $\theta$.

💥 $E[\hat{\Theta} - \theta] = 0$, unbiased!

<br/>

<span class="statement-title">Example.</span><br>

Let $X_1, X_2, \dots, X_n$ be a random sample taken from $N(\mu, \sigma^2)$.

Then, $\bar{X}$ is an unbiased estimator of $\mu$, and $\S^2$ is an unbiased estimator of $\mu$.

Note that $E \left[ \frac{2X_1 + 0.5 X_2 + 0.5 X_3 + \cdots + X_n}{n}\right] = \mu$, so that one is also an unbiased estimator!

Let's consider a weigted average $\displaystyle\bar{X}_w = \sum^n_i w_i X_i$. This estimator is also an unbiased estimator.

$$
E\left[ \bar{X}_w \right] = \sum^n_i w_i E[X_i] = \cancelto{1}{\left( \sum^n_i w_i \right)} \mu = \mu
$$

Q. Why we use $\bar{X}$ instead of $\bar{X}_w$ for an estimator of $\mu$?

A. Because the variance of $\bar{X}$ is less than $\bar{X}_w$!

$$
\text{Var}(\bar{X}) = E \left[ (\bar{X} - \mu)^2 \right] = \frac{\sigma^2}{n} \le \text{Var}(\bar{X}_w)
$$

<span class="statement-title">Claim.</span><br>

Among all weighted averages $\\{ \bar{X}_w : w = (w_1, \dots, w_n), \sum w_i = 1\\}$, $\bar{X}$ has the smallest variance.

<div class="math-statement" markdown="1">

We know that $\displaystyle\text{Var} = \frac{\sigma^2}{n}$.

$$
\begin{aligned}
\text{Var}(\bar{X}_w)
&= \text{Var}\left( \sum^n_i w_i X_i \right) \\
&= \sum^n_i w_i^2 \cdot \text{Var}(X_i) \\
&= \sigma^2 \cdot \sum^n_i w_i^2
\end{aligned}
$$

For $\sum w_i = 1$, 

$$
0 \le \sum^n_i \left(w_i - \frac{1}{n}\right)^2 = \sum w_i^2 - \frac{2}{n} \sum w_i + n \cdot \frac{1}{n^2} = \sum w_i^2 - \frac{1}{n}
$$

따라서,

$$
\text{Var}(\bar{X}) = \frac{\sigma^2}{n} \le \sigma^2 \cdot \sum^n_i w_i^2 = \text{Var}(\bar{X}_w)
$$

$\blacksquare$

</div>

<span class="statement-title">Definition.</span> the most efficient estimator of $\theta$ 🔥<br>

Among all <u>unbiased estimators</u> of parameter $\theta$, the one <u>with the smallest variance</u> is called \<the most efficient estimator of $\theta$\>.

<br/>

<span class="statement-title">Remark.</span><br>

When $X_i$'s are iid $N(\mu, \sigma^2)$, it is known that $\bar{X}$ is the most efficient estimator of $\mu$.

<br/>

Q. biased estimator 중에서도 variance가 가장 작은게 있을 수도 있지 않을까?

A. Yes, it is possble that <span class="half_HL">a biased estimator can have smaller variance</span> than an unbiased estimator.

<br/>

<span class="statement-title">Exercise.</span><br>

Let $X_1, \dots, X_n$ be iid $N(\mu, \sigma^2$.

Let $\displaystyle S^2 := \frac{1}{n-1} \sum^n_i (X_i - \bar{X})^2$ and $\displaystyle \hat{S}^2 := \frac{1}{n} \sum^n_i (X_i - \bar{X})^2$

Show that $\text{Var}(S^2) > \text{Var}(\hat{S}^2)$.

(Homework🎈)

<hr/>

<span class="statement-title">Definition.</span> MSE; Mean Squared Error 🔥<br>

The \<MSE; Mean Squared Error\> of an estimator is defined as 

$$
\text{MSE} := E \left[ \hat{\Theta} - \theta \right]^2 = \text{Var}(\hat{\Theta}) + \left[ \text{Bias} \right]^2
$$

where $\text{Bias} := E \left[ \hat{\Theta} - \theta \right]$.

<div class="math-statement" markdown="1">

<span class="statement-title">*Proof*.</span><br/>

(Homework🎈)

</div>

<hr/>

이어지는 포스트에서는 또다른 estimation 방식인 \<Interval Estimation\>에 대해 살펴보겠다.

👉 [Interval Estimation]({{"/2021/05/05/interval-estimation.html" | relative_url}})


