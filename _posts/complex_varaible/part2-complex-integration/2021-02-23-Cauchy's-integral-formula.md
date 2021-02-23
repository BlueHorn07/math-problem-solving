---
title: "Cauchy's Integral Formula"
layout: post
use_math: true
tags: ["Complex Variable"]
---

### 서론
2020-2학기, 대학에서 '응용복소함수론' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<br><span class="statement-title">TOC.</span><br>

- Cauchy-Goursat Thm on a disc
- Cauchy-Goursat Thm on a simply connected domain
- multiply connected domains
- Cauchy's Integral Formula

<br/>
<hr/>

<span class="statement-title">[Review] Theorem.</span> Goursat Theorem<br/>

<div class="statement" markdown="1">

Let $D$ be an open set in $\mathbb{C}$.

Let $T$ be a triangle such that $T$ and its interior lie in $D$.

If $f(z)$ is **<u>analytic</u>** in $D$, then

$$
\oint_{T} f(z) dz = 0
$$

</div>

<br/>

<span class="statement-title">Theorem.</span> Cauchy-Goursat Theorem for a disc<br/>

<div class="statement" markdown="1">

Let $f(z)$ be **<u>analytic</u>** in a disc $D$. 

Then there is an analytic function $F(z)$ in $D$ such that

$$
F'(z) = f(z) \quad \textrm{for} \; z \in D
$$

</div>

<span class="statement-title">Corollary.</span><br/>

<div class="statement" markdown="1">

Let $f(z)$ be **<u>analytic</u>** in a disc $D$.

Then for any closed contour $C$ in $D$,

$$
\oint_{C} f(z) \; dz = 0
$$

</div>

증명은 생각보다 간단하다.

<div class="math-statement" markdown="1">

논의의 편의를 위해 Disc $D$의 중심이 원점이라고 하자.

그리고 $F(z)$를 아래와 같이 정의하자.

$$
F(z_0) = \int_{C} f(z) \; dz
$$

이제, 

$$
\lim_{h \rightarrow 0} \frac{F(z_0 + h) - F(z_0)}{h} = f(z_0)
$$

임을 보이자!

<div class="img-wrapper">
<img src= "{{"/assets/img/Complex_Varaible/cauchy-integral-formula-1.jpg" | relative_url }}" style="width:320px;">
</div>

$$
\begin{aligned}
    F(z_0 + h) - F(z_0) &= \int_{C_2} f(z) \; dz - \int_{C_1} f(z) \; dz \\
    &= \int_{C_3} f(z) \; dz
\end{aligned}
$$

Then, 

이때, $f(z_0)$에 대해 아래의 등식을 확인할 수 있다.

$$
\begin{aligned}
\frac{1}{h} \int_{C_3} f(z_0) \; dz &= f(z_0) \frac{1}{h} \int_{C_3} \; dz \\
 &= f(z_0) \frac{1}{h} h \\
 &= f(z_0)
\end{aligned}
$$

$$
\begin{aligned}
    &\frac{1}{h} \left( F(z_0 + h) - F(z_0) \right) - f(z_0) \\
    &= \frac{1}{h} \int_{C_3} f(z) \; dz - \frac{1}{h} \int_{C_3} f(z_0) \; dz \\
    &= \frac{1}{h} \int_{C_3} \left( f(z) - f(z_0) \right) \; dz
\end{aligned}
$$

이제 위의 식에서 "**ML-inequality**"를 적용해보자!!

$$
\begin{aligned}
\left| \frac{1}{h} \int_{C_3} \left( f(z) - f(z_0) \right) \; dz \right| &= \frac{1}{\left| h \right|} \max_{z \in C_3} \left| f(z) - f(z_0) \right| \cdot \left| h \right| \\ 
&= \max_{z \in C_3} \left| f(z) - f(z_0) \right|
\end{aligned}
$$

이때, $z \rightarrow z_0$ 할수록 $(z - z_0) \rightarrow 0$ 이므로 우변은 0이 된다.

즉, 

$$
\lim_{h \rightarrow 0} \frac{F(z_0 + h) - F(z_0)}{h} = f(z_0)
$$

이다!!

결론은 $F(z_0) = \int_{C} f(z) \; dz$로 둠으로써 $F'(z) = f(z)$가 되는 함수 $F(z)$를 찾았다!!

