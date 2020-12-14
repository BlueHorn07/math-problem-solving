---
title: "Linear Transform"
layout: post
use_math: true
tags: ["Complex Variable"]
---

### 서론
2020-2학기, 대학에서 '응용복소함수론' 수업을 듣고 공부한 바를 정리한 글입니다. 지적은 언제나 환영입니다 :)

<hr>

### Linear Transformation

$$
w = Az + B \quad (A \ne 0)
$$

위와 같은 형태의 변환은 Linear Transform이라고 한다.

복소 영역에서 Linear Transform이 어떻게 행동하는지 케이스 별로 살펴보자.

<br>

#### $B=0$

$$
w  = Az \quad (A \ne 0)
$$

$A = a \cdot e^{i\alpha}$, $z = r \cdot e^{i\theta}$라고 두면, $w$는 $w = (ar) \cdot e^{i(\theta + \alpha)}$가 된다.

<div class="img-wrapper">
  <img src= "{{ "/assets/img/Complex_Varaible/linear_transform_1.png" | relative_url }}" style="width:50%;">
</div>

즉, 각도 $\alpha$ 만큼 Domain이 회전 이동 한다.
