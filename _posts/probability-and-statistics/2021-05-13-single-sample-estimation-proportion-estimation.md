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

</div>