---
title: "Point and Interval Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Introduction to Estimation
- Point Estimation
- Interval Estimation

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




