---
title: "Random Variables and Probability Distriubtions"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Random Variables
- Probability Distributions
  - CDF; Cumulative Distriubtion Function

<hr/>

## Random Variable

<br><span class="statement-title">Definition.</span> Random Variable<br>

A \<random variable\> is a function from $S$ to $\mathbb{R}$ s.t.

$$
X: S \longmapsto \mathbb{R}
$$

Random Variable을 표현하는 규칙으로는

- Random Variable은 대문자로 표기한다. $X$, $Y$, $Z$
- 소문자 $x$는 Random Variable이 가질 수 있는 값(= 치역의 값) 중 하나를 의미한다.

<br/>

만약 Random Variable $X$가 0, 1 둘 중 하나를 택하는 것과 같이 두 값 중 하나를 취하는 function이라면, 이것을 \<Bernoulli Random Variable\>이라고 한다.

<hr/>

### Discrete vs. Continuous

<br><span class="statement-title">Definition.</span> Discrete Sample Space<br>

If a sample space $S$ contains a finite or an unending sequence of possibilities, it is called a \<discrete sample space\>.

<br><span class="statement-title">Definition.</span> Continuous Sample Space<br>

If a sample space $S$ contains an infinite number of possibilities or equal to the number of points on a line segment, it is called a \<continuous sample space\>.

즉, Sample Space $S$의 Cardinality에 따라 "**Discrete**"이냐 "**Continous**"가 나뉜다.

<br/>

<br><span class="statement-title">Definition.</span> Discrete Random Variable<br>

A random variable is called a \<discrete random variable\>, if its set of possible outcomes it **countable**.

<br><span class="statement-title">Definition.</span> Continous Random Variable<br>

A random variable is called a \<continuous random variable\>, if its set of possible outcomes it **uncountable**.

즉, Random Variable의 치역의 Cardinality에 따라  "**Discrete**"이냐 "**Continous**"가 나뉜다.

<hr/>

## Probability Distribution

### Discrete Prability Distribution

> A discrete random variable assumes each of its values with a certain probability.

정리하면, Discrete RV $X$가 가질 수 있는 어떤 값 $x$에 대해, 그것에 대응되는 확률 $P(X = x)$가 어떤 값으로 정해진다는 말임. 그리고 이걸 $f(x)$의 형태로 표현한 것이 바로 \<Probability Distribution\>임.

<br><span class="statement-title">Definition.</span> Probability Mass Function; Probability Distribution<br> 

The set of ordered pairs $(x, f(x))$ is a \<**probability function**\>, \<**probability mass function**\>, or \<**probability distribution**\> of the discrete RV $X$, if for each possible outcome $x$,

1. $$f(x) \ge 0$$
2. $$\sum_x f(x) = 1$$
3. $$P(X = x) = f(x)$$

위와 같은 prabability function $f(x)$는 RV $X$가 $x$에서 갖는 \<확률 probability\>을 출력해준다.

<div class="img-wrapper">
  <img src="{{ "/images/probability-and-statistics/pmf-1.jpg" | relative_url }}" width="320px">
</div>

<br><span class="statement-title">Definition.</span> Cumulative Distribution Function for Discrete RV<br> 

The \<**cumulative distribution function**\> $F(x)$ of a discrete RV $X$ with probability distribution $f(x)$ is

$$
F(x) = P(X \le x) = \sum_{t \le x} f(t), \quad \mbox{for} - \infty < x < \infty
$$

개인적으로 PMF에 $\sum$을 한거라 명칭이 CMF가 되야 하지 않나 싶었는데, 교재에 "CMF"란 용어는 존재하지 않았다. 즉, \<**Cumulative Distribution Function**\>, 이게 맞는 표현이다.

<div class="img-wrapper" style="margin: 10px">
  <img src="{{ "/images/probability-and-statistics/discrete-cdf-1.jpg" | relative_url }}" width="400px">
</div>

앞의 내용을 미리 스포하자면, \<Discrete RV\>와 \<Continuous RV\>에서의 CDF는 다르게 표현된다.

1\. CDF $F(x)$ of a **<u>discrete RV</u>** $X$ with **<u>probability distribution</u>** $f(x)$

$$
F(x) = P(X \le x) = \sum_{t \le x} f(t)
$$

2\. CDF $F(x)$ of a **<u>continuous RV</u>** $X$ with **<u>density function</u>** $f(x)$

$$
F(x) = P(X \le x) = \int^{x}_{-\infty} f(t) \; dt 
$$

<hr/>

### Continuous Prability Distribution

In Continuous RV, we assign a probability of 0 to the event. And tis probability distribution cannot be given in tabular form. <small>(확률 분포를 표로 적을 수 없다.)</small> However, it can be stated as a formula $f(x)$. we call that formula as a \<probability density function\>!

<br><span class="statement-title">Definition.</span> Probability Density Function<br>

The function $f(x)$ is a \<**Probability Density Function**\> (PDF) for the continuous RV $X$, defined over the set of real numbers, if

1. $$f(x) > 0, \quad \mbox{for all } x \in R$$
2. $$\int^{\infty}_{-\infty} f(x) \; dx = 1$$
3. $$P(a < X < b) = \int^b_a f(x) \; dx$$

<div class="img-wrapper" style="margin: 10px">
  <img src="{{ "/images/probability-and-statistics/density-function-1.jpg" | relative_url }}" width="600px">
</div>

<br><span class="statement-title">Definition.</span> Cumulative Distribution Function for Continuous RV<br>

The \<**cumulative distribution function**\> $F(x)$ of a continuuous RV $X$ with density function $f(x)$ is

$$
F(x) = P(X \le x) = \int^x_{-\infty} f(t) \; dt, \quad - \infty < x < \infty
$$

<div class="img-wrapper" style="margin: 10px">
  <img src="{{ "/images/probability-and-statistics/continuous-cdf-1.jpg" | relative_url }}" width="400px">
</div>

Continuous RV에서의 CDF는 적분으로 정의되기 때문에 CDF $F(x)$를 통해 PDF $f(x)$를 얻을 수 있다!!!

$$
f(x) = \frac{dF(x)}{dx}
$$

(단, $F(x)$의 derivative가 존재해야 한다.)

<hr/>

지금까지는 하나의  \<Random Variable\>이 $X$ 하나인 상황을 다뤘다면, 이어지는 내용에선 \<Random Variable\>이 $X$, $Y$ 두 개인 상황을 다룬다! 이것을 \<**Joint Probability Distribution**\>이라고 한다!