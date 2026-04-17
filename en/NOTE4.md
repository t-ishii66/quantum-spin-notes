# Why θ/2 Appears in the Spin-1/2 Rotation Operator

> **Series**: [From Experiments to Pauli Matrices](NOTE1.md) → [Rotation Operators](NOTE2.md) → [The Bloch Sphere](NOTE3.md) → This document (NOTE4.md) → [Bell's Inequality](NOTE5.md)

## Purpose of This Document

In [NOTE1.md](NOTE1.md), we derived the Pauli matrices $\sigma_x, \sigma_y, \sigma_z$ from experimental facts, confirmed that the spin operators are $S_i = \hbar\sigma_i/2$, and verified the commutation relation $[\sigma_i, \sigma_j] = 2i\epsilon_{ijk}\sigma_k$.

In [NOTE2.md](NOTE2.md), we derived that the rotation operator takes the form

```math
U(\theta,\mathbf{n}) = \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

This document connects the two. Specifically, we explain in a single logical flow:

1. Why Pauli matrices are on equal footing with angular momentum (the meaning of commutation relations)
2. Substituting $\mathbf{J} = \mathbf{S} = \frac{\hbar}{2}\boldsymbol{\sigma}$ produces $\theta/2$
3. What the resulting rotation matrix looks like concretely
4. The physical meaning of $\theta/2$ (not returning to the original after 360 degrees)

Throughout this document, $\theta$ denotes the **rotation angle** about the axis $\mathbf{n}$, which is different from the polar angle of the Bloch sphere (the angle from the $z$-axis).

---

## Stage 1: Why Pauli Matrices Are Angular Momentum

### Two Faces of Classical Angular Momentum

In classical mechanics, angular momentum is defined as

```math
\mathbf{L} = \mathbf{r} \times \mathbf{p}
```

This is a **constructive definition** — "a quantity built from position and momentum."

However, as we saw in [NOTE2.md](NOTE2.md), $\mathbf{L}$ has another face: its role as the **generator of rotations**. For an infinitesimal rotation $\delta\phi$ about the $z$-axis,

```math
\delta\hat{x} = \frac{i}{\hbar}\delta\phi\,[G_z,\,\hat{x}]
```

when we searched for $G_z$ satisfying this condition, we found $G_z = \hat{L}_z$. In other words, angular momentum is also "the quantity that generates rotations."

In classical mechanics, these two faces refer to the same thing. But in quantum mechanics, **being a generator of rotations** becomes the more fundamental definition.

### Definition of Angular Momentum in Quantum Mechanics

In quantum mechanics, angular momentum is defined as follows.

**Definition**: When three Hermitian operators $J_x, J_y, J_z$ satisfy

<table border="1" align="center"><tr><td>

```math
[J_i, J_j] = i\hbar\,\epsilon_{ijk}\,J_k
```

</td></tr></table>

we call $\mathbf{J} = (J_x, J_y, J_z)$ an **angular momentum**.

Why is this the definition? Because satisfying this commutation relation is **necessary and sufficient** for being a generator of rotations. We now examine the necessity and sufficiency concretely.

### Why the Commutation Relation Is Necessary

Rotations in space give different results when performed in different orders. Let us see this concretely.

Pick up a book in front of you and try the following two sequences:

- **Order A:** First rotate 90 degrees about the $x$-axis (left-right direction), then 90 degrees about the $z$-axis (vertical direction)
- **Order B:** First 90 degrees about the $z$-axis, then 90 degrees about the $x$-axis

The results differ. Rotations depend on the order (they are non-commutative).

We want to capture this "discrepancy when the order is swapped" using quantum-mechanical operators. Consider infinitesimal rotations: rotate by $\delta\alpha$ about the $x$-axis, then by $\delta\beta$ about the $y$-axis. Using the form from [NOTE2.md](NOTE2.md):

```math
U(\delta\alpha, \hat{x}) = I - \frac{i}{\hbar}\delta\alpha\,G_x + O(\delta\alpha^2)
```

```math
U(\delta\beta, \hat{y}) = I - \frac{i}{\hbar}\delta\beta\,G_y + O(\delta\beta^2)
```

Expanding the product for Order A ($x$ first, $y$ second) to second order:

```math
U(\delta\beta, \hat{y})\,U(\delta\alpha, \hat{x})
= I
- \frac{i}{\hbar}\delta\alpha\,G_x
- \frac{i}{\hbar}\delta\beta\,G_y
- \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,G_y G_x
+ \cdots
```

Order B ($y$ first, $x$ second):

```math
U(\delta\alpha, \hat{x})\,U(\delta\beta, \hat{y})
= I
- \frac{i}{\hbar}\delta\alpha\,G_x
- \frac{i}{\hbar}\delta\beta\,G_y
- \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,G_x G_y
+ \cdots
```

The first-order terms are the same. The difference appears at second order:

```math
\text{Order A} - \text{Order B}
= -\frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,(G_y G_x - G_x G_y)
= \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,[G_x, G_y]
```

In other words, **the discrepancy when two rotations are swapped is determined by the commutator $[G_x, G_y]$ of the generators.**

On the other hand, in classical geometry, the discrepancy from swapping infinitesimal rotations about $x$ and $y$ is an infinitesimal rotation about the $z$-axis. Let us verify this directly with rotation matrices.

The infinitesimal rotation matrix about the $x$-axis is (using $\cos\delta\alpha \approx 1$, $\sin\delta\alpha \approx \delta\alpha$ as in the $z$-axis version in [NOTE2.md](NOTE2.md)):

```math
R_x(\delta\alpha) \approx
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & -\delta\alpha \\
0 & \delta\alpha & 1
\end{pmatrix}
```

About the $y$-axis:

```math
R_y(\delta\beta) \approx
\begin{pmatrix}
1 & 0 & \delta\beta \\
0 & 1 & 0 \\
-\delta\beta & 0 & 1
\end{pmatrix}
```

Order A ($x$ first, $y$ second):

```math
R_y R_x \approx
\begin{pmatrix}
1 & \delta\alpha\,\delta\beta & \delta\beta \\
0 & 1 & -\delta\alpha \\
-\delta\beta & \delta\alpha & 1
\end{pmatrix}
```

Order B ($y$ first, $x$ second):

```math
R_x R_y \approx
\begin{pmatrix}
1 & 0 & \delta\beta \\
\delta\alpha\,\delta\beta & 1 & -\delta\alpha \\
-\delta\beta & \delta\alpha & 1
\end{pmatrix}
```

Taking the difference (the first-order terms are the same, so only second-order terms remain):

```math
R_y R_x - R_x R_y \approx
\begin{pmatrix}
0 & \delta\alpha\,\delta\beta & 0 \\
-\delta\alpha\,\delta\beta & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
```

Meanwhile, the infinitesimal rotation matrix about the $z$-axis is

```math
R_z(\delta\gamma) \approx
\begin{pmatrix}
1 & -\delta\gamma & 0 \\
\delta\gamma & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
```

and $R_z - I$ is

```math
R_z(\delta\gamma) - I \approx
\begin{pmatrix}
0 & -\delta\gamma & 0 \\
\delta\gamma & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
```

Comparing, setting $\delta\gamma = -\delta\alpha\,\delta\beta$ gives an exact match. That is,

```math
R_y R_x - R_x R_y \approx R_z(-\delta\alpha\,\delta\beta) - I
```

The discrepancy from swapping infinitesimal rotations about $x$ and $y$ is an infinitesimal rotation about the $z$-axis.

Now we translate this classical result into the language of quantum-mechanical generators. We will show that even the coefficient $i\hbar$ can be derived.

From the quantum-mechanical calculation above, the order difference was

```math
\text{Order A} - \text{Order B}
= \frac{1}{\hbar^2}\,\delta\alpha\,\delta\beta\,[G_x, G_y]
```

Meanwhile, the classical result says "the discrepancy is an infinitesimal rotation about the $z$-axis by angle $\delta\gamma = -\delta\alpha\,\delta\beta$." In quantum mechanics, an infinitesimal rotation about the $z$-axis is

```math
U(\delta\gamma, \hat{z}) = I - \frac{i}{\hbar}\,\delta\gamma\,G_z
```

so the "discrepancy" is

```math
U(\delta\gamma, \hat{z}) - I = -\frac{i}{\hbar}\,\delta\gamma\,G_z
= -\frac{i}{\hbar}\,(-\delta\alpha\,\delta\beta)\,G_z
= \frac{i}{\hbar}\,\delta\alpha\,\delta\beta\,G_z
```

Setting the two equal:

```math
\frac{1}{\hbar^2}\,\delta\alpha\,\delta\beta\,[G_x, G_y]
= \frac{i}{\hbar}\,\delta\alpha\,\delta\beta\,G_z
```

Cancelling $\delta\alpha\,\delta\beta$ and multiplying by $\hbar^2$:

```math
[G_x, G_y] = i\hbar\,G_z
```

**The $i\hbar$ is not postulated but derived.** Breaking down its origin:

- The $i$ comes from writing the infinitesimal rotation operator as $U = I - \frac{i}{\hbar}\delta\theta\,G$ (with $G$ Hermitian)
- The $\hbar$ comes from the ratio of $1/\hbar$ in the denominator and $1/\hbar^2$ at second order

The same calculation can be done for the $y$-$z$ and $z$-$x$ combinations, yielding

```math
[G_x, G_y] = i\hbar\,G_z, \qquad
[G_y, G_z] = i\hbar\,G_x, \qquad
[G_z, G_x] = i\hbar\,G_y
```

Summarizing:

<table border="1" align="center"><tr><td>

```math
[G_i, G_j] = i\hbar\,\epsilon_{ijk}\,G_k
```

</td></tr></table>

This is the **commutation relation** that rotation generators must satisfy, and it is the very definition of angular momentum.

In other words, this commutation relation is a translation into the language of operators of the geometrical property of 3-dimensional rotations: "swapping rotations about $x$ and $y$ produces a rotation about $z$ as a discrepancy." If something is a generator of rotations, it must satisfy this relation.

### Why the Commutation Relation Is Sufficient

Conversely, suppose three Hermitian operators $J_x, J_y, J_z$ satisfy this commutation relation. Can we actually construct rotation operators from them?

As seen in [NOTE2.md](NOTE2.md), finite rotations can be built by accumulating infinitesimal rotations:

```math
U(\theta, \mathbf{n}) = \lim_{N\to\infty}\left(I - \frac{i}{\hbar}\frac{\theta}{N}\,\mathbf{n}\cdot\mathbf{J}\right)^N
= \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

The question is whether the $U$ constructed this way behaves correctly as a "genuine rotation." That is, when composing two rotations $U(\alpha, \mathbf{e}_x)$ and $U(\beta, \mathbf{e}_y)$, does the result give the geometrically correct composite rotation?

To answer this question, let us decompose finite rotations into infinitesimal ones. The finite rotation $U(\alpha, \mathbf{e}_x)$ is the product of $N$ infinitesimal rotations $U(\delta\alpha, \mathbf{e}_x)$. Similarly, $U(\beta, \mathbf{e}_y)$ is a product of $N$ infinitesimal rotations. Therefore, the composition of two finite rotations is a long sequence of infinitesimal rotations:

```math
\underbrace{U(\delta\beta, \mathbf{e}_y)\cdots U(\delta\beta, \mathbf{e}_y)}_{N\text{ copies}}\;\underbrace{U(\delta\alpha, \mathbf{e}_x)\cdots U(\delta\alpha, \mathbf{e}_x)}_{N\text{ copies}}
```

When we want to swap the order of adjacent infinitesimal rotations in this sequence, what happens? As shown in the previous section, swapping two infinitesimal rotations produces

```math
U(\delta\alpha, \mathbf{e}_x)\,U(\delta\beta, \mathbf{e}_y) - U(\delta\beta, \mathbf{e}_y)\,U(\delta\alpha, \mathbf{e}_x) \sim \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,[G_x, G_y]
```

a "discrepancy" determined by the commutator $[G_x, G_y]$. If the commutation relation $[G_x, G_y] = i\hbar\,G_z$ matches the geometrical requirement, then the discrepancy from swapping one pair of infinitesimal rotations is correct.

Correctly rearranging the composition of finite rotations requires repeating such swaps of infinitesimal rotations many times, but if each swap produces the correct discrepancy, the final result is also correct. In other words, the commutation relations define the "swapping rules" for infinitesimal rotations, and as long as these match the geometry, finite rotations are automatically composed correctly.

### Orbital Angular Momentum Is Just a Special Case

In [NOTE2.md](NOTE2.md), we took the classical orbital angular momentum $\mathbf{L} = \mathbf{r} \times \mathbf{p}$, directly quantized it as $\hat{L}_z = \hat{x}\hat{p}_y - \hat{y}\hat{p}_x$, and verified that it satisfies the required commutation relations. This is a **concrete construction** of a generator satisfying the commutation relations, specific to particles with position and momentum.

However, the definition via commutation relations does not require the construction $\mathbf{r} \times \mathbf{p}$. Even for degrees of freedom that possess no position or momentum whatsoever, if three Hermitian operators satisfy the commutation relations, they constitute angular momentum.

### Pauli Matrices Satisfy This Condition

As directly computed in [NOTE1.md](NOTE1.md):

```math
[\sigma_i, \sigma_j] = 2i\,\epsilon_{ijk}\,\sigma_k
```

Therefore, setting $S_i = \frac{\hbar}{2}\sigma_i$:

<table border="1" align="center"><tr><td>

```math
[S_i, S_j] = i\hbar\,\epsilon_{ijk}\,S_k
```

</td></tr></table>

This is precisely the definition of angular momentum stated above.

Moreover, $S_i$ is a $2 \times 2$ matrix with no relation whatsoever to the position $\hat{x}$ or momentum $\hat{p}$. That is, $\mathbf{S}$:

- Is not constructed from $\mathbf{r} \times \mathbf{p}$
- But satisfies the commutation relations for rotation generators
- And is therefore angular momentum

This is the true identity of what is called **spin angular momentum**. It is "angular momentum that does not originate from motion through space," residing in an **internal degree of freedom** of the particle.

Furthermore, since $\mathbf{S}$ consists of $2 \times 2$ matrices, it is a 2-dimensional irreducible representation of angular momentum. In angular momentum theory, irreducible representations are classified by the quantum number $j = 0, 1/2, 1, 3/2, \ldots$. Only $j = 1/2$ corresponds to 2 dimensions, so $\mathbf{S}$ constructed from the Pauli matrices is established as the angular momentum for **spin 1/2**.

### Summary: Why $\boldsymbol{\sigma}$ Is Angular Momentum

Let us organize the flow.

1. Rotation generators satisfy the commutation relation $[J_i, J_j] = i\hbar\,\epsilon_{ijk}\,J_k$ (required by the geometry of rotations)
2. We define as angular momentum anything satisfying this commutation relation ($\mathbf{r} \times \mathbf{p}$ is merely a special case)
3. $S_i = \frac{\hbar}{2}\sigma_i$ satisfies this commutation relation (computed in [NOTE1.md](NOTE1.md))
4. Therefore $\mathbf{S}$ is angular momentum and can be substituted for $\mathbf{J}$ in the rotation operator $U = \exp(-i\theta\,\mathbf{n}\cdot\mathbf{J}/\hbar)$

---

## Stage 2: Substituting to Produce θ/2

### Starting Point

When dealing with purely spin degrees of freedom (ignoring spatial motion):

```math
\mathbf{J} = \mathbf{S}
```

As confirmed in the previous section, the spin operator for spin 1/2 is

```math
S_i = \frac{\hbar}{2}\,\sigma_i \qquad (i = x, y, z)
```

so

```math
\mathbf{n}\cdot\mathbf{J}
= \mathbf{n}\cdot\mathbf{S}
= n_x S_x + n_y S_y + n_z S_z
= \frac{\hbar}{2}(n_x\sigma_x + n_y\sigma_y + n_z\sigma_z)
= \frac{\hbar}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
```

Substituting into the rotation operator:

```math
U(\theta,\mathbf{n})
= \exp\!\left(-\frac{i}{\hbar}\,\theta\cdot\frac{\hbar}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
```

The $\hbar$ cancels:

<table border="1" align="center"><tr><td>

```math
U(\theta,\mathbf{n}) = \exp\!\left(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
```

</td></tr></table>

### Where Does θ/2 Come From?

Let us confirm the mechanism by which $\theta/2$ appears. The original expression

```math
\exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

has $\hbar$ in the denominator. On the other hand, for spin 1/2, $\mathbf{J} = \frac{\hbar}{2}\boldsymbol{\sigma}$, so $\hbar$ also appears in the numerator. These two $\hbar$'s cancel, leaving only $1/2$.

In other words, the $1/2$ in $\theta/2$ is the "1/2" of spin 1/2 itself. For a spin quantum number $s$, the angular momentum has scale $\hbar s$, so $s$ appears in the exponent in general. Since $s = 1/2$, we get $\theta/2$.

---

## Stage 3: Computing the Matrix Exponential

### A Convenient Property of Pauli Matrices

To write the rotation matrix explicitly, we need to compute $\exp(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma})$. Matrix exponentials are generally complicated, but Pauli matrices have a special property.

First, write out $\mathbf{n}\cdot\boldsymbol{\sigma}$. With $\mathbf{n} = (n_x, n_y, n_z)$:

```math
\mathbf{n}\cdot\boldsymbol{\sigma}
= n_x\begin{pmatrix}0&1\\1&0\end{pmatrix}
+ n_y\begin{pmatrix}0&-i\\i&0\end{pmatrix}
+ n_z\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= \begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
```

Let $M$ denote this matrix and compute $M^2$:

```math
M^2 = \begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
\begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
```

The $(1,1)$ entry:

```math
n_z^2 + (n_x - in_y)(n_x + in_y)
= n_z^2 + n_x^2 + n_y^2
= 1
```

(since $\mathbf{n}$ is a unit vector, $n_x^2 + n_y^2 + n_z^2 = 1$)

The $(1,2)$ entry:

```math
n_z(n_x - in_y) + (n_x - in_y)(-n_z) = 0
```

Similarly $(2,1) = 0$, $(2,2) = 1$. Therefore

```math
(\mathbf{n}\cdot\boldsymbol{\sigma})^2 = I
```

This is a property specific to Pauli matrices, following solely from $\mathbf{n}$ being a unit vector.

### Expanding the Exponential

Using $M^2 = I$, the powers of $M$ take only two forms:

```math
M^0 = I, \quad M^1 = M, \quad M^2 = I, \quad M^3 = M, \quad \ldots
```

That is, even powers give $I$ and odd powers give $M$.

The definition of the matrix exponential is

```math
e^{-i\alpha M}
= \sum_{k=0}^{\infty}\frac{(-i\alpha)^k}{k!}M^k
```

(setting $\alpha = \theta/2$), and we separate this into even and odd terms:

```math
= \sum_{k\,\text{even}}\frac{(-i\alpha)^k}{k!}\,I
\;+\;\sum_{k\,\text{odd}}\frac{(-i\alpha)^k}{k!}\,M
```

The coefficient of the even terms is

```math
\sum_{k\,\text{even}}\frac{(-i\alpha)^k}{k!}
= 1 - \frac{\alpha^2}{2!} + \frac{\alpha^4}{4!} - \cdots
= \cos\alpha
```

The coefficient of the odd terms is

```math
\sum_{k\,\text{odd}}\frac{(-i\alpha)^k}{k!}
= -i\alpha + \frac{i\alpha^3}{3!} - \cdots
= -i\!\left(\alpha - \frac{\alpha^3}{3!} + \cdots\right)
= -i\sin\alpha
```

Therefore

```math
e^{-i\alpha M} = \cos\alpha\,I - i\sin\alpha\,M
```

Restoring $\alpha = \theta/2$, $M = \mathbf{n}\cdot\boldsymbol{\sigma}$:

<table border="1" align="center"><tr><td>

```math
U(\theta,\mathbf{n}) = \cos\frac{\theta}{2}\,I - i\sin\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
```

</td></tr></table>

This is the complete form of the spin-1/2 rotation matrix.

---

## Stage 4: Verifying with Concrete Examples

### Example 1: Rotation about the $z$-axis

Setting $\mathbf{n} = (0,0,1)$ gives $\mathbf{n}\cdot\boldsymbol{\sigma} = \sigma_z$, so

```math
U(\theta, \hat{z})
= \cos\frac{\theta}{2}\begin{pmatrix}1&0\\0&1\end{pmatrix}
- i\sin\frac{\theta}{2}\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= \begin{pmatrix}
\cos\frac{\theta}{2} - i\sin\frac{\theta}{2} & 0 \\
0 & \cos\frac{\theta}{2} + i\sin\frac{\theta}{2}
\end{pmatrix}
```

Here $\theta$ is the **rotation angle** about the $z$-axis (not the Bloch sphere polar angle). Using Euler's formula $e^{-ix} = \cos x - i\sin x$:

```math
U(\theta, \hat{z})
= \begin{pmatrix}
e^{-i\theta/2} & 0 \\
0 & e^{+i\theta/2}
\end{pmatrix}
```

Opposite-sign phases are attached to $\vert {+z}\rangle$ and $\vert {-z}\rangle$ respectively. This alone does not evoke the image of "rotation," so let us apply it to a concrete state.

$\vert {+x}\rangle$ is, as derived in [NOTE1.md](NOTE1.md):

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
```

This is a state on the equator of the Bloch sphere (azimuthal angle $\phi = 0$). Since rotation about the $z$-axis is a rotation within the $x$-$y$ plane, the azimuthal angle $\phi$ should change. Applying $U(\theta, \hat{z})$:

```math
U(\theta, \hat{z})\,\vert {+x}\rangle
= \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}e^{-i\theta/2}\\e^{+i\theta/2}\end{pmatrix}
```

Factoring out the overall phase $e^{-i\theta/2}$:

```math
= \frac{e^{-i\theta/2}}{\sqrt{2}}\begin{pmatrix}1\\e^{+i\theta}\end{pmatrix}
```

Ignoring the overall phase (it does not affect physics):

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i\theta}\end{pmatrix}
```

As seen in [NOTE1.md](NOTE1.md), this is the equatorial state

```math
\frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

