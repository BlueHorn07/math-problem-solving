---
title: "Sampling Distribution"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- sample mean & sampling distribution
- random sample
- location measures of a sample
  - sample mean
  - sample median
  - sample mode
- variability measures of a sample
  - sample variance 🔥
  - sample standard deviation
  - range
- Distribution of Mean & CLT
- Weak Law of Large Numbers
- CLT; Central Limit Theorem


<hr/>

확통 수업을 듣는 전체 학생을 대상으로, 확통 수업을 선호하는 학생의 비율을 구하고자 한다. 그런데, 확통 수업을 듣는 학생 수가 너무 많아서 전체를 조사할 순 없고, 전체 중 $n$명 학생을 대상으로 설문조사를 시행한다고 하자.

$X$가 $n$명의 학생 중에 확통 수업을 선호한다고, 응답한 학생에 대한 RV라면, $X$는 HyperGeo의 분포를 따를 것이다.

또, 만약 전체 학생 수가 충분히 크다면, HyperGeo를 BIN으로 근사할 수도 있을 것이다.

이때, 각 학생 $i$의 선호를 RV $X_i$로 표현해보자. 그러면,

$$
X_i = \begin{cases}
    1 & i\text{-th student likes it!} \\
    0 & \text{else}
\end{cases}
$$

그러면, 전체 RV $X_1, \dots, X_n$를 종합하면, 새로운 RV $\overline{X}$를 유도할 수 있다.

$$
\overline{X} := \frac{X_1 + \cdots X_n}{n}
$$

우리는 이 $\overline{X}$를 \<**sample mean**\>이라고 한다!

위의 예시를 좀더 구체화 해서 생각해보자.

$n=100$, and 60 students said they like lecture. Then, $\overline{x} = \frac{60}{100} = 0.6$

이때, 우리가 \<sample mean\> $\overline{x}$에 대해 논하고자 하는 주제는 바로

$$
P(\left| \overline{x} - 0.6 \right| < \epsilon)
$$

과 같은 확률을 어떻게 구하는지에 대한 것이다. 이것을 구하기 위해서는 $\overline{x}$에 대한 분포를 알아야 하며, 우리는 이것을 \<**sampling distribution**\>이라고 한다!

<hr/>

<span class="statement-title">Definition.</span> population<br>

A \<population\> is the totality of observations.

<span class="statement-title">Definition.</span> sample<br>

A \<sample\> is a subset of population.

<span class="statement-title">Definition.</span> random sample<br>

RVs $X_1, \dots, X_n$ are said to be a \<random sample\> of size $n$, <span class="half_HL">if they are independent and identically distributed as pmf or pdf $f(x)$</span>.


That is, 

$$
f_{(X_1, \dots, X_n)} (x_1, \dots, x_n) = f_{X_1} (x_1) \cdots f_{X_n} (x_n)
$$

The observed values $x_1, \dots, x_n$ of $X_1, \dots, X_n$ are called \<**sample points**\> or \<**observations**\>.

<hr/>

<span class="statement-title">Definition.</span> statistic<br>

A \<statistic\> is a function of a random sample $X_1, \dots, X_n$, <span class="half_HL">not depending on unknown parameters</span>.

<span class="statement-title">Example.</span><br>

Supp. $X_1, \dots, X_n$ is a random sample from $N(\mu, 1)$.

Then, 

1\. $\dfrac{X_1 + \cdots + X_n}{n}$ is a <u>statistic</u>!

2\. $\max \\{ X_1, \dots, X_n \\}$ is a <u>statistic</u>!

3\. $\dfrac{X_1 + \cdots + X_n + \mu}{n}$ is <u>not a statistic</u>!

우리는 \<statistic\>라는 특별한 조건 아래에 있을 때, random sample을 통해 population에 대한 inference를 수행할 수 있다.

<hr/>

#### Location Measures of a Sample

Let $X_1, \dots, X_n$ be a random sample.

<span class="statement-title">Definition.</span> sample mean<br>


$\overline{X} = \dfrac{X_1 + \cdots + X_n}{n}$ is called a \<sample mean\>.

(1) $\overline{X}$ is also a random varaible!

(2) If $E(X_1) = \mu$ and $\text{Var}(X_1) = \sigma^2$, then $E(\overline{X}) = \dfrac{n\mu}{n} = \mu$ and $\text{Var}(\overline{X}) = \dfrac{\sigma^2}{n}$

(3) $\overline{X}$ cab be sensitive to outliers.

<br/>

<span class="statement-title">Definition.</span> sample median<br>

그냥 Sample에서의 중간값을 말함.

<br/>

<span class="statement-title">Definition.</span> sample mode<br>

Sample에서의 최빈값.


<hr/>

#### Variability Measures of a Sample

