---
title: "Proportion Estimation on Binomial Distribution"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- [Singe Sample Estimation: Proportion Estimation](#singe-sample-estimation-proportion-estimation)
- [Two Samples Estimation: Diff Btw Two Proportions](#two-samples-estimation-diff-btw-two-proportions)

<hr/>

### Singe Sample Estimation: Proportion Estimation

Supp. we have a p-coin. We want to verify that the coin is really a p-coin.

<div class="statement" markdown="1">

✨ Goal: Estimate $p$ based on the sample points!

</div>

<div class="light-margin" markdown="1">

Q1. Which coin estimator can we use for $p$?

A1. Here, we can use $\hat{p} = \dfrac{\text{# of heads}}{\text{# of toss}} = \dfrac{X_1 + \cdots + X_n}{n} = \bar{X}$.

</div>

<div class="light-margin" markdown="1">

Q2. How about 95% confidence interval for $p$?

A2. We can use CLT!!

$$
\frac{\bar{X} - \mu}{\sigma / \sqrt{n}} = \frac{\hat{p} - p}{\sqrt{p(1-p)} / \sqrt{n}} \approx N(0, 1)
$$

then, the confidence interval is

$$
\hat{p} - z_{\alpha/2} \cdot \sqrt{\frac{p(1-p)}{n}} 
\; \le \; p \; \le \; 
\hat{p} + z_{\alpha/2} \cdot \sqrt{\frac{p(1-p)}{n}}
$$

💥 하지만!!! 위의 식은 문제가 있다!! 바로 우리가 $p$를 추정하기 위해 interval을 잡았는데, interval의 좌우변에 또 $p$가 등장한다는 것이다!! 😲

[Solution 1] solve the inequality for $p$.

[Solution 2] replace $p$ by $\hat{p}$ <small>// if $n$ is large, $\hat{p} \rightarrow p$ by LLN</small>

Therefore, we the $n$ is large, 

$$
\hat{p} - z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1-\hat{p})}{n}} 
\; \le \; p \; \le \; 
\hat{p} + z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}
$$

</div>

<hr/>

이번에는 \<Proportion Estimation\>의 Error에 대해 살펴보자. Error는 이전의 Estimation과 마찬가지로 아래와 같이 제시된다.

The error $\left\| \hat{p} - p \right\|$ will note exceed $z_{\alpha/2} \cdot \sqrt{\dfrac{\hat{p}\hat{q}}{n}}$.

Q. How large should the sample size be so that the error is at most $\epsilon$?

이것은 Error에 대한 식을 $n$으로 다시 풀어서 쉽게 유도할 수 있었다.

$$
\begin{aligned}
z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}\hat{q}}{n}} 
&\le \epsilon \\
z_{\alpha/2}^2 \cdot \frac{\hat{p}\hat{q}}{n}
&\le \epsilon^2 \\
n 
&\ge \frac{z_{\alpha/2} \cdot \hat{p}\hat{q}}{\epsilon^2}
\end{aligned}
$$

이때, 위의 식은 문제가 있다!! 바로 sample proportion $\hat{p}$는 우리가 $n$을 결정해 샘플링하기 전에는 그 값을 알 수 없다는 것이다!!!

[Solution 1] Guess $\hat{p}$ or use small size of sample to estimate $p$. From this, we get $\hat{p}$, then use it!

[Solution 2] Consider the worst case, maximum error situation.

$$
z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \le z_{\alpha/2} \cdot \sqrt{\frac{1}{4}\frac{1}{n}} \le \epsilon
$$

$$
n \ge \left( \frac{z_{\alpha/2}}{2\epsilon} \right)^2
$$

<hr/>

### Two Samples Estimation: Diff Btw Two Proportions


<div class="img-wrapper">
<img src= "{{"/images/probability-and-statistics/difference-btw-two-proportions-1.png" | relative_url }}" width=650>
</div>

Select $n_1$: math major, and $n_2$: physics major, independently.

Assume $X_1, \dots, X_{n_1}$ and $Y_1, \dots, Y_{n_2}$ are two independent random samples.

From the sample, we get $\hat{p_1} = \bar{x}$, $\hat{p_2} = \bar{y}$. Then, $\hat{p_1} - \hat{p_2}$ can be estimator for $p_1 - p_2$.

By CLT,

$$
\frac{(\hat{p_1} - \hat{p_2}) - (p_1 - p_2)}{\sqrt{\dfrac{p_1q_1}{n_1} + \dfrac{p_2q_2}{n_2}}} \; \approx \; N(0, 1)
$$

Then, the $100(1-\alpha)\%$ confidence interval for $p_1 - p_2$ is 

$$
\left( (\hat{p_1} - \hat{p_2}) - z_{\alpha/2} \cdot \sqrt{\dfrac{\hat{p}_1\hat{q}_1}{n_1} + \dfrac{\hat{p}_2\hat{q}_2}{n_2}}, \;
(\hat{p_1} - \hat{p_2}) + z_{\alpha/2} \cdot \sqrt{\dfrac{\hat{p}_1\hat{q}_1}{n_1} + \dfrac{\hat{p}_2\hat{q}_2}{n_2}} \right)
$$

<hr/>

이어지는 포스트에서는 sample variance $s^2$로부터 population variance $\sigma^2$를 추정하는 방법에 대해 다룬다.

👉 [Variance Estimation]({{"/2021/05/16/variance-estimation.html" | relative_url}})