where $\phi$ is the azimuthal angle on the equator. $\phi = 0$ corresponds to $\vert {+x}\rangle$, $\phi = \pi/2$ to $\vert {+y}\rangle$.

In the result above, the azimuthal angle has become $\phi = \theta$ (the rotation angle). That is, the original $\vert {+x}\rangle$ (azimuthal angle $0$) has moved to azimuthal angle $\theta$ on the equator of the Bloch sphere. This is precisely a rotation by angle $\theta$ about the $z$-axis.

On the other hand, applying to $\vert {+z}\rangle$ (north pole) and $\vert {-z}\rangle$ (south pole):

```math
U(\theta, \hat{z})\,\vert {+z}\rangle = e^{-i\theta/2}\vert {+z}\rangle, \qquad
U(\theta, \hat{z})\,\vert {-z}\rangle = e^{+i\theta/2}\vert {-z}\rangle
```

Both acquire only an overall phase and do not move on the Bloch sphere. It is natural that the north and south poles do not move under rotation about the $z$-axis.

### Example 2: 180-Degree Rotation about the $x$-axis

Setting $\mathbf{n} = (1,0,0)$, $\theta = \pi$ (here too $\theta$ is the **rotation angle** about the $x$-axis, not the Bloch sphere polar angle):

```math
U(\pi, \hat{x})
= \cos\frac{\pi}{2}\,I - i\sin\frac{\pi}{2}\,\sigma_x
= 0\cdot I - i\cdot 1\cdot\sigma_x
= -i\sigma_x
= -i\begin{pmatrix}0&1\\1&0\end{pmatrix}
= \begin{pmatrix}0&-i\\-i&0\end{pmatrix}
```