Let $X_1, \dots, X_n$ be a random sample with $E[X_i] = \mu$ and $\text{Var}(X_i) = \sigma^2$.


<span class="statement-title">Definition.</span> sample variance<br>


$$
S^2 := \frac{1}{n-1} \sum^n_{i=1} \left( X_i - \overline{X}\right)^2
$$

Q. Why $(n-1)$ in the bottom??

A. 왜냐하면, $(n-1)$로 나눠줘야 $E[S^2]$이 $\sigma^2$이 되기 때문!!!

<span class="statement-title">*Proof*.</span><br>

<div class="math-statement" markdown="1">

w.l.o.g. we can assume that $E[X_i] = 0$. (그냥 편의를 위해 $X_i$를 적당히 표준화 했다고 보면 된다.)

$$
\begin{aligned}
S^2 &= \frac{1}{n-1} \sum^n_{i=1} \left( X_i^2 - 2 X_i \overline{X} + (\overline{X})^2 \right) \\
    &= \frac{1}{n-1} \left\{ \sum^n_{i=1} X_i^2 - 2 \overline{X} \sum^n_{i=1} X_i + n (\overline{X})^2 \right\} \\
\end{aligned}
$$

이때, $\displaystyle\sum^n_{i=1} X_i$는 그 정의에 의해 $n\overline{X}$가 된다.

$$
\begin{aligned}
S^2 &= \frac{1}{n-1} \left\{ \sum^n_{i=1} X_i^2 - 2 \overline{X} \cdot n\overline{X} + n (\overline{X})^2 \right\} \\
    &= \frac{1}{n-1} \left\{ \sum^n_{i=1} X_i^2 - n (\overline{X})^2 \right\} \\
\end{aligned}
$$

이제 위의 식의 양변에 평균을 취해보자.

$$
\begin{aligned}
E[S^2] &= \frac{1}{n-1} \left\{ \sum^n_{i=1} E(X_i)^2 - n E\left[(\overline{X})^2\right] \right\} \\
       &= \frac{1}{n-1} \left\{ n \cdot \sigma^2 - n \cdot \frac{1}{n^2} \cdot E \left[(X_1 + \cdots + X_n)^2 \right] \right\} \\
       &= \frac{1}{n-1} \left\{ n \cdot \sigma^2 - \frac{1}{n} \cdot \left( n E[X_1^2] + \cancelto{0}{E[X_i X_j]} + \cdots \right) \right\} \\
       &= \frac{1}{n-1} \left\{ n \cdot \sigma^2 - \frac{1}{\cancel{n}} \cdot \left( \cancel{n} \cancelto{\sigma^2}{E[X_1^2]} \right) \right\} \quad (\text{independence}) \\
       &= \frac{1}{n-1} \left\{ n \cdot \sigma^2 - \sigma^2 \right\} \\
       &= \sigma^2
\end{aligned}
$$

$\blacksquare$

</div>

<br/>

<span class="statement-title">Definition.</span> sample standard deviation<br>

$$
S := \sqrt{S^2} = \sqrt{\frac{1}{n-1} \sum^n_{i=1}\left( X_i - \overline{X} \right)^2}
$$

<br/>

<span class="statement-title">Definition.</span> range<br>

$$
R := \max_{1 \le i \le n} X_i - \min_{1 \le i \le n} X_i
$$

<hr/>

<span class="statement-title">Definition.</span> sample distribution<br>

The <span class="half_HL">probability distribution of a statistic</span> is called a \<sample distribution\>.

ex) distribution of sample mean, distribution of sample variance, ...

#### Sampling Distribution of Means and CLT

Let $X_1, \dots, X_n$ be a random sample with $E[X_i] = \mu$ and $\text{Var}(X_i) = \sigma^2$.

Then,

- $E[\overline{X}] = \mu$
- $\text{Var}(\overline{X}) = E\left[\left(\overline{X} - E[\overline{X}]\right)^2 \right] = \dfrac{\sigma^2}{n}$

이때, \<CLT; Central Limit Theorem\>은 $n$이 무한으로 갈때, $\text{Var}(\overline{X}) = \dfrac{\sigma^2}{n}$이 0이 수렴함을 기술한다. 그리고 이에 따라, $\overline{X} \rightarrow \mu$가 된다.

<hr/>

#### Weak Law of Large Numbers

<span class="statement-title">Theorem.</span> WLLN<br>

Let $X_1, \dots, X_n$ be a random sample with $E[X_i] = \mu$ and $\text{Var}(X_i) = \sigma^2$.

Let $\overline{X} = \dfrac{X_1 + \cdots + X_n}{n}$.

For any $\epsilon > 0$, we have

$$
\lim_{n\rightarrow\infty} P\left(\left| \overline{X} - \mu \right| > \epsilon\right) = 0
$$

<span class="statement-title">*Proof*.</span><br>

