---
title: "Single Sample Estimation: Proportion Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr/>

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

이어지는 포스트에서는 두 개 샘플에서 proportion의 차이를 추정하는 방법에 대해 다룬다.

👉 [Two Samples Estimation: Diff btw Two Proportions]({{"/2021/05/16/two-samples-estimation-diff-btw-two-proportions.html" | relative_url}})