Applying this to $\vert {+z}\rangle$:

```math
U(\pi, \hat{x})\vert {+z}\rangle
= \begin{pmatrix}0&-i\\-i&0\end{pmatrix}\begin{pmatrix}1\\0\end{pmatrix}
= \begin{pmatrix}0\\-i\end{pmatrix}
= -i\begin{pmatrix}0\\1\end{pmatrix}
= -i\,\vert {-z}\rangle
```

Removing the overall phase $-i$, this is $\vert {-z}\rangle$. A 180-degree rotation about the $x$-axis sends the north pole to the south pole. This is the expected result from the Bloch sphere picture.

---

## Thought Experiment: If You Classically Rotate by θ, Does the Bloch Vector Also Move by θ?

Here $\theta$ is the **rotation angle** about the axis $\mathbf{n}$ (the $\theta$ in $U(\theta, \mathbf{n})$ itself), which is a different quantity from the Bloch sphere polar angle (the angle from the $z$-axis). Where both appear simultaneously, we write the Bloch sphere parameters as $\theta_0, \phi_0$ to distinguish them.

### Setting Up the Question

Suppose a spin-1/2 particle is in a state $\vert \psi\rangle$, pointing to some location on the Bloch sphere.

Suppose this particle is **classically** rotated by angle $\theta$. Imagine physically rotating the Bloch sphere itself by $\theta$.

