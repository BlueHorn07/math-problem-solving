---
title: "MATH301 - Modern Algebra 1"
layout: post
use_math: true
tags: ["Modern Algebra1"]
hidden: true
---


<div class="img-wrapper">
  <img src="{{ "/assets/img/group_meme.jpg" | relative_url }}">
</div>

#### 참고 교재
- 『A First Course in Abstract Algebra』 Fraleigh, 7th ed.
- 『Abstract Algebra』 Dummit & Foote, 3rd ed.

<hr>

### Group

<div class="statement" markdown="1">

<span class="statement-title">Lagrange Theorem</span><br>

If $H$ is a subgrop of a group $G$, then $\lvert H \rvert \mid \lvert G \rvert$, in other words, $\lvert G \rvert = [G:H] \lvert H \rvert$. 

</div>

- [Cyclic Group]({{"2020/10/18/Cyclic-group-and-subgroup.html" | relative_url}})
- Symmetric Group
- Coset
- [Lagrange Theorem]({{"2020/10/14/Lagrange-thm.html" | relative_url}})
- Permutation Group
- orbit; cycle; transposition
- Alternating Group

#### Fundamental Theorem of Finitely Generated Abelian Group

<div class="statement" markdown="1">

<span class="statement-title">F.T of f.g. Abelian Group</span><br>

Every f.g. abelian group $G$ is isomorphic to direct product of cyclic groups.

$$
G \cong \mathbb{Z}_{(p_1)^{r_1}} \times \mathbb{Z}_{(p_2)^{r_2}} \times \cdots \times \mathbb{Z}_{(p_n)^{r_n}} \times \mathbb{Z} \times \mathbb{Z} \times \cdots \times \mathbb{Z}
$$

Where $p_i$ are primes, not necessarily distinct, and $r_i$ are positive integers.

</div>

- Decomposable & Indecomposable group
- $p$-group [^1]

<hr>

### Factor Group & Homomorphisms

