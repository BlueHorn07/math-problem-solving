---
title: "Chi-square Goodness-of-fit Test"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Introduction to Goodness-of-fit Test
- Test on Independence
- Test on Homogeneity

<hr/>

### Introduction to Goodness-of-fit Test

\<**Goodness-of-fit Test; 적합도 검정**\>은 population distribution이 categorical variable을 가지는 경우, 예를 들어 Head-Tail의 동전 던지기, 주사위 던지기 등에서 사용하는 검정 기법이다. \<Goodness-of-fit Test\>는 카테고리 변수에 대한 Sample Distribution <small>(또는 Observed Distribution)</small>이 우리가 가정한 Expected Distribution과 일치하는지를 결정한다.

먼저 아래의 예제를 풀면서, \<**Goodness-of-fit Test; 적합도 검정**\>에 대해 살펴보자.

<div class="img-wrapper">
<img src= "{{"/images/probability-and-statistics/goodness-of-fit-test-1.png" | relative_url }}" width=650>
</div>

<div class="statement" markdown="1">

1\. 문제 상황

- $H_0: p=0.8$
- $H_1: p \ne 0.8$
- significance level $\alpha$

2\. 샘플링 상황

|-|made|missed|total|
|:---:|:---:|:---:|:---:|
|observed|70|30| 100 | 
|expected <br/>under $H_0$| 80 | 20 | 100 |

3\. Test Statistic

이제 검정을 수행하기 위한 \<Test Statistics\>을 결정하자. 우리는 $\hat{p}$를 사용한다.

그리고 CLT를 적용하면, 아래와 같다.

$$
\frac{\hat{p} - p}{\sqrt{p(1-p) / n}} \sim N(0, 1)
$$

이때, 우리는 이전의 \<Test on Proportion\>에서 수행한 것과 달리 아래의 기준으로 $H_0$를 reject 할 것이다.

$$
\text{reject} \; H_0 \quad \text{if} \quad \left| \frac{\hat{p} - p}{\sqrt{p(1-p) / n}}\right|^2 > \left| z_{\alpha/2}\right|^2 = \chi^2_{\alpha}(1)
$$

여기서 잠깐! 위의 식을 약간 변형해 \<Goodness-of-fit\>의 식을 유도해보자.

<div class="math-statement" markdown="1">

$$
\begin{aligned}
\left| \frac{\hat{p} - p}{\sqrt{p(1-p) / n}}\right|^2
&= \frac{(\hat{p} - p)^2}{p(1-p)/n} = \frac{(x/n - p)^2}{p(1-p)/n} \\
&= \frac{(x/n - p)^2 \times n^2}{p(1-p)/n \times n^2} = \frac{(x - np)^2}{np(1-p)}
\end{aligned}
$$

여기서 우변의 식을 $\frac{1}{y(1-y)} = \frac{1}{y} + \frac{1}{1-y}$를 이용해 아래와 같이 분해한다.

$$
\begin{aligned}
\frac{(x - np)^2}{np(1-p)}
&= \frac{(x-np)^2}{np} + \frac{(x-np)^2}{n(1-p)}
\end{aligned}
$$

이때, $np$는 첫번째 expected value인 $e_1 = 80$이고, $n(1-p)$는 두번째인 $e_2 = 20$이다.

마찬가지로, $(x-np)^2$는 observed value와 expected value의 차이로 표현할 수 있다.

$$
(x-np)^2 = (o_1 - e_1)^2
$$

또, $(x-np)^2$의 경우, 아래와 같이 표현하면, 두번째 observed value와 expected value의 차이로 표현할 수 있다.

$$
(x-np)^2 = (x-n + n-np)^2 = (o_2 - e_2)^2
$$

그래서 식을 종합하면 아래와 같다.

$$
\left| \frac{\hat{p} - p}{\sqrt{p(1-p) / n}}\right|^2 = \frac{(o_1 - e_1)^2}{e_1} + \frac{(o_2 - e_2)^2}{e_2}
$$

</div>

그래서 rejection criterion을 다시 쓰면,

$$
\text{reject} \; H_0 \quad \text{if} \quad \sum_{i=1}^2 \frac{(o_i - e_i)^2}{e_i} > \chi^2_{\alpha}(1)
$$

</div>

위의 예제에서 살펴본 것을 다시 기술해보자.

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> Test Statistics for Goodness-of-fit<br>

\<Goodness-of-fit\>의 Test Statistic은 

$$
\chi^2 := \sum_{i=1}^k \frac{(o_i - e_i)^2}{e_i}
$$

where $o_i$ and $e_i$ are the observed and expected frequencies respectively.

💥 NOTE: <span style="color: red">all expected frequencies must be at least 5</span>. <small>만약, 5 이하의 빈도를 가지는 카테고리가 있다면, 우리는 그것을 다른 카테고리에 합치는 **pooling**을 수행할 것이다!</small>

</div>

위의 예제에서는 카테고리가 단 2개인 상황이었다. 하지만, 주사위 굴리기와 같이 카테고리가 여러 개인 경우는 $\chi^2$의 DOF가 달라진다. 그 공식은 아래와 같다.

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> Dgree of Freedom for Goodness-of-fit<br>

The degree of freedom $\nu$ = (#. of categories after pooling - 1) - #. of parameters estimated

</div>

<hr/>

### Test for Independence

우리는 \<Chi-squared goodness-of-fit Test\>를 응용해 두 개의 카테고리가 서로 독립(independent)한지 검정할 수 있다!

(바빠서 생략)

<hr/>

### Test for Homogeneity

(바빠서 생략)

<hr/>

