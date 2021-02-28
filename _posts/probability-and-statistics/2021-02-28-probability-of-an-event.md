---
title: "Probability of an Event"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>


<hr/>

### Probability

<br><span class="statement-title">Definition.</span> Probability of an event $A$; $P(A)$<br>

Let $S$ be a sample space. The probability of an event $A$ is the sum of the probabilities of all sample points in $A$.

And there are following properties:

1. $0 \le P(A) \le 1$ for every event $A$
2. $P(S) = 1$
3. If $A \cap B = \emptyset$, then $P(A \cup B) = P(A) + P(B)$
4. If $A_1$, $A_2$, ... is a sequence of mutually exclusive events, then $P(A_1 \cap A_2 \cap \cdots) = P(A_1) + P(A_2) + \cdots$

<br><span class="statement-title">Term.</span> Equally likely outcomes<br>

\<Equally likely outcomes\> mean that each element in the sample space occurs with equal chance.

Under this circumstance, if $S = \\{ x_1, \dots, x_N \\}$ so that $\left\| S \right\| = N$, then we define $P(A) := \dfrac{\left\| A \right\|}{N}$.

<hr/>

### Additive Rule

<br><span class="statement-title">Theorem.</span><br>

For any two events $A$ and $B$,

$P(A \cup B) = P(A) + P(B) - P(A \cap B)$

<br><span class="statement-title">proof.</span><br>

Exercise

// 본인은 "probability"를 계산할 때, 그 event에 속한 sample point의 "probability"를 합한다고 생각함. 그런데 만약 $P(A) + P(B)$만 하게 되면, $A \cap B$에 속하는 sample point의 확률을 중복해서 더하는 꼴이 되기 때문에 이것을 제외해줘야 한다고 생각함.

<br><span class="statement-title">Topic.</span> Matching Problem<br>

> 수학 시험에서 3명의 학생들이 자신들이 친 시험지를 채점한다고 한다. 선생은 학생들이 자기 자신의 시험지를 채점하지는 않도록 하고 싶다. 그 확률은 어떻게 되는가?

// 본인은 처음 문제를 풀었을 때, 틀렸었다 ㅠㅠ

<hr/>

### Conditional Probability

<br><span class="statement-title">Defitnition.</span> Conditional Probability<br>

The **conditional probability** of $B$, given $A$, denoted by $P(B \mid A)$, is defined by

$$
P(B \mid A) = \frac{P(B \cap A)}{P(A)}, \quad \mbox{provided} \; P(A) > 0
$$

> "The notion of conditional probability provides the capability of reevaluating the idea of probability of an event in light of additional information"

> The probability $P(A \mid B)$ is an updating of $P(A)$ based on the knowledge that event $B$ has occured.

#### Independent Events

<br><span class="statement-title">Definition.</span> Independent<br>

Two events $A$ and $B$ are **independent** if and only if

$$
P(B \mid A) = P(B) \quad \mbox{or} \quad P(A \mid B) = P(A)
$$

assuming the existences of the conditional probabilites.

Otherwise, $A$ and $B$ are **dependent**.

> If two events $A$ and $B$ are independent, then the occrurence of  $B$ had no impact on the odds of occurence of $A$.

<hr/>

### Product Rule

<br><span class="statement-title">Theorem.</span><br>

If an experiment the events $A$ and $B$ can both occur, then

$$
P(A \cap B) = P(A) P(B \mid A), \quad \mbox{providied} \; P(A) > 0
$$

Codntional Probability와 함께 Product Rule의 의미를 곱씹어 보자.

$P(A \cap B)$가 $P(A)$와 $P(B \mid A)$의 곱으로 표현된다고 한다. 즉, "$A$가 발생할 확률" $P(A)$에 "$A$가 발생했을 때, $B$가 발생할 확률 $P(B \mid A)$"를 곱해주는 거다. 

다시 말하면, 두 사건 $A$, $B$에 대해, 그 둘이 동시에 발생하는 사건 $A \cap B$를 $A$ 발생 후 $B$가 발생한 사건으로 해석하는 셈이다. 이때, $A$가 발생했다면, 그 정보를 사건 $B$ 발생에 반영해야 하기 때문에 $P(B \mid A)$라는 conditional probability를 도입한 것이다.


<br><span class="statement-title">Theorem.</span><br>

Two events $A$ and $B$ are **independent** if and only if

$$
P(A \cap B) = P(A) P(B)
$$

<br><span class="statement-title">Notation.</span> $A \perp B$<br>

When two events $A$ and $B$ are **independent**, we denote it as

$$
A \perp B
$$

