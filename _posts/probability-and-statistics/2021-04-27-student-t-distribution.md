---
title: "Student's t-Distribution"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

<hr/>

Consider a random sample of size 100 from $N(1, \sigma^2)$ and $\sigma$ is <u>unknown</u>!

이전에는 population variance $\sigma^2$에 대한 값을 정확히 알았다면, 이번에는 $\sigma^2$를 모르는 상태에서 estimation을 진행한다!! 현재 $\sigma^2$에 대해 하는 정보는 $\sigma^2$가 $\chi^2(n)$을 따른다는 것이 전부다.

<span class="statement-title">Definition.</span> Student's $t$-distribution<br>

Let $Z \sim N(0, 1)$, and $V \sim \chi^2(n)$, and $Z \perp V$.

Define $T$ as

$$
T := \frac{Z}{\sqrt{V / n}} \sim \frac{X_1^2 + \cdots X_n^2}{n}
$$

Then, the distribution of $T$ is called \<student's $t$-distribution of $n$ degrees of freedom\>.

<span class="statement-title">Remark.</span><br>

1\. The pdf is 

$$
f(x) = \frac{\Gamma\left(\dfrac{n+1}{2}\right)}{\sqrt{n\pi} \cdot \Gamma\left( \dfrac{n}{2} \right)} \left( 1 + \frac{x^2}{n} \right)^{-\left( \dfrac{n+1}{2}\right)} \quad \text{for} \quad x \in \mathbb{R}
$$

<div class="img-wrapper" style="margin: 10px">
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200525113955/f126.png" height="300px">
</div>

We define $t_\alpha$ as the number $x$ s.t. $P(T \ge x) = \alpha$.


2\. As $n \rightarrow \infty$, 

$$
f(x) = \cancelto{\frac{1}{\sqrt{2\pi}}}{\frac{\Gamma\left(\dfrac{n+1}{2}\right)}{\sqrt{n\pi} \cdot \Gamma\left( \dfrac{n}{2} \right)}} \cancelto{e^{-x^2/2}}{\left( 1 + \frac{x^2}{n} \right)^{-\left( \dfrac{n+1}{2}\right)}} \quad \text{for} \quad x \in \mathbb{R}
$$

<br/>

<span class="statement-title">Theorem.</span><br>

Let $X_1, \dots, X_n$ be a random sample from $N(\mu, \sigma^2)$. Let $T := \dfrac{\overline{X} - \mu}{S / \sqrt{n}}$, then $T$ has a $t$-distribution with $(n-1)$ dof.

<span class="statement-title">*Proof*.</span><br>

<div class="math-statement" markdown="1">

$$
\begin{aligned}
T &= \frac{\overline{X} - \mu}{S / \sqrt{n}} \\
  &= \frac{\overline{X} - \mu}{\sigma / \sqrt{n}} \cdot \frac{\sigma / \cancel{\sqrt{n}}}{S / \cancel{\sqrt{n}}} \\
  &= \dfrac{\left(\dfrac{\overline{X} - \mu}{\sigma / \sqrt{n}}\right)}{S / \sigma}
\end{aligned}
$$

이때, 분자인 $\dfrac{\overline{X} - \mu}{\sigma / \sqrt{n}}$는 $N(0, 1)$의 분포를 따르고, 

분모인 $S / \sigma$는

$$
\frac{S}{\sigma} = \sqrt{\frac{(n-1) \cdot S^2}{\sigma^2}\cdot \frac{1}{(n-1)}}
$$

인데 이때, $\dfrac{(n-1)\cdot S^2}{\sigma^2}$가 $\chi^2(n-1)$를 따르므로, 식을 정리하면,

$$
T = \frac{X}{\sqrt{V/(n-1)}} \quad \text{where} \quad X \sim N(0, 1) \quad \text{and} \quad V \sim \chi^2(n-1)
$$

그리고 Sample Variance와 Sample Mean을 서로 독립이므로, $X \perp V$이다.

따라서, $T$는 dof가 $n-1$인 $t$-distribution이다. $\blacksquare$

</div>

