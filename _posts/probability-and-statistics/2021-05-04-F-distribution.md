---
title: "F-Distribution"
layout: post
use_math: true
tags: ["Probability"]
---

### 서론
2021-1학기, 대학에서 '확률과 통계' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr/>

<span class="statement-title">Definition.</span> F-Distribution<br>

If $V_1 \sim \chi^2(n_1)$ and $V_2 \sim \chi^2(n_2)$ are independent, 

then $F := \dfrac{V_1/n_1}{V_2/n_2}$ is called **\<Snedecor's F-Distribution\>** with degrees of freedom $n_1$ and $n_2$, and denoted as

$$
F \sim F(n_1, n_2)
$$

ps) 일반적으로, $F(n_1, n_2) \ne F(n_2, n_1)$이다. F-Distribution은 non-symmetric이라는 말.


<div class="img-wrapper">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/F-distribution_pdf.svg/488px-F-distribution_pdf.svg.png" width="300px">
  <p>
  Image from <a href="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/F-distribution_pdf.svg/488px-F-distribution_pdf.svg.png">Wikipedia</a>
  </p>
</div>

<br/>

<span class="statement-title">Remark.</span><br>

1\. The order $n_1$ and $n_2$ is very important.

In fact we have $F(n_1, n_2) \overset{D}{=} \dfrac{1}{F(n_2, n_1)}$.

<br/>

2\. Let $f_\alpha (n_1, n_2)$ be the number $x$ such that $\alpha = P\left(F(n_1, n_2) \ge x\right)$.

Here, we have $f_{1-\alpha}(n_1, n_2) = \dfrac{1}{f_{\alpha}(n_2, n_1)}$