- [Homomorphism + 문풀]({{"2020/12/24/Group-Homo-Iso.html" | relative_url}})
- [Cayley's Theorem]({{"2020/12/24/Cayley-Theorem.html" | relative_url}})

<hr>

<div class="statement" markdown="1">

condition for operation well-definedness on Factor group

$$
H \trianglelefteq G \iff gHg^{-1} \subseteq H \quad (\forall g \in G)
$$

</div>

- [Factor Group]({{"2020/12/24/Factor-Group.html" | relative_url}})
  - from normal subgroups
  - from homomorphism
  - Auto-morphism
    - inner automorphism $\sigma_g$

<hr>

<div class="statement" markdown="1">

<span class="statement-title">Fundamental Homomorphism Theorem</span><br>

Let $\phi: G \longrightarrow G'$ be a group homomorphism, THEN

1. $\phi[G]$ is a group.
2. ${G}/{\ker \phi} \cong \phi[G]$

</div>

- [Fundamental Homomorphism Theorem(FHT)]({{"2020/12/25/Fundamental-Homo-theorem.html" | relative_url}}); 1st Isomorphism Thm
  - [Canonical homomorphism]({{"2020/12/25/Fundamental-Homo-theorem.html#canonical-homomorphism" | relative_url}}) $\gamma: G \longrightarrow G/H \quad (H \trianglelefteq G)$
- [index-2 group is normal]({{"2020/12/25/index-2-Group.html" | relative_url}})
- [Factor Group - Appliaction]({{"2020/12/25/Factor-Group-Application.html" | relative_url}}')
  - [Converse of Lagrange Thm]({{"2020/11/28/Converse-of-Lagrange-Thm.html" | relative_url}})
- [Three Isomorphism Theorems]({{"2020/12/25/Isomorphism-Thm.html" | relative_url}})
- [Three Sylow Theorems]({{"2020/12/26/Sylow-thm.html" | relative_url}})
  - [$p$-group]({{"2020/12/26/Sylow-thm.html#p-group" | relative_url}})
  - [normalizer]({{"2020/12/26/Sylow-thm.html#normalizer" | relative_url}}) of $H$ in $G$; $N_G(H)$

<hr>

  - [Sylow $p$-group]({{"2020/12/26/Sylow-thm.html#sylow-p-group" | relative_url}})
  - [Application 1]({{"2020/12/26/Sylow-thm-Application-1.html" | relative_url}})
  - [Application 2]({{"2020/12/26/Sylow-thm-Application-2.html" | relative_url}})
  - [Examples]({{"2020/12/26/Sylow-thm-Application-2.html#sylow-theorem---examples" | relative_url}})
    - [Type-1]({{"2020/12/26/Sylow-thm-Application-2.html#type-1" | relative_url}})
    - [Type-2]({{"2020/12/26/Sylow-thm-Application-2.html#type-2" | relative_url}})

### Ring & Field
- Ring [1]({{"2020/12/05/Ring-1.html" | relative_url}}), [2]({{"2020/12/05/Ring-2.html" | relative_url}})
  - commutative ring
  - [Ring homormophism & isomorphism]({{"2020/12/05/Ring-1.html#ring-homomorphism" | relative_url}})
  - Unity; multiplicative identity
  - [division ring]({{"2020/12/05/Ring-2.html#division-ring" | relative_url}})
  - [Field & Skew Field]({{"2020/12/05/Ring-2.html#field--skew-field" | relative_url}})
  - [Quaternion]({{"2020/12/05/Ring-2.html#quternion" | relative_url}})
  - [zero-divisor]({{"2020/12/05/Ring-2.html#zero-divisor" | relative_url}})
  - Bezout's Identity
  - Charasteric of Ring; $\textrm{Char}(R)$
- [Integral Domain]({{"2020/12/06/Field.html" | relative_url}})
  - [Field $\implies$ Integral Domain]({{"2020/12/06/Field.html#field-implies-integral-domain" | relative_url}})
  - [Finite integral domain $\implies$ Field]({{"2020/12/06/Field.html#finite-integral-domain-implies-field" | relative_url}})

<hr>

<div class="statement" markdown="1">

<span class="statement-title">Fermat's Little Theorem</span><br>

Let $p$ be a prime, IF $a \in \mathbb{Z}$, and $p \nmid a$, THEN

$$
a^{p-1} \equiv 1 \quad (\textrm{mod} \; p)
$$

</div>

- [Fermat's Little Theorem]({{"2020/12/26/Fermat-little-theorem.html" | relative_url}})
  - [Examples]({{"2020/12/26/Fermat-little-theorem.html#examples" | relative_url}})

<div class="statement" markdown="1">

<span class="statement-title">Euler's Theorem</span><br>

If $a \in \mathbb{Z}$, and $(a, n) = 1$, THEN

$$
a^{\varphi(n)} \equiv 1 \quad (\textrm{mod} \; p)
$$

**<u>NOTE</u>**: if $n = p$, then $\varphi(p) = p-1$

</div>

- Euler's Theorem

<hr>

- [Quotient Field]({{"2020/12/19/Qutient-Field.html" | relative_url}})

<div class="statement" markdown="1">

<span class="statement-title">Eisenstein Criteria</span><br>

Let $p \in \mathbb{Z}$ be a prime, $f(x) = a_n x^n + \cdots a_0 \in \mathbb{Z}[x]$

IF 

$$
\begin{aligned}
  a_n &\not\equiv 0 \quad (\textrm{mod} \; p) \\
  a_i &\equiv 0 \quad (\textrm{mod} \; p) \quad 0 \le i < n\\
  a_0 &\not\equiv 0 \quad (\textrm{mod} \; p^2) \\
\end{aligned}
$$

THEN, $f(x)$ is irreducible over $\mathbb{Q}$.

</div>

- Ring of Polynomials
- Irreducible Polynomials
- Eisenstein Criteria
- Group Ring

### Appendix

<div class="statement" markdown="1">

For a homormophism $\phi$,

if $\ker \phi = \\{ e \\}$, then $\phi$ is 1-1.

</div>

<br>
<hr>

[^1]: Sylow Theorem 할 때도 잠깐 나온다!