</div>

<br/>

<span class="statement-title">Generalization.</span> Principles of Deformation of Contours<br/>

앞에서는 disc $D$에 대해 Cauchy Theorem을 적용했다면, 이번에는 일반적인 형태의 영역 $D$에서 Cauchy Theorem을 적용한다.

일반적인 simply connected domain $D$ 위에서 폐적분 closed integral이 0이 됨을 보이기 위해 아래의 식을 증명해야 한다.

$$
\int_{C_1} f(z) \; dz = \int_{C_2} f(z) \; dz
$$

<div class="img-wrapper">
<img src= "{{"/assets/img/Complex_Varaible/cauchy-integral-formula-2.jpg" | relative_url }}" style="width:400px;">
</div>

curve $C_1$, $C_2$를 가로지르는 3개의 disc를 생각해보자.

이미 앞에서 disc 내의 analytic function의 closed integral의 값은 0임을 확인했으므로, 3개의 disc로 적당히 나누어 curve $C_1$, $C_2$를 disc 내부의 closed curve 3개로 나눌 수 있다.

이제 disc 위에서 three closed integral을 잘 정리하면, 

$$
\int_{C_1} f(z) \; dz = \int_{C_2} f(z) \; dz
$$

의 결과를 얻을 수 있다.

<br/>

<span class="statement-title">Theorem.</span><br/>

<div class="statement" markdown="1">

Let $f(z)$ be analytic in a simply connected domain $D$,

then there is an analytic function $F(z)$ in $D$ s.t.

$$
F'(z) = f(z) \quad \textrm{for} \; z \in D
$$

where $F(z)$ id defined as

$$
F(z) = \int_{C} f(w) \; dw
$$

</div>

<br/>
<hr/>

### Multiply Connected Domains

지금까지는 Domain에 hole이 없는 "simply connected domain" 위에서 analytic function을 살펴보았다.

지금부터는 시야를 확장해서 Domain에 "hole"이 있는 경우를 살펴보자.

<div class="img-wrapper">
<img src= "{{"/assets/img/Complex_Varaible/cauchy-integral-formula-3.jpg" | relative_url }}" style="width:450px;">
</div>

먼저 Domain에 hole이 하나 존재한다면, "**doubly connected domain**"이라고 한다. 만약 Domain에 hole이 $(p-1)$개 만큼 존재한다면, "**$p$-fold connected domain**"이라고 한다.

<span class="statement-title">Example.</span> integral of analytic function on doubly connected domain<br/>

doubly connected domain $D$ 위에서 analytic function $f(z)$를 적분해보자.

<div class="img-wrapper">
<img src= "{{"/assets/img/Complex_Varaible/cauchy-integral-formula-4.jpg" | relative_url }}" style="width:250px;">
</div>

이제까지 우리는 simply connected domain 위에서의 적분을 수행했다. 하지만, 지금은 "doubly connected domain" 위에서 적분하기 때문에 앞에서 얻은 "closed integral = 0"이라는 결과를 그대로 사용할 수 없다!!

그래서 약간의 꼼수를 쓰려고 한다.

<div class="img-wrapper">
<img src= "{{"/assets/img/Complex_Varaible/cauchy-integral-formula-5.jpg" | relative_url }}" style="width:450px;">
</div>

double connected domain 위에서의 curve $C_1$, $C_2$에서의 적분을 생각해보자. 이때, 두 curve의 사이를 적절히 분리하여 위와 같이 두 개의 curve $A_1$, $A_2$로 변형할 수 있다!

놀랍게도 $A_1$과 $A_2$는 simply connected domain 위에 있는 것으로 앞에서 쓴 Cauchy Theorem을 적용할 수 있다!!

따라서

$$
\oint_{A_1} f(z) \; dz = \oint_{A_2} f(z) \; dz = 0
$$

이 되고, 이에 따라 

$$
\oint_{C_1} f(z) \; dz - \oint_{C_2} f(z) \; dz = 0
$$

이 되어 결국

$$
\oint_{C_1} f(z) \; dz = \oint_{C_2} f(z) \; dz
$$

이 된다.

즉, doubly connected domain에서의 적분은 "curve와 상관없이" 모두 동일한 적분값을 얻는다!!


