---
title: "Interval Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- invertal estimator; $(\hat{\theta}_L, \hat{\theta}_U)$
- $100 \cdot (1 - \alpha)$% confidence interval
  - confidence level; $1-\alpha$

<hr/>

Let $X_1, X_2, \dots, X_n$ be a random sample with $X_i \sim f(x; \theta)$, and $x_1, x_2, \dots, x_n$ be the values of the sample.

Here $\theta$ is unknown. The \<**interval estimation**\> is to find $(\hat{\theta}_L, \hat{\theta}_U)$ in which we expect to find the true value of the parameter $\theta$.

<br/>

Q. How to find the interval?

A1. $\theta \in (-\infty, \infty)$ → bad! 🤬

A2. We would construct two estimators $\hat{\theta}_L$ and $\hat{\theta}_U$ from the random sample such that $P(\hat{\theta}_L < \theta < \hat{\theta}_U) = 1 - \alpha$.

Here, $(\hat{\theta}_L, \hat{\theta}_U)$ is called an \<interval estimator\> of $\theta$, <span class="half_HL">$(\hat{\theta}_L, \hat{\theta}_U)$ is called a $100 \cdot (1 - \alpha)$% confidence interval</span>. 🔥

Also, $1-\alpha$ is called the \<**confidence coefficient**\> or \<**confidence level**\>. 🔥

We usually take $\alpha = 0.01, \; 0.05, \; 0.1$.

💥 Note that $(\hat{\theta}_L, \hat{\theta}_U)$ is not unique!! (꼭 대칭일 필요는 없다는 말)

<hr/>

지금부터는 사례들을 살펴보며, \<interval estimation\>에 대해 살펴보겠다!

- Estimate $\mu$ when $\sigma^2$ is known
- Estimate $\mu$ when $\sigma^2$ is unknown

<hr/>

<span class="statement-title">Example.</span><br>

<div class="img-wrapper">
<img src= "{{"/images/probability-and-statistics/interval-estimation-example-1.png" | relative_url }}" width=550>
</div>

- $n=100$, $\bar{X} = 170$.
- $\sigma = 20$

<div class="math-statement" markdown="1">

1\. We use $\bar{X}$ as a point estimator for $\mu$.

2\. We can use CLT here.

$$
\frac{\bar{X} - \mu}{\sigma / \sqrt{n}} \overset{D}{\approx} N(0, 1)
$$

$$
\begin{aligned}
P(\hat{\mu}_L < \mu < \hat{\mu}_U) 
&= 0.95 \\
&= P(-z_{0.025} \le z \le z_{0.025}) \\
&\approx P \left(-1.96 \le \frac{\bar{X} - \mu}{\sigma / \sqrt{n}} \le 1.96 \right) \\
&= P \left( \bar{X} - 1.96 \frac{\sigma}{\sqrt{n}} \le \mu \le \bar{X} + 1.96 \frac{\sigma}{\sqrt{n}} \right)
\end{aligned}
$$

Here, we have $\hat{\mu}_L := \bar{X} - 1.96 \dfrac{\sigma}{\sqrt{n}}$, $\hat{\mu}_U := \bar{X} + 1.96 \dfrac{\sigma}{\sqrt{n}}$

$\therefore$ A 95% confidence interval would be $(170 - 3.92, 170 + 3.92)$.

</div>

<span class="statement-title">Remark.</span> Confidence Interval on $\mu$ when $\sigma^2$ is knonw<br>

Let $x_1, \dots, x_n$ be given data points from a random sample $X_1, \dots, X_n$ with knwon population variance $\sigma^2$ and unkwown population mean $\mu$.

If $\bar{x}$ is the sample mean, a $100(1-\alpha)\%$ confidence interval for $\mu$ is given by

$$
\left( \bar{x} - z_{\alpha/2} \frac{\sigma}{\sqrt{n}} , \bar{x} + z_{\alpha/2} \frac{\sigma}{\sqrt{n}} \right)
$$

Note that this is an approximate interval unless $X_i \sim N(\mu, \sigma^2)$.

<br/>

Q1. IS it true that $P \left( \mu \in (\hat{\mu}_L, \hat{\mu}_U) \right) \overset{?}{=} 0.95$? 🔥

A1. No!!

Q2. Then what does the confidence interval really mean?

A2. Its the number of counts that $\mu$ is actually belong to sampled interval! 🔥

<div class="math-statement" markdown="1">

Let $x_1, \dots, x_n$ be a random sample. Supp. we obtain 1000 samples and each sample has size $n$. Then, we have the following:

1st sample: $x_{11}, x_{12}, \dots, x_{1n}$ → $\bar{x}_1$ → confidence $$(\bar{\mu}_{1L}, \bar{\mu}_{1U})$$

2nd sample: $x_{21}, x_{22}, \dots, x_{2n}$ → $\bar{x}_1$ → confidence $$(\bar{\mu}_{2L}, \bar{\mu}_{2U})$$

$\vdots$

1000th sample: $x_{1000, 1}, x_{1000, 2}, \dots, x_{1000, n}$ → $\bar{x}_1$ → confidence $$(\bar{\mu}_{1000, L}, \bar{\mu}_{1000, U})$$

이렇게 얻은 1000개의 interval estimation에 대해, 정확히 95%의 비율, 즉 950개의 interval에 true parameter $\mu$가 실제로 포함되어 있다는 말!

</div>

<span class="statement-title">Definition.</span> Error of estimation<br>

Now, let's consider the error $\| \bar{x} - \mu \|$.

For an interval estimation $\mu \in \left( \bar{x} - z_{\alpha/2} \frac{\sigma}{\sqrt{n}}, \bar{x} + z_{\alpha/2} \frac{\sigma}{\sqrt{n}}\right)$, the error is

$$
\left| \bar{x} - \mu \right| \le z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}
$$

<span class="statement-title">Thereom.</span><br>

If $\bar{x}$ is used as an estimate of $\mu$, we can be $100(1-\alpha)\%$ confident that the <u>error</u> will note exceed $z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$.



<hr/>

