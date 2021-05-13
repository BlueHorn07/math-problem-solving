---
title: "Prediction & Tolerance Estimation"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- [Prediction Interval](#prediction-interval)
- [Tolerance Interval](#tolerance-interval)

<hr/>

### Prediction Interval

Supp. the data points $x_1, x_2, \dots, x_n$ are drawn from $M(\mu, \sigma^2)$ with knwon $\sigma^2$. Now, we draw one more data point $x_0$. Can we estimate where this data point can be?

Q. Infd a confidence interval of the new observation $x_0$ by using data points $x_1, \dots, x_n$.

(가정) Here, assume $X_1, \dots, X_n$ follows iid normal $N(\mu, \sigma^2)$, and the new observation $X_0 \sim N(\mu, \sigma^2)$ and $X_0 \perp X_i$.

먼저, 우리는 아래와 같은 분포를 생각해볼 수 있다.

$$
(X_0 - \bar{X}) \; \sim \; N(0, \; \sigma^2 + \frac{\sigma^2}{n})
$$

위의 분포를 바탕으로 Confidence Interval을 구하면,

$$
\begin{aligned}
1 - \alpha 
&= P \left(-z_{\alpha/2} \le \frac{X_0 - \bar{X}}{\sqrt{\sigma^2 + \frac{\sigma^2}{n}}} \le z_{\alpha/2} \right) \\
&= P \left(\bar{X} - z_{\alpha/2} \cdot \sqrt{\sigma^2 + \frac{\sigma^2}{n}} \le X_0  \le \bar{X} + z_{\alpha/2} \cdot \sqrt{\sigma^2 + \frac{\sigma^2}{n}} \right)
\end{aligned}
$$

💥 만약 $\sigma^2$을 모르는 상황이라면, 위의 식에서 Z-score 부분은 t-value로 바꿔주면 된다!!

<hr/>

### Tolerance Interval

Now, our interest is <u>the proportion of the distribution</u> where is the large bulk of our distribution.

Q. Let $X \sim N(\mu, \sigma^2)$, can you find interval which contains 95% of the distribution?

<div class="light-margin">

[$\mu$ and $\sigma^2$ both are known]

$$
\begin{aligned}
0.95
&= P\left( -z_{0.025} \le N(0, 1) \le z_{0.025} \right) \\
&= P\left( -z_{0.025} \le \frac{X - \mu}{\sigma/\sqrt{n}} \le z_{0.025} \right) \\
&= P\left(\mu - z_{0.025} \cdot \frac{\sigma}{\sqrt{n}} \le X \le \mu + z_{0.025} \cdot \frac{\sigma}{\sqrt{n}} \right)
\end{aligned}
$$

</div>

<div class="light-margin" markdown="1">

[$\mu$ and $\sigma^2$ both are <span style="color:red">unknown</span>]

만약 분포의 두 파라미터 $\mu$, $\sigma^2$에 대한 정보가 없다면, 우리는 <span class="half_HL">$L(X_1, \dots, X_n)$ and $U(X_1, \dots, X_n)$ s.t. $(L, U)$ contains 95% of population with $100(1-\gamma)\%$ confidence</span>라는 두 \<statistics\>를 추정해줘야 한다!! 😲

$$
P \left( F(U) - F(L) \ge 1 - \alpha \right) = 1 - \gamma
$$

where $F$ is the CFD of $N(0, 1)$.

만약 우리가 population $\mu$, $\sigma^2$를 정확히 안 다면, 아래의 Interval을 사용했을 것이다.

$$
\mu \pm 1.96 \cdot \sigma
$$

그러니가 우리는 $\mu$, $\sigma^2$를 알지 못하기 때문에, sample mean $\bar{x}$, sample variance $s$를 써야만 한다!! 그래서 sample로부터 추정한 분포에서 95%를 커버하는 범위는 아래와 같을 것이다.

$$
\bar{x} \pm k \cdot s
$$

위의 범위는 전체 observation을 적어도 $1-\alpha$ 만큼 커버하는, 신뢰도 $100\cdot(1-\gamma)\%$의 범위다!

이 $k$ 값은 \<Tolerance Table\>을 통해 구하면 된다. 아래는 테이블의 예시다.

👉 [Tolerance Table](http://www.bessegato.com.br/UFJF/resources/tolerance_table.pdf)

값은 아래의 3가지 파라미터로 구하면 된다. 

- Confidence Level of interval: $1-\gamma$
- Percent Coverage: $1-\alpha$
- sample size: $n$

</div>

<hr/>

이어지는 포스트에서는 "두 가지 샘플이 존재하는 상황"을 다룬다. 주로 두 샘플의 평균의 차 $(\mu_1 - \mu_2)$를 추정한다. 또, 두 샘플의 분산의 비율 $\sigma_1^2 / \sigma_2^2$을 추정하기도 한다.

👉 [Two Samples Estimation - Diff btw two means]({{"/2021/05/13/two-samples-estimation-diff-btw-two-means.html" | relative_url}})