Does the Bloch vector (the arrow representing measurement statistics) move by $\theta$, or only by $\theta/2$?

Since the rotation operator contains $\theta/2$, one might think "the Bloch vector also moves only by half." Let us check.

### Checking with Concrete Examples

Rotate by angle $\theta$ about the $z$-axis. Since rotation about the $z$-axis is a rotation within the $x$-$y$ plane, the azimuthal angle changes on the Bloch sphere. From Example 1:

```math
U(\theta, \hat{z}) = \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
```

Take the initial state to be $\vert {+x}\rangle$ (on the equator of the Bloch sphere, azimuthal angle $\phi_0 = 0$).

As computed in Example 1, the state after rotation is (up to overall phase):

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i\theta}\end{pmatrix}
```

The azimuthal angle has moved from $0 \to \theta$. That is, **the Bloch vector has moved by $\theta$** — not $\theta/2$.

Another example. Take the initial state to be $\vert {+y}\rangle$ (azimuthal angle $\phi_0 = \pi/2$):

```math
U(\theta, \hat{z})\,\vert {+y}\rangle
= \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}e^{-i\theta/2}\\i\,e^{+i\theta/2}\end{pmatrix}
```

Factoring out the overall phase $e^{-i\theta/2}$:

```math
= \frac{e^{-i\theta/2}}{\sqrt{2}}\begin{pmatrix}1\\i\,e^{i\theta}\end{pmatrix}
```

Since $i = e^{i\pi/2}$, we have $i\,e^{i\theta} = e^{i(\theta + \pi/2)}$. Removing the overall phase:

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i(\theta + \pi/2)}\end{pmatrix}
```

