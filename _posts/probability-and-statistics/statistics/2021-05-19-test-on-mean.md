---
title: "Test on Mean"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Test on Mean
  - When $\sigma$ is known
  - When $\sigma$ is unknown
- Test on Two Means
- Choice of Sample Size for testing mean
  - power of a test

<hr/>

(내용이 할만해서 지금은 생-략)

<hr/>

### Choice of Sample Size

<div class="img-wrapper">
<img src= "{{"/images/probability-and-statistics/choice-of-sample-size-1.png" | relative_url }}" width=650>
</div>

1\. Set Hypothesis

- $H_0$: $\mu=190$ (cm)
- $H_1$: $\mu=195$ (cm)

<div class="light-margin"></div>

2\. we want

- $\alpha = 0.05$
- $\beta \ge 0.9$

<div class="light-margin"></div>

3\. Evaluate T1 Error

$$
\begin{aligned}
\alpha &= P(\text{rejeect} \; H_0 \mid \mu = 190) \\
&= P \left( \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}} > z_{\alpha} \right) \\
\end{aligned}
$$

위의 식은 어떤 $n$을 선택하더라도 항상 참인 명제다!

<div class="light-margin"></div>

4\. Evaluate T2 Error

power at $\mu = \mu_1 \ge 0.9 = 1 - \beta$.

$$
P \left( \text{reject}\; H_0 \mid \mu = \mu_1 \right)
= P \left( \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}} > z_{\alpha} \mid \mu = \mu_1 \right) \ge 1 - \beta
$$

Now, let's find $n$ which guarantees the eq. of (3) and (4).

$$
\begin{aligned}
P \left( \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}} < z_{\alpha} \mid \mu = \mu_1 \right) 
&\le \beta \\
P \left( \frac{\bar{X} - \mu_1 + \mu_1 - \mu_0}{\sigma/\sqrt{n}} < z_{\alpha} \mid \mu = \mu_1 \right) 
&\le \beta \\
P \left( z < z_{\alpha} - \frac{\mu_1 - \mu_0}{\sigma/\sqrt{n}} \mid \mu = \mu_1 \right) 
&\le \beta
\end{aligned}
$$

이때, $\mu_1 > \mu_0$ and $n$ is large, 

$$
z_{\alpha} - \frac{\mu_1 - \mu_0}{\sigma/\sqrt{n}} < 0
$$

More specifically,

$$
z_{\alpha} - \frac{\mu_1 - \mu_0}{\sigma/\sqrt{n}} < - z_{\beta}
$$

Then, if we solve the above inequality, then we get a inequality for sample size $n$!

$$
n \ge \left( \frac{(z_\alpha + z_\beta) \sigma }{\mu_1 - \mu_0} \right)^2
$$

<div class="light-margin"></div>

💥 If $H_1$ is a form fo $H_1: \mu \ne \mu_0$ at the level $\alpha$, and we want the power at $\mu = \mu_1$ to be at least $1 - \beta$?

이 경우에는 식이

$$
n \ge \left( \frac{(z_{\alpha/2} + z_\beta) \sigma }{\mu_1 - \mu_0} \right)^2
$$

가 된다!

<hr/>

이어지는 포스트에서는 평균(mean)이 아닌, 비율(proportion)과 분산(variance)에 대한 검정을 살펴본다!

👉 [Test on Proportion and Variance]({{"/2021/05/27/test-on-proportion-and-variance.html" | relative_url}})