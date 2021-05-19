---
title: "Introduction to Hypothesis Tests"
layout: post
use_math: true
tags: ["Statistics"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Statistical Hypothesis
- Null Hypothetsis $H_0$ & Alternative Hypothesis $H_1$
- Test Statistics
  - Rejection Region or Critical Region
  - Critical Value
- Type 1 Error & Type 2 Error
- Significance level; Size of Test; 유의 수준 🔥
- Power of Test; 검정력 🔥
- p-value 🔥

<hr/>

<span class="statement-title">Definition.</span> Statistical Hypothesis<br>

A \<**statistical hypothesis**\> is a <span class="half_HL">statement about the population distribution</span>, usually, in terms of the parameter values.

<span class="statement-title">Example.</span><br>

Supp. we have a p-coin, I belive that it is a fair coin, on the other hand, you think it is a biased coin, in particular, you believe that $p=0.7$. What can we do?

- $H_0: p = 0.5$
- $H_1: p = 0.7$

<br/>

<span class="statement-title">Definition.</span> Null Hypothetsis $H_0$ & Alternative Hypothesis $H_1$<br>

- Null Hypothetsis $H_0$: a hypothesis we expect to reject
- Alternative Hypothesis $H_1$: a hypothesis we set out to prove

<div class="statement" markdown="1">

Q. How do we do \<Hypothesis test\>?

A. First, we should set a \<test statistics\>!

Let's toss a coin $n$-times independently. For each toss, let $X_i$ are $1$ for head and $0$ for otherwise.

Then, $X := \sum X_i$, the num. of heads in $n$ tosses be $X \sim \text{BIN}(n, p)$.

Then, we can use $X$ as a \<test statistics\>!

</div>

우리는 이 \<**test statistics**\>로 가설 $H_0$를 reject 하거나 reject 하지 않을 것이다!

위의 $H_0: p=0.5$, $H_1: p=0.7$의 경우에서 생각해보자면, 우리는 $X$가 large enough, 즉 "$X \ge C$ for some $C$"라면, $H_0$를 reject 하는게 합리적이다.

우리는 이 $H_0$를 reject하는 기준이 되는 범위 $X \ge C$를 \<**rejection region**\> 또는 \<**critical region**\>이라고 하며, 이 범위를 잡을 때 쓰는 값 $C$를 \<**critial value**\>라고 한다!

<hr/>

<big>Q. How to choose $C$?</big>

\<critical value\> $C$의 값을 잡기 위해서는 \<Type 1 Error\>, \<Type 2 Error\>를 살펴봐야 한다.

| | reject $H_0$ | not reject $H_0$ |
|:---:|:---:|:---:|
|$H_0$ is true | <span class="half_HL">Type 1 Error</span> | good|
|$H_0$ is false | good | <span class="half_HL">Type 2 Error</span>|

<div align="center">

"It's best if we can make T1 & T2 errors as small as possible."

</div>

<div class="light-margin" markdown="1">

<span class="statement-title">Case.</span> Type 1 error<br>

$$
\begin{aligned}
P(\text{T1 error})
&= P(\text{reject} \; H_0 \mid H_0 \; \text{is true}) \\
&= P(X \ge C \mid p = 0.5)
\end{aligned}
$$

이때, $P(T1)$을 최대한 줄이려면, $C$를 최대한 키워서 웬만한 경우가 아니면 $X$가 $X \ge C$의 조건을 만족시키지 못 하도록 만들면 된다.

</div>

<div class="light-margin" markdown="1">

<span class="statement-title">Case.</span> Type 2 error<br>

$$
\begin{aligned}
P(\text{T2 error})
&= P(\text{not reject} \; H_0 \mid H_1 \; \text{is true}) \\
&= P(X < C \mid p = 0.7)
\end{aligned}
$$

이때, $P(T2)$를 최대한 줄이려면, $C$를 최대한 줄여서 웬만한 경우가 아니면 $X$가 $X < C$의 조건을 만족시키지 못하도록 만들면 된다.

</div>

?? 뭔가 이상하다. $P(T1)$를 줄이려면, $C$를 키워야 하고, $P(T2)$를 줄이려면, $C$를 줄여야 한다. 😕 뭐가 맞는 걸까?

답은 우리는 $P(T1)$과 $P(T2)$, 둘 중 하나만 가능한 작게 만들 수 있다는 것이다 😱

<div class="light-margin" align="center">

"For a fixed sample size, we can make only one error as small as we want."

</div>

그럼 또다른 질문이 떠오른다. 

<big>Q. $P(T1)$과 $P(T2)$ 중 어느 것을 줄여야 좋을까?</big>

아래의 경우를 생각해보자.

<div class="math-statement" markdown="1">

- $H_0$: 피고 A is innocent
- $H_1$: 피고 A is guilty

이때, T1 & T2 error가 무엇을 의미하는지 잘 보자.

- T1 error: $H_0$가 사실인데, $H_0$를 reject
- T2 error: $H_1$이 사실인데, $H_1$을 reject

두 상황 중 뭐가 더 안 좋을까? 당연히 "T1 error"의 경우다! 왜냐하면, <span class="half_HL">무고한 사람을 유죄라고 선고</span>했기 때문이다!

<br/>

"암 진단"이라는 다른 상황을 생각해본다면, 

- $H_0$: 환자 B는 건강하다.
- $H_1$: 환자 B는 암이 있다.

- T1 error: 사실 환자 B가 건강한데, 암 환자로 진단
- T2 error: 사실 환자 B가 암이 있는데, 건강하다고 진단

이 경우에서도 건강한 사람을 암 환자로 진단해 엄청난 돈을 쓰게 했으니 "T1 error"가 더 안 좋다.

</div>

위와 같은 상황을 바탕으로, 둘 중 하나만 줄일 수 있다면, <span class="half_HL">"T1 error"를 최대한 줄여라</span>는 결론을 얻는다.

그럼 "T2 error"는?? "T2 error"는 운에 맡긴다고 한다 ㅋㅋㅋ

그 이유는 T2 error의 경우, "not reject $H_0$"라는 결과가 나오는데, 이것이 "$H_1$를 accept한다"와는 다른 의미이기 때문이다. 결국 <span class="half_HL">T2 error에서는 $H_0$에 대해서도 $H_1$에 대해서도 어떤 진술도 할 수 없기 때문에</span>, 그나마 괜찮다고 보는 것이다!

<hr/>

<span class="statement-title">Definition.</span> Significance level; size of a test<br>

The probability of committing a \<Type 1 Error\> is called the \<significance level\> and we use $\alpha$ to denote the significance level.

$$
\alpha = P(\text{T1 Err}) = P(\text{reject} \; H_0 \mid H_0 \; \text{is true})
$$

💥 commonly used values for $\alpha$ are $0.1$, $0.05$, $0.01$.

<hr/>

<div class="math-statement" markdown="1">

<span class="statement-title">Example.</span><br>

<div align="center" markdown="1">

$H_0: p=0.5$ vs. $H_1: p=0.7$

</div>

We toss a coin 20 times independently and obtained 14 heads. Test this at $\alpha = 0.0577$.

<span class="statement-title">Solve.</span><br>

Let $X = \sum X_i \sim \text{BIN}(20, p)$.

The critical region is $\\{ X \ge C \\}$.

Here, $\alpha = P(X \ge C \mid p=0.5) = P(\text{BIN}(20, 0.5) \ge C)$.

Then, by the cdf of $\text{BIN}(20, 0.5)$, 

$$
P(\text{BIN}(20, 0.5) \le 13) = 0.9423
$$

Therefore, $C = 14$.

We will reject $H_0$ if num. of heads in 20 tosses is $\ge 14$.

Since $x=14$, we reject $H_0$ at $\alpha = 0.0577$. $\blacksquare$

</div>


<div class="math-statement" markdown="1">

Now, we consider T2 error case! If T2 error is small, then we might accept $H_0$.

<span class="statement-title">Example.</span><br>

(Same situation with the above example)

<span class="statement-title">Solve.</span><br>

$$
P(\text{T2 Err}) = P(X < C \mid H_1 \; \text{is true}) = P(\text{BIN}(20, 0.7) \le C)
$$

We've found that $C=14$ from the privous example. Then,

$$
P(\text{BIN}(20, 0.7) \le 14) = 0.392 \approx 0.4
$$

We fail to reject $H_0$, but we can't accept $H_0$ because not enough statistical evidence to accept it, i.e. $P(T2)$ is high.

</div>

<div class="math-statement" markdown="1">

<span class="statement-title">Example.</span><br>

(Now, everything is same but $H_1: p=0.8$)

<span class="statement-title">Solve.</span><br>

The critical point $C$ is same as the previous one, because $H_0$ doens't change. → $C=14$

Now, T2 Error is

$$
P(\text{T2 Err}) = P(X < 14 \mid p=0.8) = P(\text{BIN}(20, 0.8) < 14>) \approx 0.0867
$$

So, we fail to reject $H_0$, also in this time, we can accept $H_0$!!

</div>

<hr/>

<span class="statement-title">Definition.</span> Power of Test; 검정력<br>

The \<power of a test\> $\gamma(\theta)$ at $\theta=\theta_1$ is defined as the probability of rejection of $H_0$ when $\theta=\theta_1$ is a true value.

$$
\gamma(\theta_1) = P(\text{reject} \; H_0 \mid \theta = \theta_1)
$$

💥 NOTE: $1-P(\text{T2 Err}) = \gamma(\theta_1)$

즉, \<power of test\>는 Null hypo $H_0$가 거짓일 때, $H_0$를 기각시키는 확률이다!

이 \<power of test\>는 아래 상황일 때, 그 값이 커진다.

- \<significance level\> $\alpha$ ▲
- 표본의 크기 $n$ ▲

<hr/>

지금까지 우리는 \<significance level\> $\alpha$ 값에 따라서, \<critical value\> $C$를 구하고, 또 \<critical region\>을 구했다. 그런데 만약 $\alpha$ 값이 주어지지 않았다면, 어떻게 할까??

<span class="statement-title">Definition.</span> p-value<br>

The \<p-value\> of a test is <span class="half_HL">the lowest significance level at which $H_0$ can be rejected</span> with the given data.

즉, $H_0$를 reject 할 수 있는 가장 작은 $\alpha$ 값이 바로 \<p-value\>이다!


<hr/>

이어지는 포스트에선 본격적인 통계 검정을 수행한다.

👉 [Test on Mean]({{"/2021/05/19/test-on-mean.html" | relative_url}})