The azimuthal angle has moved from $\pi/2 \to \theta + \pi/2$. Again, **the change in azimuthal angle is $\theta$** — not $\theta/2$.

### Why θ and Not θ/2?

The state vector does contain $\theta/2$. The $\vert {+z}\rangle$ component acquires $e^{-i\theta/2}$ and the $\vert {-z}\rangle$ component acquires $e^{+i\theta/2}$.

However, what determines the azimuthal angle on the Bloch sphere is the **relative phase** of the two components:

```math
\frac{e^{+i\theta/2}}{e^{-i\theta/2}} = e^{i\theta}
```

The difference between $+\theta/2$ and $-\theta/2$ is $\theta$. Because the two components receive phases of $\theta/2$ with opposite signs, the relative phase changes by $\theta$.

This is the mechanism by which the Bloch vector moves by $\theta$ even though $\theta/2$ appears in the rotation operator.

### Remark: This Holds for General States, Not Just Equatorial Ones

We verified this for equatorial states under rotation about the $z$-axis, but the same holds for general states.

Writing the Bloch sphere parameters of a general state as polar angle $\theta_0$ and azimuthal angle $\phi_0$, the state is $\vert \psi\rangle = \cos(\theta_0/2)\vert {+z}\rangle + e^{i\phi_0}\sin(\theta_0/2)\vert {-z}\rangle$. Applying the $z$-axis rotation $U(\theta, \hat{z})$:

