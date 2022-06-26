---
title: "Introduction to Linear Regression"
layout: post
use_math: true
tags: ["Statistics"]
---


2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- [Introduction to Linear Regression](#introduction-to-linear-regression)
- [Simple Linear Regression](#simple-linear-regression)
- [Least Square Method](#least-square-method)

<hr/>

### Introduction to Linear Regression

\<Regression\>을 간단하게 설명하자면, 아래와 같다.

<div class="statement" style="font-size: larger" align="center" markdown="1">

Model the relationship btw $x$ and $y$ <br/>
by finding a function $y = f(x)$ that is a close fit to the data

</div>

<span class="statement-title">Mathematical Model</span>

$$
Y = \beta_0 + \beta_1 x + \epsilon
$$

이때, regression parameter $\beta_0$, $\beta_1$가 unknown이며, 우리는 이것을 sample point로부터 추정(Estimate)할 것이다!

\* $\epsilon$은 error를 대변하며, random variable이다!

<hr/>

### Simple Linear Regression

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> Simple Linear Regression Model<br>

$n$개 sample points를 갖고 있다고 하자: $(x_1, y_1), \dots, (x_n, y_n)$.

$y_i$가 $x_i$에 dependent 하다고 가정한다. 이때, 둘은 random factor에 의해 영향을 받는다. 이 random factor는 $\epsilon_i$로 표현된다.

$$
y_i = \beta_0 + \beta_1 x_i + \epsilon_i
$$

where $\epsilon_i$ are independent random variables with mean 0 and variance $\sigma^2$.

위와 같은 Regression Modeling을 \<**Simple Linear Regression Model**\>이라고 한다!!

</div>


<div class="statement" markdown="1">

<span class="statement-title">Remark.</span><br>

1\. $x_i$ is called the \<predictor\> or \<regressor\>, and <span style="color: red">we assume $x_i$s are non-random.</span>

2\. $y_i$ is called the \<response\>, and it is a random variable with $E[y_i] = \beta_0 + \beta_1 x_i$ and $\text{Var}(y_i) = \sigma^2$.

3\. $\epsilon_i$ is called an \<error\>, and $\sigma^2$ is called the \<**error variance**\>. 🔥

</div>

여기서 우리는 이런 의문이 든다!

Q. 우리는 주어진 data points에 맞는 line $y = \beta_0 + \beta_1 x$를 찾고싶다. 이때, $\beta_0$, $\beta_1$로 가능한 값이 아주 많을 텐데, 어떤 $\beta_0$, $\beta_1$ 값이 좋다고 말할 수 있을까??

우리는 이 "Linear Regression"의 좋은 정도를 표현하기 위해 \<residual\>과 그들의 합인 \<residual sum\>을 정의한다.

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> residual<br>

For a line $\hat{y} = b_0 + b_1 x$, the \<residual\> $e_i$  of a data point $(x_i, y_i)$ is defined to be 

$$
e_i := y_i - \hat{y}_i
$$

</div>

우리는 이 residual을 최소화하는 $b_0$, $b_1$의 값을 찾고 싶다!! 이때, 쓰는 방법이 바로 \<Least Square Method\>다!

<hr/>

### Least Square Method

\<LS Method\>는 최선의 $\beta_0$, $\beta_1$을 얻기 위해 아래의 \<SSE; Sum of Squares of the Errors\>를 최소화하는 $b_0$, $b_1$를 찾고자 한다!

$$
\text{SSE} = \sum_{i=1}^n e_i^2 = \sum_{i=1}^n (y_i - \hat{y}_i)^2 = \sum_{i=1}^n (y_i - b_0 - b_1 x_i)^2
$$

위의 식을 최적화하는 건 정말 간단하다. 그냥 SSE를 $b_0$, $b_1$에 대해 편미분 해서 0이 되는 $b_0$, $b_1$의 값을 찾으면 된다.

Let $f(b_0, b_1) = \text{SSE}$, then

$$
\frac{\partial f}{\partial b_0} = - 2 \sum_{i=1}^n (y_i - b_0 - b_1 x_i) = 0
$$

$$
\frac{\partial f}{\partial b_1} = - 2 \sum_{i=1}^n (y_i - b_0 - b_1 x_i) x_i = 0
$$

먼저, $b_0$에 대한 식부터 정리해보자.

<div class="statement" markdown="1">

$$
\frac{\partial f}{\partial b_0} = - 2 \sum_{i=1}^n (y_i - b_0 - b_1 x_i) = 0
$$

$$
\sum_{i=1}^n (y_i - b_0 - b_1 x_i) = 0
$$

$$
\sum_{i=1}^n y_i = b_0 \sum_{i=1}^n 1 + b_1 \sum_{i=1}^n x_i
$$

양변을 $n$으로 나누면,

$$
\bar{y} = b_0 + b_1 \bar{x}
$$

따라서,

$$
b_0 = \bar{y} - b_1 \bar{x}
$$

$\blacksquare$

</div>

이번에는 $b_1$에 대한 식을 정리해보자.

<div class="statement" markdown="1">

$$
\frac{\partial f}{\partial b_1} = - 2 \sum_{i=1}^n (y_i - b_0 - b_1 x_i) x_i = 0
$$

$$
\sum_{i=1}^n (y_i - b_0 - b_1 x_i) x_i = 0
$$

위의 식에서 아까 구한 $b_0$를 대입해주자!

$$
\sum_{i=1}^n (y_i - \bar{y} + b_1 \bar{x} - b_1 x_i) x_i = 0
$$

$$
\sum_{i=1}^n (y_i - \bar{y} + b_1 (\bar{x} - x_i)) x_i = 0
$$

$$
\sum_{i=1}^n (y_i - \bar{y})x_i + \sum_{i=1}^n b_1 (\bar{x} - x_i) x_i= 0
$$

$$
b_1 \cdot \sum_{i=1}^n (\bar{x} - x_i) x_i= - \sum_{i=1}^n (y_i - \bar{y})x_i
$$

$$
b_1 = - \frac{\sum (y_i - \bar{y})x_i}{\sum (\bar{x} - x_i) x_i}
$$

$$
b_1 = \frac{\sum (y_i - \bar{y})x_i}{\sum (x_i - \bar{x}) x_i}
$$

또는 위의 식을 약간 변형해 아래와 같이 쓰기도 한다.

$$
b_1 = \frac{\sum (y_i - \bar{y})(x_i - \bar{x})}{\sum (x_i - \bar{x}) (x_i - \bar{x})}
$$

이게 가능한 것은 $b_1$에 대한 첫번째 식에서 $\sum (y_i - \bar{y}) \bar{x}$, $\sum (x_i - \bar{x}) \bar{x}$를 빼줄 때, $\sum (y_i - \bar{y}) = \sum (x_i - \bar{x}) = 0$이기 때문이다!!

</div>

다시 잘 정리하면 아래와 같다.

<div class="theorem" markdown="1">

In \<LS method\>, the regression coefficients of $\beta_0$ and $\beta_1$ are estimated by

$$
b_1 = \frac{\sum (y_i - \bar{y})(x_i - \bar{x})}{\sum (x_i - \bar{x}) (x_i - \bar{x})} = \frac{S_{xy}}{S_{xx}}
$$

$$
b_0 = \bar{y} - b_1 \bar{x}
$$

</div>

여기까지 진행하면, 이제 아래와 같은 의문이 든다.

Q. Are $b_1$ and $b_0$ good estimators? 🤔

A. Yes!!

<div class="theorem" markdown="1">

<span class="statement-title">Theorem.</span><br>

$b_1$ and $b_0$ are unibased for $\beta_1$ and $\beta_0$ respectively.

$$
E[b_1] = \beta_1 \quad \text{and} \quad E[b_0] = \beta_0 
$$

</div>


<div class="proof" markdown="1">

<span class="statement-title">*proof*.</span><br>

$$
\begin{aligned}
E[b_1]
&= E \left[ \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{S_{xx}} \right] \\
&= E \left[ \frac{\sum_{i=1}^n (x_i - \bar{x})y_i}{S_{xx}} \right] \\
&= \frac{\sum_{i=1}^n (x_i - \bar{x})E[y_i]}{S_{xx}}
\end{aligned}
$$

식에서 위와 같이 $E[y_i]$가 가능한 이유는 <span style="color: red">$x_i$는 Random Variable이 아니기 때문</span>이다!! 

$$
\begin{aligned}
&= \frac{\sum_{i=1}^n (x_i - \bar{x})E[y_i]}{S_{xx}} \\
&= \frac{\sum_{i=1}^n (x_i - \bar{x})(\beta_0 + \beta_1 x_i )}{S_{xx}} \\
&= \frac{\cancel{\sum_{i=1}^n (x_i - \bar{x})\beta_0} + \sum_{i=1}^n (x_i - \bar{x}) \beta_1 x_i }{S_{xx}} \\
&= \frac{\sum_{i=1}^n (x_i - \bar{x}) \beta_1 x_i }{S_{xx}} \\
&= \beta_1 \cdot \frac{\sum_{i=1}^n (x_i - \bar{x}) x_i }{S_{xx}} \\
&= \beta_1 \cdot \cancelto{1}{\frac{\sum_{i=1}^n (x_i - \bar{x}) (x_i - \bar{x})}{S_{xx}}} \\
&= \beta_1
\end{aligned} 
$$

$\blacksquare$

</div>

<div class="proof" markdown="1">

<span class="statement-title">*proof*.</span><br>

$$
\begin{aligned}
E[\beta_0]
&= E[\bar{y} - b_1 \bar{x}] \\
&= E[\bar{y}] - E[b_1] \cdot \bar{x} \\
&= (\beta_0 + \beta_1 \bar{x}) - \beta_1 \bar{x} \\
&= \beta_0
\end{aligned}
$$

$\blacksquare$

</div>

<div class="statement" markdown="1">

<span class="statement-title">Remark.</span><br>

1\. The derivation of LSEs does not depend on the distribution of $\epsilon_i$.

2\. If $\epsilon_i$s are iid $N(0, \sigma^2)$, then $b_0$ and $b_1$ are the MLEs for $\beta_0$ and $\beta_1$.

3\. $\sum e_i = 0$

4\. $\sum x_i e_i = 0$

(Homework 🎈)

</div>

위의 명제 [3, 4]를 활용해 아래의 등식을 얻을 수 있다.

$$
\sum_{i=1}^n (y_i - \bar{y})^2 = \sum_{i=1}^n (\hat{y}_i - \bar{y})^2 + \sum_{i=1}^n (y_i - \hat{y}_i)^2
$$

이때, 각 텀은 아래와 같다.

$$
\text{SST} = \text{SSR} + \text{SSE}
$$

- SST: Total Sum of Squares
- SSR: the Regression Sum of Squares
- SSE: the Residual Sum of Squares

증명은 마찬가지로 (Homework 🎈)

<hr/>

<div class="definition" markdown="1">

<span class="statement-title">Definition.</span> R-square; 결정 계수<br>

$$
R^2 := 1 - \frac{\text{SSE}}{\text{SST}}
$$

be the "coefficient of determination; 결정 계수".

- $R^2 = 1$ is equivalent to
  - $\text{SSE} = 0$
  - $\hat{y_i} = y_i$ for all inputs
  - Regression model work very well!
- $R^2 = 0$ is equivalent to
  - $\text{SSE} = \text{SST}$
  - $\text{SSR} = 0$
  - $\hat{y}_i = \bar{y}$ for all inputs
  - Regression model outputs a constant.

</div>


<div class="definition" markdown="1">

<span class="statement-title">Remark.</span><br>

1\. $0 \le R^2 \le 1$

2\. $R^2$ represents the proportionate reduction of total variation in $Y$ associated with the use of the variable $X$.

(a) If $R^2=1$, then $SSE = 0$, this means $\hat{y}_i = y_i$.

All observations fall on the line.

(b) If $R^2 = 0$, then $\text{SSE} = \text{SST}$ or $\text{SSR} = 0$.

The fitted regression line is the constant, $\bar{y}$.

</div>

<hr/>

이어지는 포스트에서는 \<Simple Linear Regression\>의 성질을을 이어서 살펴볼 예정이다. \<Linear Regression\>에서 계수 $b_0$, $b_1$의 분포를 살펴보고 이를 통해 검정(Test)을 수행한다. 또, Regression을 통해 얻은 Prediction 결과를 바탕으로 \<Prediction Inference\>를 수행한다!

👉 [Test on Regression]({{"/2021/06/09/test-on-regression.html" | relative_url}})