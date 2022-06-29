---
title: "Point Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---


2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- [Introduction to Estimation](#introduction-to-estimation)
- [Point Estimation](#point-estimation)
  - unbiased estimator 🔥
  - variance of estimator 🔥
  - the most efficient estimator of $\theta$
  - MSE of an estimator

<hr/>

## Introduction to Estimation

<div class="statement" markdown="1">

"\<**Statistics**\> is the area of science which can make inferences from data set."

</div>

<div class="statement" markdown="1">

"\<**Statistical Inference; 통계적 추론**\> means making generalization about the <u>population properties</u> <u>based on a random sample</u>."

</div>

Supp. someone gave you some data set $\\{ x_1, \dots, x_n \\}$ and it is known that this data set is taken from a normal random sample $X_i \sim N(\mu, 1)$.

Q. You are asked to estimate $\mu$. What can be a good estimate of $\mu$ from the sample?

A. $\bar{x}$, sample mean<br/>
why? by LLN, $\bar{x} \rightarrow \mu$ as $n \rightarrow \infty$.

<br/>

위의 sample mean $\bar{x}$ 같이 모집단(population)의 성질을 추론하는 것을 \<**추정(Estimation)**\>이라고 한다.

추정에는 \<Point Estimation\>과 \<Interval Estimation\>, 2가지 방식이 존재한다.

population mean $\mu$을 추정하기 위해 sample mean $\bar{x}$를 사용하는 것은 \<Point Estimation\> 방식이다.

만약 "population mean $\mu$는 어떤 범위(interval) $(a, b)$에서 높은 확률로 존재할 것이다"라고 interval $(a, b)$을 제시하는 방식을 \<Interval Estimation\>이라고 한다.

ex) $P\left( \mu \in (a, b) \right) \approx 0.99 \quad \text{or} \quad 0.95$.

💥 Note: For true distribution $N(\mu, \sigma^2)$, $\mu$, $\sigma$ are <span class="half_HL">unknown, and not random</span>!!

<hr/>

## Point Estimation

Let $X_1, \dots, X_n$ be a random sample and $X_i \sim f(x; \theta)$ for some pdf(or pmf), and let $x_1, \dots, x_n$ be sample points.

A \<Point Estimation\> of some population parameter $\theta$ is <span class="half_HL">a single value $\hat{\theta}$ of statistic[^1] $\hat{\Theta}$</span>.

이때, statistic $\hat{\Theta}$를 estimator라고 하며, <span class="half_HL">estimator $\hat{\Theta}$는 Random Variable이다</span>.

(hat $\hat{x}$이 붙으면 random sample로부터 유도되는 대상이다.)

<br>

<span class="statement-title">Example.</span><br>

Let $X_1, X_2, \dots, X_n$ be a random sample taken from $N(\mu, \sigma^2)$.

Q1\. What can be a point estimator of $\mu$?

A1. sample mean, $\bar{X} = \dfrac{X_1 + \cdots + X_n}{n}$.

<br/>

Q2. How about a point estimator of $\sigma^2$?

A2. sample variance, $\displaystyle S^2 = \dfrac{1}{n-1} \sum^n_i (X_i - \bar{X})^2$ where $E[S^2] = \sigma^2$

or $\displaystyle \hat{S}^2 = \dfrac{1}{n} \sum^n_i (X_i - \bar{X})^2$ where $E[\hat{S}^2] = \dfrac{n-1}{n} \sigma^2$.

<div class="light-margin"></div>

Q3. 두 estimator 중 어떤 것이 더 좋은가?

A3. 두 estimator의 \<**bias**\>를 비교한다!

### Unbiased Estimator

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> unbiased estimator 🔥<br>

A statistic $\hat{\Theta}$ is called an \<**unbiased estimator**\> if

$$
E[\hat{\Theta}] = \theta \quad \text{for all} \quad \theta
$$

즉, <span class="half_HL">\<Estimator\>에 평균을 취했을 때, population parameter $\theta$가 유도되는 estimator</span>를 말한다!

<div class="light-margin"></div>

$E[\hat{\Theta} - \theta]$ is the "**bias**" of $\hat{\Theta}$ related to $\theta$.

💥 $E[\hat{\Theta} - \theta] = 0$, unbiased!

</div>


<span class="statement-title">Example.</span><br>

Let $X_1, X_2, \dots, X_n$ be a random sample taken from $N(\mu, \sigma^2)$.

Then, $\bar{X}$ is an unbiased estimator of $\mu$, and $S^2$ is an unbiased estimator of $\mu$.

Note that $E \left[ \frac{2X_1 + 0.5 X_2 + 0.5 X_3 + \cdots + X_n}{n}\right] = \mu$, so that one is also an unbiased estimator!

(Generalization) Let's consider a weigted average $\displaystyle\bar{X}_w = \sum^n_i w_i X_i$. This estimator is also an unbiased estimator.

$$
E\left[ \bar{X}_w \right] = \sum^n_i w_i E[X_i] = \cancelto{1}{\left( \sum^n_i w_i \right)} \mu = \mu
$$

Q. Why we use $\bar{X}$ instead of $\bar{X}_w$ for an estimator of $\mu$?

A. Because the **"variance"** of $\bar{X}$ is less than $\bar{X}_w$!

$$
\text{Var}(\bar{X}) = E \left[ (\bar{X} - \mu)^2 \right] = \frac{\sigma^2}{n} \le \text{Var}(\bar{X}_w)
$$

### Variance of Estimator

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> variance of estimator 🔥<br>

For an estimator $\hat{\Theta}$, the variance of estimator is

$$
\text{Var}(\hat{\Theta}) = E \left[ (\hat{\Theta} - E[\hat{\Theta}])^2 \right]
$$

\* Variance의 정의를 그대로 따른다. 그러나 $\hat{\Theta}$가 statistic, 즉 function of random samples $\hat{\Theta} = f(X_1, ..., X_n)$이기 떄문에 실제 계산은 random sample의 distribution $X_i \sim g(x; \mu, \sigma)$를 활용하면 된다. $\text{Var}(\hat{\Theta}) = \text{Var}(g(X_1, ..., X_n))$

</div>

<br/>


<span class="statement-title">Claim.</span><br>

Among all weighted averages $\\{ \bar{X}_w : w = (w_1, \dots, w_n), \sum w_i = 1\\}$, $\bar{X}$ has the smallest variance.

<div class="math-statement" markdown="1">

We know that $\displaystyle\text{Var}(\bar{X}) = \frac{\sigma^2}{n}$.

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

### Most Efficient Estimator

"bias"와 "variance"를 종합해 어떤 estimator가 좋은 estimator인지 판단할 수 있다.

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> the most efficient estimator of $\theta$ 🔥<br>

Among all <u>unbiased estimators</u> of parameter $\theta$, the one <u>with the smallest variance</u> is called **\<the most efficient estimator of $\theta$\>**.

</div>

<br/>

<span class="statement-title">Remark.</span><br>

When $X_i$'s are iid $N(\mu, \sigma^2)$, it is known that $\bar{X}$ is the most efficient estimator of $\mu$.

<br/>

Q. 왜 most efficient estimator는 unbiased estimator 중에서 고르는 걸까? biased estimator 중에서 variance가 가장 작은게 있을 수도 있지 않을까?

A. Yes, it is possble that <span class="half_HL">a biased estimator can have smaller variance</span> than an unbiased estimator.

<br/>

<span class="statement-title">Exercise.</span><br>

Let $X_1, \dots, X_n$ be iid $N(\mu, \sigma^2)$.

Let $\displaystyle S^2 := \frac{1}{n-1} \sum^n_i (X_i - \bar{X})^2$ and $\displaystyle \hat{S}^2 := \frac{1}{n} \sum^n_i (X_i - \bar{X})^2$

Show that $\text{Var}(S^2) > \text{Var}(\hat{S}^2)$.

(Homework🎈)

### Mean Squared Error

\<MSE; Mean Squared Error\>를 Point Estimator의 평가 지표로 사용할 수도 있다!

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> MSE; Mean Squared Error 🔥<br>

The \<MSE; Mean Squared Error\> of an estimator is defined as 

$$
\text{MSE} := E \left[ \left( \hat{\Theta} - \theta \right)^2 \right]
$$

</div>

<div class="statement" markdown="1">

<span class="statement-title">Claim.</span><br/>

$$
\text{MSE} 
:= E \left[ \left( \hat{\Theta} - \theta \right)^2 \right] 
= \text{Var}(\hat{\Theta}) + \left[ \text{Bias} \right]^2
$$

where $\text{Bias} := E \left[ \hat{\Theta} - \theta \right]$.

</div>

<div class="math-statement" markdown="1">

<span class="statement-title">*Proof*.</span><br/>

(Homework🎈) / [(Solution)]({{"/2021/06/06/statistics-ps1.html" | relative_url}})

</div>

<hr/>

이어지는 포스트에서는 또다른 estimation 방식인 \<Interval Estimation\>에 대해 살펴보겠다. 이때, 주어진 Interval이 얼마나 좋은지 알려주는 지표가 바로 \<confidence level\> $1 - \alpha$다!

👉 [Interval Estimation, and confidence level]({{"/2021/05/06/interval-estimation-and-confidence-level.html" | relative_url}})

포스트에 제시 되었던 HW 문제들은 아래의 포스트에 별도로 정리해두었다.

👉 [Statistics - PS1]({{"/2021/06/06/statistics-ps1.html" | relative_url}})

<hr/>

[^1]: \<statistic; 통계량\>은 random samples $X_1, ..., X_n$의 함수 $f(X_1, ..., X_n)$을 말한다. [Sampling Distribution]({{"/2021/04/25/sampling-distribution.html" | relative_url}}) 포스트 참고