```math
U(\theta, \hat{z})\vert \psi\rangle
= e^{-i\theta/2}\cos\frac{\theta_0}{2}\vert {+z}\rangle + e^{i(\phi_0+\theta/2)}\sin\frac{\theta_0}{2}\vert {-z}\rangle
```

Factoring out the overall phase $e^{-i\theta/2}$:

```math
= e^{-i\theta/2}\left(\cos\frac{\theta_0}{2}\vert {+z}\rangle + e^{i(\phi_0+\theta)}\sin\frac{\theta_0}{2}\vert {-z}\rangle\right)
```

The polar angle $\theta_0$ is unchanged, and the azimuthal angle changes from $\phi_0 \to \phi_0 + \theta$. This is a rotation by $\theta$ about the $z$-axis.

### Summary: The Dual Structure

When classically rotated by $\theta$:

- The **state vector** (spinor) undergoes a phase change of $\theta/2$
- The **Bloch vector** (measurement statistics) rotates by $\theta$

This dual structure comes from the many-to-one mapping from state vectors to Bloch vectors. $\vert \psi\rangle$ and $e^{i\chi}\vert \psi\rangle$ (differing only by an overall phase) point to the same location on the Bloch sphere. In particular, $\vert \psi\rangle$ and $-\vert \psi\rangle$ correspond to the same point.

