---
title: "Sampling Distribution of Variance"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Sampling Distribution of the difference btw two mean
- Sampling Distribution of $S^2$

<hr/>

### Sampling Distribution of the difference btw two mean

이번에는 두 개의 서로 population에서 뽑은 두 independent sample을 생각해보자!

Let $X_1, \dots, X_{n_1}$, and $Y_1, \dots, Y_{n_2}$ be two independent random samples with $E[X_1] = \mu_1$, $\text{Var}(X_1) = \sigma_1^2$, and  $E[X_2] = \mu_2$, $\text{Var}(Y_2) = \sigma_2^2$.

우리는 "두 샘플 평균의 차" $\mu_1 - \mu_2$에 대한 inference를 수행하고자 한다. 이때, $\overline{X} - \overline{Y}$를 사용하면 "두 샘플 평균의 차"에 대해 추론할 수 있다!!

By CLT,

$$
\begin{aligned}
    \frac{\overline{X} - \mu_1}{\frac{\sigma_1}{\sqrt{n_1}}} \sim N(0, 1) \quad & \iff \quad \overline{X} \sim N\left(\mu_1, \frac{\sigma_1^2}{n_1}\right) \\
    \frac{\overline{Y} - \mu_2}{\frac{\sigma_2}{\sqrt{n_2}}} \sim N(0, 2) \quad & \iff \quad \overline{Y} \sim N\left(\mu_2, \frac{\sigma_2^2}{n_2}\right)
\end{aligned}
$$

따라서, $\overline{X} - \overline{Y}$에 대한 분포는 independent한 두 normal distribution에 대한 덧셈으로 쉽게 유도할 수 있다!

$$
\overline{X} - \overline{Y} \sim N\left( \mu_1 - \mu_2, \; \frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2} \right)
$$

위의 사실을 이용해서, "두 샘플 평균의 차"에 대한 추론도 쉽게 수행할 수 있다 😉

<hr/>

### Sampling Distribution of $S^2$

Let $X_1, \dots, X_n$ be a random sample with $\text{Var}(X_i) = \sigma^2$. We already know that $E[S^2] = \sigma^2$. How about the distribution of $\displaystyle S^2 = \dfrac{1}{n-1} \sum^n_{i=1} (X_i - \overline{X})^2$?

가장 간단한 경우인, $n=2$인 경우를 살펴보자. 이때, $\overline{X} = \dfrac{X_1 + X_2}{2}$이다. 이때, $Y_i := X_i - \overline{X}$라고 둔다면,

$$
\begin{aligned}
    Y_1 = X_1 - \overline{X} = \frac{X_1 - X_2}{2} \\
    Y_2 = X_2 - \overline{X} = \frac{X_2 - X_1}{2} \\
\end{aligned}
$$

즉, $Y_1 = - Y_2$로 서로 dependent다! 그래서 $S^2$에 대해서는 CLT를 적용할 수가 없다 😥 그러나 아래의 정리를 잘 활용하면, $S^2$에 대한 Distribution을 유도할 수 있다!!

<br/>

<span class="statement-title">Note.</span><br>

Let $X_1, \dots, X_{n_1}$ be randome sample from $N(\mu, \sigma^2)$.

1\. $\overline{X} \sim N\left( \mu, \frac{\sigma^2}{n}\right)$

2\. $\displaystyle\sum^n_i \left( \frac{X_i - \mu}{\sigma} \right)^2 \sim \chi^2(n)$

<span class="statement-title">Theorem.</span> Sampling Distribution of $S^2$<br>

Let $X_1, \dots, X_{n_1}$ be randome sample from $N(\mu, \sigma^2)$, then

$$
\frac{(n-1)S^2}{\sigma^2} = \sum^n_{i=1} \left( \frac{X_i - \overline{X}}{\sigma}\right)^2 \sim \chi^2 (n-1)
$$

"We lose one degree of freedom, because we estimate a parameter $\mu$ by $\overline{X}$."

<span class="statement-title">*Proof*.</span><br>

<div class="math-statement" markdown="1">

$$
\begin{aligned}
\frac{1}{\sigma^2} \sum^n_i \left( X_i - \mu \right)^2 &= \frac{1}{\sigma^2} \sum^n_{i=1} (X_i - \overline{X} + \overline{X} - \mu)^2 \\
&= \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2 + \frac{1}{\sigma^2} \sum^n_i (\overline{X} - \mu)^2 + \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})(\overline{X} - \mu)
\end{aligned}
$$

이때, 마지막 텀인 $\displaystyle \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})(\overline{X} - \mu)$를 살펴보자.

$$
\begin{aligned}
\frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})(\overline{X} - \mu) &= \frac{1}{\sigma^2} \cdot (\overline{X} - \mu) \cdot \sum^n_i (X_i - \overline{X}) \\
&= \frac{1}{\sigma^2} \cdot (\overline{X} - \mu) \cdot \cancelto{0}{(X_1 + \cdots + X_n - n\overline{X})} \\
&= 0
\end{aligned}
$$

다시 원래의 식으로 돌아가서

$$
\begin{aligned}
\frac{1}{\sigma^2} \sum^n_i \left( X_i - \mu \right)^2 
&= \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2 + \frac{1}{\sigma^2} \sum^n_i (\overline{X} - \mu)^2 + \cancelto{0}{\frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})(\overline{X} - \mu)} \\
&= \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2 + \frac{1}{\sigma^2} \sum^n_i (\overline{X} - \mu)^2 \\
&= \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2 + \frac{n(\overline{X} - \mu)^2}{\sigma^2} \\
&= \frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2 + \left( \frac{\overline{X} - \mu}{\frac{\sigma}{\sqrt{n}}}\right)^2 \\
\end{aligned}
$$

이때, 좌변의 $\displaystyle \frac{1}{\sigma^2} \sum^n_i \left( X_i - \mu \right)^2$는 $\chi^2(n)$의 분포를 따르고, 우변의 $\displaystyle \left( \frac{\overline{X} - \mu}{\frac{\sigma}{\sqrt{n}}}\right)^2$는 $\chi^2(1)$의 분포를 따른다.

만약 $Z = X + Y$에서 $Z \sim \chi^2(n)$이고, $Y \sim \chi^2(1)$이고, 게다가 $X \perp Y$라면, $X \sim \chi^2(n-1)$가 된다. 그러나 우리는 아직 $X \perp Y$에 대해 언급하지 않았다. 그래서 아래의 Lemma를 통해 $X \perp Y$를 확인해보자.

<div class="statement" markdown="1">

<span class="statement-title">Lemma.</span><br>

Let $X_1, \dots, X_n$ be a random sample from $N(\mu, \sigma^2)$, then $S^2$ and $\overline{X}$ are independent.

In fact, $\overline{X}$ and $(X_1 - \overline{X}, \dots, X_n - \overline{X})$ are independent.

</div>

따라서, 위의 Lemma에 의해 

$$
\frac{1}{\sigma^2} \sum^n_i (X_i - \overline{X})^2  = \frac{(n-1) S^2}{\sigma^2} \sim \chi^2(n-1)
$$

$\blacksquare$

</div>