<div class="math-statement" markdonw="1">

\<Chebyshev's Inequality\>를 사용하면 아주 쉽게 증명할 수 있다!

$$
\begin{aligned}
P\left(\left| \overline{X} - \mu \right| > \epsilon\right) &\le \frac{\text{Var}(\overline{X})}{\epsilon^2} \\
&= \frac{1}{\epsilon} \cdot \frac{\sigma^2}{n} \rightarrow 0 \quad \text{as} \quad n \rightarrow \infty
\end{aligned}
$$

$\blacksquare$

</div>

<big>"WLLN says that as the sample size $n$ gets larger, then the sample mean is close to the true mean in probability!"</big>

이때, WLLN과 같은 형태의 수렴을 <span class="half_HL">"the convergence in probability"</span>라고 한다.

cf) 참고로 \<Strong Law of Larger Numbers\>도 존재한다. 그러나 이 정리를 증명하려면, 측도(measure)에 대한 개념이 필요하기 때문에 소개만 하고 넘어가겠다.

$$
P\left(\lim_{n\rightarrow\infty} \overline{X} = \mu \right) = 1
$$

<hr/>

#### CLT; Central Limit Theorem

<span class="statement-title">Example.</span><br>

What is the probability of $P\left( \overline{X} > 7\right)$?

Note that $X_1, \dots, X_n \sim \text{Ber}(p)$, and then $(X_1 + \cdots + X_n) \sim \text{BIN}(n, p)$. 

When $n$ is larget, then $(X_1 + \cdots + X_n) \rightarrow N(\mu, \sigma^2)$.

Let's standardize it, then

$$
P\left( \frac{(X_1 + \cdots + X_n) - np}{\sqrt{npq}} \le z \right) \approx P(Z \le z)
$$

이때, 좌변의 분모/분자에 $n$를 나줘주면

$$
P\left( \frac{((X_1 + \cdots + X_n) - np)/n}{(\sqrt{npq})/n} \le z \right) = P\left( \frac{\frac{(X_1 + \cdots + X_n)}{n} - p}{\sqrt{\frac{pq}{n}}} \le z \right) = P\left( \frac{\overline{X} - E[\overline{X}]}{\sqrt{\text{Var}(\overline{X})}} \le z \right) \approx P(Z \le z)
$$

그래서 결론은, 원래 문제였던 $P\left(\overline{X} > 7\right)$을 잘 정규화해서 normal 분포로 근사하여 풀면 된다는 것이다. 그런데, 지금의 경우는 $\overline{X}$가 BIN 분포였기 때문에 \<Noarml Approximation\>에 의해 자연스럽게 유도된 것이었다. 과연 $\overline{X}$ 또는 $X_i$가 다른 분포를 가져도 위와 같은 방식을 풀 수 있을까? 이 의문에 대한 답을 제시하는 것이 바로 \<CLT; Central Limit Theorem\>이다 🤩

<br/>

<span class="statement-title">Theorem.</span> CLT; Central Limit Theorem<br>

Let $X_1, \dots, X_n$ be a random sample with $E[X_i] = \mu$ and $\text{Var}(X_i) = \sigma^2$.

Let $\overline{X}_n := \dfrac{X_1 + \cdots + X_n}{n}$.

Let $Z_n := \dfrac{\overline{X}_n - E[\overline{X}]}{\sqrt{\text{Var}(\overline{X})}} = \dfrac{\overline{X}_n - \mu}{\frac{\sigma}{\sqrt{n}}}$.

then, for any $z \in \mathbb{R}$, we have

$$
P(Z_n \le z) \rightarrow P(Z \le z) \quad \text{as} \quad n \rightarrow \infty
$$

where $Z \sim N(0, 1)$.

<span class="statement-title">Remark.</span><br>

1\. As long as i.i.d. RVs have finite second moment[^1], then we have CLT.

이것이 의미하는 바는 아주 강력하다 💥 바로 $X_i$가 어떤 분포를 따르는 상관없이 CLT를 적용할 수 있다는 말이기 때문이다!! 이런 점 때문에 CLT를 <span class="half_HL">"universal result"</span>라고 한다!

<br/>

2\. We call $z: = \dfrac{\overline{x} - \mu}{\sigma / \sqrt{n}}$ as \<$z$-value\> or \<$z$-score; $z$-점수, 표준 점수\>, we define $z_\alpha$ as the number $x$ s.t. $P(Z \ge x) = \alpha$ when $Z \sim N(0, 1)$.

<div class="img-wrapper">
<img src="https://upload.wikimedia.org/wikipedia/commons/2/25/The_Normal_Distribution.svg" height="400px">
</div>

\<CLT\>에 대한 증명은 추후에 제시하도록 하겠다!

<hr/>

[^1]: 그냥 finite variance를 가진다는 말이다.