In mathematical language, the spin-1/2 rotation operator is not a representation of the rotation group $\mathrm{SO}(3)$ itself, but of its **double cover** $\mathrm{SU}(2)$. Two elements of $\mathrm{SU}(2)$ ($U$ and $-U$) correspond to one rotation of $\mathrm{SO}(3)$ — therefore the state vector completes a cycle in $4\pi$, while the Bloch vector (i.e., the physical measurement statistics) completes a cycle in $2\pi$.

The answer is therefore clear:

> If you classically rotate by $\theta$, the Bloch vector also moves by $\theta$ — not $\theta/2$.

---

## Stage 5: A 360-Degree Rotation Does Not Return to the Original

### Computation

Substituting $\theta = 2\pi$ (360 degrees):

```math
U(2\pi,\mathbf{n})
= \cos\pi\,I - i\sin\pi\,\mathbf{n}\cdot\boldsymbol{\sigma}
= (-1)\cdot I - i\cdot 0\cdot\mathbf{n}\cdot\boldsymbol{\sigma}
= -I
```

That is, regardless of the axis, a 360-degree rotation gives

```math
\vert \psi\rangle \to -\vert \psi\rangle
```

The state vector does not return to the original — its **sign is flipped**.

However, what about the physical state? In quantum mechanics, $\vert \psi\rangle$ and $-\vert \psi\rangle$ lie on the same ray (they differ only by an overall phase), so all probabilities agree in any single measurement and they cannot be distinguished. In other words, "the state vector flips sign, but physical observables are unchanged" — the sign difference is visible only in interference experiments where it is compared with another path.

### Returning After 720 Degrees

Substituting $\theta = 4\pi$ (720 degrees):

```math
U(4\pi,\mathbf{n})
= \cos 2\pi\,I - i\sin 2\pi\,\mathbf{n}\cdot\boldsymbol{\sigma}
= (+1)\cdot I - 0
= I
```

Only after 720 degrees does $\vert \psi\rangle \to \vert \psi\rangle$.

### Why It Doesn't Return After 360 Degrees

The cause is $\theta/2$. For rotation angle $\theta$, the matrix contains $\cos(\theta/2)$ and $\sin(\theta/2)$. Since trigonometric functions have period $2\pi$, $\theta/2 = 2\pi$ means $\theta = 4\pi$ for one full cycle.

In other words:

- **Classical rotations** complete a cycle in $2\pi$
- **The spin-1/2 state vector** completes a cycle in $4\pi$

This property of "rotating at half the speed" is directly tied to the value $s = 1/2$.

### Can It Be Observed?

$\vert \psi\rangle$ and $-\vert \psi\rangle$ cannot be distinguished by a single measurement. Probabilities are computed as $\vert \langle\phi\vert \psi\rangle\vert ^2$, and the overall phase $-1$ cancels in the square.

However, if a particle's spin is split into two paths and only one path undergoes a 360-degree rotation before the paths are recombined, the $-1$ sign difference is observed as **interference**. This has been experimentally confirmed using neutron interferometry.

**A note on the relationship with NOTE1**: In [NOTE1.md](NOTE1.md), we stated that "multiplying the entire state vector by a common phase $e^{i\gamma}$ is unobservable by any measurement." This might appear to contradict the above, but there is no contradiction.

What NOTE1 calls an "overall phase" is a phase applied uniformly to the entire system. As long as one measures a single state $\vert \psi\rangle$, $\vert \psi\rangle$ and $e^{i\gamma}\vert \psi\rangle$ are indeed indistinguishable.

What happens in the interference experiment is different. A single particle is split into two paths A and B, and only path B undergoes a 360-degree rotation. Then

```math
\text{state after recombination} \sim \vert \psi_A\rangle + (-1)\vert \psi_B\rangle
```

