---
title: "Variance Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Singe Sample Estimation: Variance Estimation
- Two Samples Estimation: The ratio of two variances

<hr/>

### Singe Sample Estimation: Variance Estimation

Let $X_1, \dots, X_n$ be a random sample from $N(\mu, \sigma^2)$.

Q. Find $100(1-\alpha)\%$ confidence interval for $\sigma^2$.

1\. choose a point estimator for $\sigma^2$.

$$
S^2 = \frac{1}{n-1} \cdot \sum^n_{i=1} (X_i - \bar{X})^2
$$

and also

$$
\frac{(n-1) S^2}{\sigma^2} \; \sim \; \chi^2 (n-1)
$$

2\. Find confidence interval by using $\dfrac{(n-1) S^2}{\sigma^2} \; \sim \; \chi^2 (n-1)$.

$$
1 - \alpha = P \left( \chi^2_{1-\alpha/2} (n-1) \; \le \; \frac{(n-1)s^2}{\sigma^2}\; \le \; \chi^2_{\alpha/2} (n-1)\right)
$$

<div class="img-wrapper">
<img src= "{{"/images/probability-and-statistics/chi-square-distribution.png" | relative_url }}" width=450>
</div>

Therefore, the confidence interval for $\sigma^2$ is

$$
\left( 
  \frac{(n-1)\cdot s^2}{\chi^2_{\alpha/2}},
  \frac{(n-1)\cdot s^2}{\chi^2_{1 - \alpha/2}}
\right)
$$

where $\chi^2_{\alpha/2}$ and $$\chi^2_{1-\alpha/2}$$ are $\chi^2$-values with $n-1$ dof.

💥 NOTE: $X_1, \dots, X_n$ should follow $N(\mu, \sigma^2)$.

💥 NOTE: $\chi^2$ distribution is NOT symmetric!

<hr/>

### Two Samples Estimation: The ratio of two variances

Let $X_1, \dots, X_{n_1}$ be a random sample from $N(\mu_1, \sigma_1^2)$.

Let $Y_1, \dots, Y_{n_2}$ be a random sample from $N(\mu_2, \sigma_2^2)$.

Supp. $X_i$s and $Y_j$s are independent.

Q. Find $100(1-\alpha)\%$ confidence interval for $\sigma_1^2 / \sigma_2^2$.

A. We can use $s_1^2 / s_2^2$ instead!!

$$
\frac{s_1^2 / \sigma_1^2}{s_2^2 / \sigma_2^2} \; \sim \; F(n_1-1, n_2-1)
$$

따라서,

$$
1 - \alpha
= P \left( f_{1-\alpha/2} \, (n_1 - 1, n_2 - 1) \; \le \; \frac{s_1^2 / \sigma_1^2}{s_2^2 / \sigma_2^2} \; \le \; f_{\alpha/2} \, (n_1 - 1, n_2 - 1) \right)
$$

Note that $f_{1-\alpha/2} \, (n_1 - 1, n_2 - 1) = \dfrac{1}{f_{\alpha/2} \, (n_2 - 1, n_1 - 1)}$.

Therefore, the confidence interval for $\sigma_1^2 / \sigma_2^2$ is

$$
\left( 
  \frac{s_1^2}{s_2^2} \cdot \frac{1}{f_{\alpha/2} \, (n_1 - 1, n_2 - 1)}, \; 
  \frac{s_1^2}{s_2^2} \cdot f_{\alpha/2} \, (n_2 - 1, n_1 - 1)
\right)
$$

<hr/>

이어지는 포스트에서는 또다른 Estimation 방법인 \<MLE; Maximum Likelihood Estimation\>에 대해 살펴본다.

👉 [Maximum Likelihood Estimation]({{"/2021/05/17/maximum-likelihood-estimation.html" | relative_url}})
