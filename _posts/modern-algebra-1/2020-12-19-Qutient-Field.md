---
title: "Quotient Field"
layout: post
use_math: true
tags: ["Modern Algebra1"]
---

### 서론
2020-2학기, 대학에서 '현대대수1' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr>

<span class="statement-title">Motivation</span>.<br>

정수 $\mathbb{Z}$와 유리수 $\mathbb{Q}$에 대해 생각해보자.

정수 $\mathbb{Z}$는 zero-divisor가 없으므로 **<u>Integral Domain</u>**이다. 물론 정수 $\mathbb{Z}$는 **<u>Ring</u>**이기도 하다.

유리수 $\mathbb{Q}$는 Integral Domain과 Ring보다 상위 단계인 **<u>Field</u>**다.

우리는 다른 평범한 Ring-Field 사이와는 달리 정수 $\mathbb{Z}$와 유리수 $\mathbb{Q}$ 사이에 어떤 좋은 관계가 있음을 보여주고 싶다!

앞으로 소개할 방법을 사용하면, Integral Domain인 $\mathbb{Z}$가 Field인 $\mathbb{Q}$에 포함되어 있음을 보일 수 있다! 한번 살펴보자 ㅎㅎ

<hr>

우리가 사용하는 방법을 일반적인 형태로 기술하면 아래와 같다.

<div class="statement" style="text-align: center;">
  Integral Domain $D$를 Quotient Field $F$로 확장
</div>

4가지 단계를 통해 Integral Domain $D$를 Quotient Field $F$로 확장할 수 있다 ㅎㅎ

<br>
<hr>

##### 1. Define element of $F$

For given domain $D$, think of Cartesian Product of it.

$$
D \times D = \{(a, b) \mid a, b \in D\}
$$

우리는 $D \times D$의 원소인 순서쌍 $(a, b)$를 formal quotient $a/b$라고 생각할 것이다.

하지만, $D \times D$를 $F$라고 보기에는 아직 충분치 않다. 그래서 아래와 같은 Equivalent Relation을 정의하자.

<span class="statement-title">Definition</span>.<br>
<div class="statement">
  $$
  (a, b) \sim (c, d) \iff ad = bc
  $$
</div>

$\sim$가 Equiv Relation임을 증명하는 것은 생략하겠다.

Equiv Relation $\sim$에 의해 유도되는 Equiv Class $[(a, b)]$를 생각해보자. 나중에 이것이 바로 우리가 유도할 $F$의 원소가 된다!

아직 $F$를 완전히 유도한 것은 아니다.

<br>
<hr>

##### 2. Define addition & multiplication on $F$

Equiv class $[(a, b)]$에 대해 연산을 아래와 같이 정의하자.

$$
\begin{aligned}
  + &: [(a, b)] + [(c, d)] = [(ad+bc, bd)] \\
  \cdot &: [(a, b)] \,\cdot\, [(c, d)] = [(ac, bd)]
\end{aligned}
$$

이제 위에서 정의한 두 연산이 Well-defined되어 있음을 보여야 한다.

<span class="statement-title">proof</span>.<br>
<div class="math-statement" markdown="1">
  Supp. $[(a, b)] = [(a', b')]$, and $[(c, d)] = [(c', d')]$

  Check $[(ad+bc, bd)] = [(a'd'+b'c', b'd')]$, and $[(ac, bd)] = [(a'c', b'd')]$.
</div>

자세한 증명은 생략한다.

이를 통해 $F$에서 사용할 연산 $+$와 $\cdot$를 정의하였다.

<br>
<hr>

##### 3. Check $(F, +, \cdot)$ is a field

과정 1, 2에서 사용한 것들을 바탕으로 Field $(F, +, \cdot)$를 정의한다.

$(F, +, \cdot)$가 Field임을 확인하기 위해 아래의 3가지 사실을 확인해야 한다.

1. $(F, +)$ is a abelian group
2. $(F, \cdot)$ is a abelian group
3. Ring Distributive Law

위의 3가지 사실을 확인하는 과정은 생략한다.

자! 이제 우리는 Field $(F, +, \cdot)$를 얻게 되었다!

<br>
<hr>

#### Show relationship btw $D$ and $F$

하지만, 아직 Domain $D$와 Field $(F, +, \cdot)$ 사이의 관계에 대해선 명확히 언급한 바가 없다. 이제 이 둘의 관계에 대해 살펴보자.

우리는 Domain $D$가 Field $(F, +, \cdot)$의 Sub-Domain과 동형임을 보일 것이다.

<br>

<span class="statement-title">Lemma</span>.<br>

We will show $D \cong \\{[(d, 1)] \mid d \in D \\}$

즉, $D$와 우항 사이에 Isomorphism $\phi$가 있음을 보일 것이다.

Define $\phi$ as 

$$
\begin{aligned}
  \phi: D &\longrightarrow F \\
        a &\longmapsto [(a, 1)]
\end{aligned}
$$


<span class="statement-title">proof</span>.<br>
<div class="math-statement" markdown="1">
  Check 

  1. $\phi$ is additive homormophism
  2. $\phi$ is multiplicative homormophism
  3. $\phi$ is 1-1 & onto

  이것에 대한 증명 역시 쉽게 할 수 있으므로 생략한다.
</div>

<br>
<hr>

이것으로 아래의 정리가 성립한다.

<span class="statement-title">Theorem</span>.<br>
<div class="statement" markdown="1">
  All Integral Domain $D$ can be enlarged to a Field $F$ which consist of quotient of $D$.

  이때의 Field $F$를 Quotient Field라고 한다.
</div>

<br>
<hr>

### Uniqueness of Quotient Field

Domain $D$를 포함하는 어떤 Field가 있다고 하자. 그러면 이 Field에는 $a, b \in D$에 대해 $a/b$를 원소로 가질 것이다.

따라서 우리가 $D$로부터 유도한 Field $F$는 $D$를 포함하는 가장 작은 Field가 될 것이다!!

즉, Domain $D$를 포함하는 모든 Field는 $D$의 Quotient Field를 포함하며, 또한 Domain $D$의 any two Qutotient Field는 서로 동형이다.

<br>

이것을 수학적으로 기술하면 아래와 같다.

<span class="statement-title">Theorem</span>.<br>
<div class="statement" markdown="1">
  Let $F$ be a Quotient Field of Domain $D$, and let $L$ be a any field containing $D$. ($L$ is any extension field of $D$.)

  THEN, $\exists$ a 1-1 ring homormophism $\psi: F \longrightarrow L$ s.t. $\psi(x) = x$ for $\forall x \in D$.

  즉, $F \cong \psi[F] \subset L$.
</div>

<br>

<span class="statement-title">proof</span>.<br>

<div class="math-statement" markdown="1">

</div>