Here the $-1$ is not a phase applied to the entire system, but a **relative phase** between the two paths. Relative phases affect interference patterns and are therefore observable. This has exactly the same structure as the statement in NOTE1 that "only the relative phase $e^{i\phi}$ remains" — the overall phase disappears, but the relative phase has physical meaning.

In other words, the principle "the overall phase is unobservable" always holds. The $-1$ from a 360-degree rotation is visible because it appears as a relative phase in the interference experiment.

---

## Appendix: Why 1/2? A Broader Perspective

### Angular Momentum Quantum Number and the Period of Rotation

In general, for a system with angular momentum quantum number $j$:

```math
U(\theta,\mathbf{n}) = \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

where $\theta$ is the rotation angle about the axis $\mathbf{n}$ (not the Bloch sphere polar angle). The angular momentum quantum number $j$ is determined from the eigenvalue of the operator $\mathbf{J}^2 = J_x^2 + J_y^2 + J_z^2$, which represents the "magnitude" of the angular momentum:

```math
\mathbf{J}^2\vert j, m\rangle = j(j+1)\hbar^2\,\vert j, m\rangle
```

$j$ takes one of the values $0, 1/2, 1, 3/2, \ldots$. For each $j$, the eigenvalues $m\hbar$ of the $z$-component $J_z$ number $(2j+1)$, with $m = -j, -j+1, \ldots, +j$.

To examine the period of rotation, it is convenient to choose the axis as the $z$-axis (the conclusion is the same for any axis). Setting $\mathbf{n} = \hat{z}$ gives $U = e^{-i\theta J_z/\hbar}$. Acting on the eigenstate $\vert j, m\rangle$ of $J_z$:

```math
e^{-i\theta J_z/\hbar}\,\vert j, m\rangle
= e^{-i\theta\,(m\hbar)/\hbar}\,\vert j, m\rangle
= e^{-im\theta}\,\vert j, m\rangle
```

In the second line we used $J_z\vert j, m\rangle = m\hbar\vert j, m\rangle$. When the operator $J_z$ inside the exponential acts on an eigenstate, it is replaced by its eigenvalue $m\hbar$ — this is the fundamental property of the operator exponential.

A general state can be expanded as $\vert \psi\rangle = \sum_m c_m\vert j, m\rangle$, so

```math
U\vert \psi\rangle = \sum_m c_m\,e^{-im\theta}\,\vert j, m\rangle
```

Each component $\vert j, m\rangle$ acquires a different phase $e^{-im\theta}$.

The condition for all components to return to the original is that $e^{-im\theta} = 1$ holds for all $m$.

- If $j$ is an integer ($j = 0, 1, 2, \ldots$), then $m$ is also an integer, so all return at $\theta = 2\pi$
- If $j$ is a half-integer ($j = 1/2, 3/2, \ldots$), then $m$ includes half-integers, so at $\theta = 2\pi$ we get $e^{-i\cdot(1/2)\cdot 2\pi} = e^{-i\pi} = -1$, and they do not return. They return at $\theta = 4\pi$

Spin 1/2 is the simplest case with $j = 1/2$.

The same caveat about 360-degree rotations applies here as well. The period of the state vector is $4\pi$ for half-integer $j$ and $2\pi$ for integer $j$. However, the $-1$ arising from a $2\pi$ rotation for half-integer $j$ is an overall phase, so single-measurement probabilities are unchanged. For spin 1/2, the Bloch vector direction returns to the original after $2\pi$. The sign flip for half-integer $j$ is visible only in interference experiments.

---

## Logical Structure (Review)

```
Rotation generators satisfy [J_i, J_j] = iℏε_{ijk}J_k (from the geometry of rotations)
    ↓
Anything satisfying this commutation relation is angular momentum (r×p is a special case)
    ↓
S_i = (ℏ/2)σ_i satisfies this commutation relation → spin is angular momentum
    ↓
Substitute J = S = (ℏ/2)σ into U(θ,n) = exp(−iθ n·J/ℏ)
    ↓
ℏ cancels → U = exp(−iθ/2 n·σ)
    ↓
Show (n·σ)² = I → the exponential decomposes into cos + sin
    ↓
U = cos(θ/2) I − i sin(θ/2) n·σ
    ↓
θ = 2π gives U = −I (sign flip after 360 degrees)
    ↓
θ = 4π gives U = +I (return to original after 720 degrees)
```

The origin of $\theta/2$ is the $1/2$ in $S_i = \hbar\sigma_i/2$, and that $1/2$ is the spin quantum number $s = 1/2$ itself. And $\mathbf{S}$ can be substituted for $\mathbf{J}$ in the rotation operator not because it is built from $\mathbf{r} \times \mathbf{p}$, but because it satisfies the commutation relations for rotations.

---

**Next document**: [NOTE5.md — Bell's Inequality](NOTE5.md) uses the tools of rotation and eigenstates developed in this document to derive Bell's inequality from the correlations of a two-particle system.
