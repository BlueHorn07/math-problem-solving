---
title: "Two Samples Estimation: Diff Btw Two Proportions"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr/>

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


