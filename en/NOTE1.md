# Deriving the Pauli Matrices from Experimental Facts

<img src="../images/pauli.png">

> **Series**: This document (NOTE1.md) → [Rotation Operators](NOTE2.md) → [The Bloch Sphere](NOTE3.md) → [The Origin of θ/2](NOTE4.md) → [Bell's Inequality](NOTE5.md)

## Purpose of This Document

This document derives the Pauli matrices $\sigma_x, \sigma_y, \sigma_z$ not as convenient tools introduced from above, but step by step from experimental facts.

Let us organize the starting assumptions.

1. When certain particles are subjected to a magnetic field, their trajectories split into **exactly two** paths (the Stern–Gerlach experiment)
2. In quantum mechanics, states are represented by vectors and physical observables by Hermitian operators
3. A state that yields a definite value $a$ upon measurement is an eigenvector belonging to eigenvalue $a$ of that operator

Along the way, situations will arise where these three alone are insufficient. For example, translating "50-50" into probabilities requires the Born rule, and adopting a complex vector space for the state space is itself an assumption. Such additional assumptions will be clearly stated each time they are used.

---

## Overall Flow

The derivation proceeds in five stages.

1. **Stern–Gerlach experiment** → Learn that spin is two-valued
2. **Two-valued $z$-measurement** → A 2-dimensional space and $\sigma_z$ are determined
3. **50-50 $x$-measurement** → The eigenstates of $\sigma_x$ are determined (with a remaining phase freedom) → Choosing a phase convention fixes $\sigma_x$
4. **The $y$-direction requires complex numbers** → Complex numbers are unavoidable, and $\sigma_y$ is determined
5. **Verification of commutation relations** → The three matrices are confirmed to be spin operators

---

## Stage 1: The Stern–Gerlach Experiment

### Overview of the Experiment

In 1922, Otto Stern and Walther Gerlach performed an experiment passing a beam of silver atoms through an inhomogeneous magnetic field. This experiment led to the discovery of spin.

The apparatus works as follows:

1. **Atom source**: Silver is heated in an oven, producing a beam of evaporated silver atoms
2. **Magnetic field region**: The beam passes through a magnetic field whose strength varies in the vertical direction ($z$-direction)
3. **Screen**: Atoms that have passed through the field strike a screen

Why an **inhomogeneous** field? If a small magnet is placed in a uniform field (same strength everywhere), the forces on the N-pole side and S-pole side are equal and opposite, and they cancel out. The magnet rotates in place but does not move — the beam trajectory is not deflected.

In the actual apparatus, the upper pole piece is shaped as a pointed wedge and the lower one is flat. This causes the field lines to be densely concentrated near the top and spread out near the bottom. In the region through which the beam passes, the field is slightly stronger toward the top and slightly weaker toward the bottom. Because of this gradient between dense and sparse field lines, the forces on the N-pole and S-pole sides of a small magnet do not balance, leaving a net force. If the $z$-component of the magnetic moment is positive, the atom is pulled toward the denser field lines at the top; if negative, it is pushed toward the sparser region at the bottom. The magnitude of the force is proportional to the $z$-component. In this way, the atomic trajectories are deflected, and the internal state can be read from the arrival position on the screen.

### Classical Prediction

The fact that silver atoms experience a force in the magnetic field means they must possess an internal magnetic moment — and hence an angular momentum as its source. In classical mechanics, this angular momentum can point in any direction in space. Therefore the $z$-component should take continuous values, and a **vertically spread continuous band** should appear on the screen.

### Actual Result

However, what appeared on the screen was not a band but **two clearly separated spots** — one at the top and one at the bottom.

This means the following:

- The $z$-component of the silver atom's internal angular momentum takes not continuous values, but **exactly two values**
- Each atom is sorted into either up or down, with nothing in between

This two-valuedness cannot be explained by classical mechanics. It was later understood to be a property of the **spin angular momentum** of the outermost electron of the silver atom — an angular momentum residing in an internal degree of freedom unrelated to spatial motion.

### Sequential Measurement Experiments

Connecting multiple Stern–Gerlach devices in series reveals further important facts.

**Experiment A: Same direction twice**

The beam is split in the $z$-direction. The lower beam ($-1$) is blocked by a wall and discarded; only the upper beam ($+1$) is extracted. This is passed through a second $z$-direction device. The result: **all particles emerge on the upper side**. None appear on the lower side.

That is, a particle confirmed to be "upper" by one $z$-measurement will always be "upper" when measured in the $z$-direction again. This is **reproducibility**.

**Experiment B: Measuring in a different direction**

The upper beam from a $z$-measurement is extracted and passed through an $x$-direction (horizontal) device. The result: upper and lower in the $x$-direction appear **50-50**.

Even though the particle was definite in the $z$-direction, the $x$-direction result is probabilistic.

**Experiment C: Confirmation of state update**

Continuing from Experiment B, only the upper beam in the $x$-direction is extracted and passed through another $z$-direction device. The result: the $z$-direction outcome returns to **50-50**.

Although we initially selected the upper side in the $z$-measurement, merely interposing an $x$-measurement has caused the $z$-information to be lost. In the standard quantum theory, this is described as **state update by measurement** — information about one direction is overwritten by measurement in another direction.

### Summary of Experimental Facts

| Fact | Description |
|------|-------------|
| Two-valuedness | The result of measurement in any direction is only $+1$ or $-1$ |
| Reproducibility | Re-measurement in the same direction reproduces the result |
| Probabilistic nature | Measurement in a different direction gives probabilistic results (after fixing $z$, measuring perpendicular $x$ gives 50-50) |
| State update | Interposing a measurement in one direction destroys information about another direction |

---

## Stage 2: From $z$-Measurement to $\sigma_z$

### From Experimental Facts to the State Space

In the Stern–Gerlach experiment, $z$-direction measurement returns only two values (upper and lower).

From this we learn:

- This internal degree of freedom returns only two values for the $z$-direction
- To distinguish these two definite states, a state space of at least 2 dimensions is required

As the minimal model, we adopt a 2-dimensional **complex** vector space. This is an assumption — the experiment tells us only the fact of "two values"; that the state space has the structure of a complex vector space, and why complex rather than real numbers, are accepted here without derivation. By "minimal model" we mean that at least 2 dimensions are needed to explain two values, and introducing more dimensions would not produce additional measurement outcomes.

### Placing the Eigenstates

A particle that comes out on the upper side in a $z$-measurement will always come out on the upper side if measured in the $z$-direction again. The same holds for the lower side. Therefore:

- There are two definite states for $z$-measurement
- One always returns "up ($+1$)," the other always returns "down ($-1$)"

We write these two states as $\vert {+z}\rangle$, $\vert {-z}\rangle$. Since they are completely distinguishable, they are orthogonal, and since they are states with probability 1, they are normalized:

```math
\langle{+z}\vert {+z}\rangle = 1, \qquad
\langle{-z}\vert {-z}\rangle = 1, \qquad
\langle{+z}\vert {-z}\rangle = 0
```

The $\langle \cdot \vert \cdot \rangle$ used here is the inner product — an operation that measures how similar two vectors are. Thinking in terms of ordinary vectors, if they point in the same direction, the inner product is maximal; if they are perpendicular, the inner product is zero. The same holds for state vectors: the inner product with itself is 1 (completely the same), and the inner product with a completely distinguishable state is 0 (not similar at all).

### Constructing the Measurement Operator

We now have states $\vert {+z}\rangle$ or $\vert {-z}\rangle$. Consider measuring silver that has been prepared in the upward state $\vert {+z}\rangle$ with a $z$-direction device. In quantum theory, the operation of "measuring with a device" is represented by a mathematical object called an **operator**.

Writing the $z$-direction device as the operator $\hat{Z}$, the result of applying it to upward-pointing silver is

```math
\hat{Z}\vert {+z}\rangle = (+1)\vert {+z}\rangle
```

The left-hand side means "applying the device $\hat{Z}$ to silver aligned upward $\vert {+z}\rangle$." The right-hand side means "measurement value $(+1)$ is obtained, and the post-measurement state remains $\vert {+z}\rangle$." Similarly for the downward case:

```math
\hat{Z}\vert {-z}\rangle = (-1)\vert {-z}\rangle
```

When applying an operator to a state yields a constant multiple (measurement value) × the original state, this relation is called an **eigenvalue equation**. The values $(+1)$, $(-1)$ are called **eigenvalues**, and $\vert {+z}\rangle$, $\vert {-z}\rangle$ are called **eigenstates**.

Using these two eigenstates and eigenvalues, we can construct the measurement operator. As preparation, let us introduce how to write an **arbitrary state**.

In a 2-dimensional complex vector space, the two orthogonal vectors $\vert {+z}\rangle$, $\vert {-z}\rangle$ form a basis. That is, any vector in this space can be written as a superposition of these two:

<table border="1" align="center"><tr><td markdown="1">

```math
\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle
```

</td></tr></table>

where $\alpha$, $\beta$ are complex coefficients. The eigenstate $\vert {+z}\rangle$ is the special case $\alpha = 1, \beta = 0$, and $\vert {-z}\rangle$ is the special case $\alpha = 0, \beta = 1$.

What physical meaning do the coefficients $\alpha$, $\beta$ have? Here we introduce one of the fundamental principles of quantum mechanics, the **Born rule**. The Born rule states that the probability of obtaining the eigenstate $\vert \phi\rangle$ when measuring the state $\vert \psi\rangle$ is given by the squared absolute value of their inner product:

<table border="1" align="center"><tr><td markdown="1">

```math
P(\phi) = \vert \langle\phi\vert \psi\rangle\vert ^2
```

</td></tr></table>

This is a rule that cannot be derived from experiment — it is an **axiom** accepted as part of the framework of quantum mechanics.

Let us apply this to $\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle$. The probability of obtaining $\vert {+z}\rangle$ in a $z$-measurement is

```math
\vert \langle{+z}\vert \psi\rangle\vert ^2
= \vert \alpha\langle{+z}\vert {+z}\rangle + \beta\langle{+z}\vert {-z}\rangle\vert ^2
= \vert \alpha\vert ^2
```

Similarly, the probability of obtaining $\vert {-z}\rangle$ is $\vert \beta\vert ^2$. That is, the squared absolute values of the coefficients directly give the probabilities. Since probabilities must sum to 1, the normalization condition $\vert\alpha\vert^2 + \vert\beta\vert^2 = 1$ is required.

Now let us proceed using this arbitrary state. Consider the meaning of the combination $\vert {+z}\rangle\langle{+z}\vert$. Acting on $\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle$:

```math
\vert {+z}\rangle\langle{+z}\vert \psi\rangle = \vert {+z}\rangle(\alpha\langle{+z}\vert {+z}\rangle + \beta\langle{+z}\vert {-z}\rangle) = \alpha\vert {+z}\rangle
```

This extracts only the $\vert {+z}\rangle$ component of the state. Such an operator is called a **projector**. Similarly, $\vert {-z}\rangle\langle{-z}\vert$ is the projector that extracts the $\vert {-z}\rangle$ component.

The idea is as follows. Multiply the projector $\vert {+z}\rangle\langle{+z}\vert$ by the eigenvalue $(+1)$ as a weight. Do the same for the $\vert {-z}\rangle$ component, and add them together:

```math
\hat{Z} = (+1)\vert {+z}\rangle\langle{+z}\vert + (-1)\vert {-z}\rangle\langle{-z}\vert
```

This is called the **spectral decomposition**. Let us verify that this is indeed the correct operator by acting on the eigenstates. Acting on $\vert {+z}\rangle$:

```math
\hat{Z}\vert {+z}\rangle
= (+1)\vert {+z}\rangle\underbrace{\langle{+z}\vert {+z}\rangle}_{=1}
 + (-1)\vert {-z}\rangle\underbrace{\langle{-z}\vert {+z}\rangle}_{=0}
= (+1)\vert {+z}\rangle \quad\checkmark
```

Similarly, acting on $\vert {-z}\rangle$:

```math
\hat{Z}\vert {-z}\rangle
= (+1)\vert {+z}\rangle\underbrace{\langle{+z}\vert {-z}\rangle}_{=0}
 + (-1)\vert {-z}\rangle\underbrace{\langle{-z}\vert {-z}\rangle}_{=1}
= (-1)\vert {-z}\rangle \quad\checkmark
```

Indeed, the two eigenvalue equations $\hat{Z}\vert {+z}\rangle = (+1)\vert {+z}\rangle$ and $\hat{Z}\vert {-z}\rangle = (-1)\vert {-z}\rangle$ set up in the "Constructing the Measurement Operator" section are reproduced. The orthogonality of the inner product ($\langle{+z}\vert {-z}\rangle = 0$) plays an essential role here.

### Expectation Value

Using the spectral decomposition, the **expectation value** (the average when a measurement is repeated many times) emerges naturally. Let us compute $\langle\psi\vert \hat{Z}\vert \psi\rangle$ for an arbitrary state $\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle$.

First, we find $\hat{Z}\vert \psi\rangle$. Using the spectral decomposition $\hat{Z} = (+1)\vert {+z}\rangle\langle{+z}\vert + (-1)\vert {-z}\rangle\langle{-z}\vert$:

```math
\hat{Z}\vert \psi\rangle = (+1)\alpha\vert {+z}\rangle + (-1)\beta\vert {-z}\rangle
```

Next, multiply from the left by

```math
\langle\psi\vert = \alpha^*\langle{+z}\vert + \beta^*\langle{-z}\vert
```

Using orthogonality:

```math
\langle\psi\vert \hat{Z}\vert \psi\rangle
= \alpha^*\cdot(+1)\alpha + \beta^*\cdot(-1)\beta
= (+1)\vert\alpha\vert^2 + (-1)\vert\beta\vert^2
```

$\vert\alpha\vert^2$ is the probability of measurement value $+1$, and $\vert\beta\vert^2$ is the probability of measurement value $-1$. Thus $\langle\psi\vert \hat{Z}\vert \psi\rangle$ is the sum of "each measurement value × its probability" — precisely the expectation value.

<table border="1" align="center"><tr><td markdown="1">

```math
\langle\psi\vert \hat{Z}\vert \psi\rangle = \sum_i (\text{eigenvalue}_i) \times (\text{its probability})
```

</td></tr></table>

This holds not only for $\hat{Z}$ but for any measurement operator in general.

### Matrix Representation

Choose these two states as the computational basis:

```math
\vert {+z}\rangle = \begin{pmatrix}1\\0\end{pmatrix}, \qquad
\vert {-z}\rangle = \begin{pmatrix}0\\1\end{pmatrix}
```

Then the matrix representation of $\hat{Z}$ is

```math
\sigma_z =
\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}
```

This is the first Pauli matrix $\sigma_z$ — it is simply the fact that "$z$-direction measurement gives two values" translated directly into a matrix.

### Arbitrary States

Here we shift our perspective. In the Stern–Gerlach experiments described so far, many silver atoms were sent through as a beam, and results were read from the statistical distribution on the screen. But the essence of quantum theory is that the state vectors $\vert {+z}\rangle$, $\vert {-z}\rangle$ are meaningful even for **a single silver atom**. States belong to individual particles, not to statistical ensembles.

Recall Experiment B. A single silver atom confirmed to be on the upper side in the $z$-direction is measured in the $x$-direction; the result is either $+1$ or $-1$, and which one comes out is unknown until the measurement is performed. This silver atom is neither $\vert {+x}\rangle$ nor $\vert {-x}\rangle$. Nor is it easy to say "it is really one or the other, we just don't know" — because, as Experiment C showed, the $x$-measurement destroys the $z$-information (the question of "wasn't it determined in advance?" is ultimately settled by Bell's inequality, treated in [NOTE5.md](NOTE5.md)). In quantum theory, this situation is expressed as a **superposition** of the two basis states.

Since the basis for the 2-dimensional space has been fixed, the arbitrary state of a single silver atom is

```math
\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle
= \begin{pmatrix}\alpha\\\beta\end{pmatrix}
```

where $\alpha, \beta$ are complex numbers. To repeat: this is not "a mixture of silver atoms going up and going down as a population." **A single silver atom** possesses the properties of both $\vert {+z}\rangle$ and $\vert {-z}\rangle$ in superposition until measured — that is the meaning of the quantum-mechanical state.

By the way, the basis vectors themselves were normalized ($\langle{+z}\vert {+z}\rangle = 1$, etc.). For a general state vector, we impose the same normalization condition:

```math
\langle\psi\vert \psi\rangle = \vert \alpha\vert ^2 + \vert \beta\vert ^2 = 1
```

This is naturally required by the Born rule — as we saw, $\vert \alpha\vert ^2$ and $\vert \beta\vert ^2$ are the probabilities of each measurement outcome, and probabilities must sum to 1.

---

## Stage 3: From $x$-Direction Measurement to the Form of Eigenstates

### Experimental Facts

A particle selected to be on the upper side in the $z$-direction is now sent through an $x$-direction device. The result:

- Upper and lower in the $x$-direction appear **50-50**

Furthermore:

- Selecting the upper side in $x$ and measuring $x$ again always gives upper
- But after that, measuring $z$ gives 50-50 again

Thus $z$ and $x$ cannot be simultaneously definite, and $x$ has its own two definite states.

### Expressing the $x$ Eigenstates in the $z$ Basis

In the $x$-direction there are also two eigenstates $\vert {+x}\rangle$, $\vert {-x}\rangle$. Since they live in the same 2-dimensional space, they can be written in the $z$ basis:

```math
\vert {+x}\rangle = a\vert {+z}\rangle + b\vert {-z}\rangle
```

We want to express the result of Experiment B — "$\vert {+z}\rangle$ silver atoms passed through an $x$-direction device give $+1$ and $-1$ in equal proportion" — as an equation. Using the Born rule ($P(\phi) = \vert \langle\phi\vert \psi\rangle\vert ^2$), the "50-50" condition is

```math
\vert \langle{+x}\vert {+z}\rangle\vert ^2 = \frac{1}{2}
```

Since $\langle{+x}\vert {+z}\rangle = a^*$, we get $\vert a\vert ^2 = 1/2$. From the normalization $\vert a\vert ^2 + \vert b\vert ^2 = 1$, we also get $\vert b\vert ^2 = 1/2$.

Therefore

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(e^{i\alpha}\vert {+z}\rangle + e^{i\beta}\vert {-z}\rangle\bigr)
```

Here $e^{i\alpha}$, $e^{i\beta}$ are coefficients that disappear when squared to find probabilities — $\vert e^{i\alpha}\vert ^2 = 1$ — meaning they are "decorations" that do not affect probabilities. Such coefficients are called phase factors.

### Counting the Phase Degrees of Freedom

In quantum mechanics, multiplying the entire state vector by a common phase $e^{i\gamma}$ does not change the physics. Computing probabilities with the Born rule: $\vert \langle\phi\vert e^{i\gamma}\psi\rangle\vert ^2 = \vert e^{i\gamma}\vert ^2\vert \langle\phi\vert \psi\rangle\vert ^2 = \vert \langle\phi\vert \psi\rangle\vert ^2$, so the overall phase cancels out — there is no way to observe the difference in overall phase through any measurement. Using this freedom, we can choose $e^{i\alpha} = 1$. Then

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

Only the **relative phase** $e^{i\phi}$ remains.

In other words, infinitely many states satisfy the condition "50-50 as seen from $z$," and they are distinguished by the relative phase $\phi$.

---

### Choosing a Phase Convention to Fix $\sigma_x$

### What Does the Choice of $\phi$ Mean Physically?

States with different relative phases $\phi$ cannot be distinguished by $z$-measurement (all give 50-50). However, they can be distinguished by measurement in another direction. For example, the state $\phi = 0$ corresponds to $\vert {+x}\rangle$ and $\phi = \pi$ to $\vert {-x}\rangle$ — both give 50-50 in $z$-measurement, but in $x$-measurement one always returns $+1$ and the other always returns $-1$. Therefore $\phi$ is a physically meaningful quantity.

In defining the $x$-axis direction, we choose a phase convention. **We call the direction whose eigenstates have real coefficients in the $z$ basis the $x$-direction.** That is, we choose

```math
\phi = 0
```

Substituting $\phi = 0$ into the previous expression $\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)$, since $e^{i \cdot 0} = 1$:

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + \vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
```

Next we find $\vert {-x}\rangle$. As discussed in the previous section "What Does the Choice of $\phi$ Mean Physically?", $\vert {-x}\rangle$ corresponds to $\phi = \pi$, so substituting $\phi = \pi$ into the same formula gives $e^{i\pi} = -1$:

```math
\vert {-x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle - \vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
```

The orthogonality condition $\langle{-x}\vert {+x}\rangle = \frac{1}{2}(1 \cdot 1 + (-1) \cdot 1) = 0$ is indeed satisfied.

### Why Is This a "Convention"?

"Choosing $\phi = 0$" means naming one direction perpendicular to the $z$-axis in 3-dimensional space as the $x$-axis. Since the $z$-axis alone does not determine the orientation within the horizontal plane, which direction is called $x$ must be chosen as a convention. $\phi = 0$ is that choice, not a physical law.

### Writing Down $\sigma_x$

We construct the operator that has eigenvalue $+1$ for $\vert {+x}\rangle$ and eigenvalue $-1$ for $\vert {-x}\rangle$:

```math
\hat{X} = (+1)\vert {+x}\rangle\langle{+x}\vert + (-1)\vert {-x}\rangle\langle{-x}\vert 
```

Converting each term to a matrix in the $z$ basis:

```math
\vert {+x}\rangle\langle{+x}\vert 
= \frac{1}{2}\begin{pmatrix}1\\1\end{pmatrix}(1\;1)
= \frac{1}{2}\begin{pmatrix}1&1\\1&1\end{pmatrix}
```

```math
\vert {-x}\rangle\langle{-x}\vert 
= \frac{1}{2}\begin{pmatrix}1\\-1\end{pmatrix}(1\;{-1})
= \frac{1}{2}\begin{pmatrix}1&-1\\-1&1\end{pmatrix}
```

Therefore

```math
\hat{X}
= \frac{1}{2}\begin{pmatrix}1&1\\1&1\end{pmatrix}
- \frac{1}{2}\begin{pmatrix}1&-1\\-1&1\end{pmatrix}
= \begin{pmatrix}0&1\\1&0\end{pmatrix}
```

This is

```math
\sigma_x = \begin{pmatrix}0&1\\1&0\end{pmatrix}
```

### Verification

We directly verify the eigenvalue equations:

```math
\sigma_x\,\vert {+x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= +1 \cdot \vert {+x}\rangle \quad\checkmark
```

```math
\sigma_x\,\vert {-x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\1\end{pmatrix}
= -1 \cdot \vert {-x}\rangle \quad\checkmark
```

---

## Stage 4: The $y$-Direction Requires Complex Numbers

### Why $y$ Is Not the Same as $x$

In 3-dimensional space there are two directions perpendicular to $z$ ($x$ and $y$). From the viewpoint of $z$, both $x$ and $y$ are on equal footing, and both give:

- 50-50 when measuring $\vert {+z}\rangle$

So are $x$ and $y$ the same thing?

The answer is no. Since $x$ and $y$ are measurements in **different directions**, they must have **different eigenstates**. However, the condition "50-50 as seen from $z$" only tells us $\vert a\vert ^2 = \vert b\vert ^2 = 1/2$; the difference lies only in the relative phase.

$x$ already uses $\phi = 0$. If $y$ is to differ from $x$, we must have $\phi \neq 0$.

### Assigning $y$ to $\phi = \pi/2$

The $y$-axis is the direction rotated 90 degrees from the $x$-axis. Here we assume that the relative phase $\phi$ of the state vector corresponds directly to the azimuthal angle in real space. This correspondence appears natural, but is in fact rigorously justified only by using the geometric structure of the rotation operator — in [NOTE3.md](NOTE3.md) we show that the relative phase $\phi$ coincides with the azimuthal angle of the Bloch sphere, and in [NOTE4.md](NOTE4.md) we concretely verify that rotation about the $z$-axis actually moves the azimuthal angle. For now, let us accept this correspondence and proceed.

Since $x$ was assigned $\phi = 0$, $y$ corresponds to

```math
\phi = \frac{\pi}{2}
```

Substituting $\phi = \pi/2$ into the same formula $\frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)$ used in the derivation of $\vert {+x}\rangle$, since $e^{i\pi/2} = i$:

```math
\vert {+y}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + i\vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
```

Similarly, $\vert {-y}\rangle$ corresponds to $\phi = \pi/2 + \pi = 3\pi/2$. Since $e^{i \cdot 3\pi/2} = -i$:

```math
\vert {-y}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle - i\vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
```

Let us verify orthogonality: $\langle{-y}\vert {+y}\rangle = \frac{1}{2}(1 \cdot 1 + i \cdot i) = \frac{1}{2}(1 - 1) = 0$.

### Why Does $i$ Appear?

The $i$ is not an arbitrary invention. The general state that is "50-50 as seen from $z$" is

```math
\vert \psi(\phi)\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

and $\phi$ is the azimuthal angle on the equator. If $x$ is $\phi = 0$, then $y$, which is 90 degrees around from there, is $\phi = \pi/2$, and

```math
e^{i\pi/2} = i
```

— that is all.

### Why Real Numbers Are Not Enough

If we restrict the coefficients to be real, the relative phase can only be $+1$ or $-1$. $+1$ is already used by $x$. Using $-1$ gives the same state as $\vert {-x}\rangle$.

In other words, with only real numbers, we can represent only one independent direction perpendicular to $z$. More precisely, the traceless Hermitian matrices (matrices whose diagonal entries sum to zero, and which equal their own conjugate transpose) that can be formed from real $2 \times 2$ matrices are limited to real-coefficient combinations of $\sigma_z$ and $\sigma_x$, and cannot include a third independent component $\sigma_y$. To represent measurements in three directions within a 2-dimensional space, complex numbers — namely $i$ — are indispensable.

### Verification of Measurement Statistics

Let us verify that $\vert {+y}\rangle$, $\vert {-y}\rangle$ do not contradict the experimental facts.

Measuring $\vert {+x}\rangle$ in the $y$-direction:

```math
\langle{+y}\vert {+x}\rangle
= \frac{1}{\sqrt{2}}(1,\,-i) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{2}(1 - i)
```

```math
\vert \langle{+y}\vert {+x}\rangle\vert ^2
= \left\vert \frac{1-i}{2}\right\vert ^2
= \frac{1+1}{4}
= \frac{1}{2} \quad\checkmark
```

Measuring $\vert {+y}\rangle$ in the $x$-direction:

```math
\langle{+x}\vert {+y}\rangle
= \frac{1}{\sqrt{2}}(1,\,1) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{2}(1 + i)
```

```math
\vert \langle{+x}\vert {+y}\rangle\vert ^2
= \left\vert \frac{1+i}{2}\right\vert ^2
= \frac{1}{2} \quad\checkmark
```

Measuring $\vert {+y}\rangle$ in the $z$-direction:

```math
\vert \langle{+z}\vert {+y}\rangle\vert ^2
= \left\vert \frac{1}{\sqrt{2}}\right\vert ^2
= \frac{1}{2} \quad\checkmark
```

For any pair among $x$, $y$, $z$, measuring an eigenstate of one direction in another gives 50-50. This symmetry shows that the choice of assigning $y$ to $\phi = \pi/2$ is consistent with experiment.

### Writing Down $\sigma_y$

We construct the operator that has eigenvalue $+1$ for $\vert {+y}\rangle$ and eigenvalue $-1$ for $\vert {-y}\rangle$:

```math
\hat{Y} = (+1)\vert {+y}\rangle\langle{+y}\vert + (-1)\vert {-y}\rangle\langle{-y}\vert 
```

Computing each term in the $z$ basis:

```math
\vert {+y}\rangle\langle{+y}\vert 
= \frac{1}{2}\begin{pmatrix}1\\i\end{pmatrix}(1\;{-i})
= \frac{1}{2}\begin{pmatrix}1&-i\\i&1\end{pmatrix}
```

```math
\vert {-y}\rangle\langle{-y}\vert 
= \frac{1}{2}\begin{pmatrix}1\\-i\end{pmatrix}(1\;{i})
= \frac{1}{2}\begin{pmatrix}1&i\\-i&1\end{pmatrix}
```

Therefore

```math
\hat{Y}
= \frac{1}{2}\begin{pmatrix}1&-i\\i&1\end{pmatrix}
- \frac{1}{2}\begin{pmatrix}1&i\\-i&1\end{pmatrix}
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

This is

```math
\sigma_y = \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

### Verification

```math
\sigma_y\,\vert {+y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-i^2\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= +1 \cdot \vert {+y}\rangle \quad\checkmark
```

```math
\sigma_y\,\vert {-y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}0\cdot 1 + (-i)(-i)\\i\cdot 1 + 0\cdot(-i)\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}i^2\\i\end{pmatrix}
```

Since $(-i)(-i) = i^2 = -1$:

```math
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\i\end{pmatrix}
= -\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= -1\cdot\vert {-y}\rangle \quad\checkmark
```

---

## Stage 5: The Three Matrices Are Spin Operators

### Summary So Far

From experimental facts and phase conventions alone, three matrices have been determined:

```math
\sigma_z = \begin{pmatrix}1&0\\0&-1\end{pmatrix}, \qquad
\sigma_x = \begin{pmatrix}0&1\\1&0\end{pmatrix}, \qquad
\sigma_y = \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

These were introduced as "matrices representing the two-valued measurement in each direction." However, verifying that they satisfy the angular momentum commutation relations reveals a deeper significance.

### Computing the Commutation Relations

Let us directly compute the commutation relations among the three Pauli matrices. The commutator is defined as $[A, B] = AB - BA$.

First, compute $[\sigma_x, \sigma_y]$:

```math
\sigma_x\sigma_y
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\begin{pmatrix}0&-i\\i&0\end{pmatrix}
= \begin{pmatrix}i&0\\0&-i\end{pmatrix}
```

```math
\sigma_y\sigma_x
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\begin{pmatrix}0&1\\1&0\end{pmatrix}
= \begin{pmatrix}-i&0\\0&i\end{pmatrix}
```

Therefore

```math
[\sigma_x, \sigma_y]
= \sigma_x\sigma_y - \sigma_y\sigma_x
= \begin{pmatrix}2i&0\\0&-2i\end{pmatrix}
= 2i\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= 2i\,\sigma_z
```

Similarly (the procedure is just matrix multiplication, so we show only the results):

```math
[\sigma_y, \sigma_z] = 2i\,\sigma_x, \qquad
[\sigma_z, \sigma_x] = 2i\,\sigma_y
```

Summarizing:

<table border="1" align="center"><tr><td markdown="1">

```math
[\sigma_i, \sigma_j] = 2i\,\epsilon_{ijk}\,\sigma_k
```

</td></tr></table>

Here $\epsilon_{ijk}$ is the completely antisymmetric tensor (Levi-Civita symbol), which encodes the sign under permutation of indices. Specifically, with $i, j, k$ standing for $1, 2, 3$ (i.e., $x, y, z$):

- $\epsilon_{123} = \epsilon_{231} = \epsilon_{312} = +1$ (cyclic order)
- $\epsilon_{213} = \epsilon_{132} = \epsilon_{321} = -1$ (swapping two adjacent indices flips the sign)
- If any indices repeat, the value is $0$ (e.g., $\epsilon_{112} = 0$)

### Connection to Spin Operators

Setting

```math
S_i = \frac{\hbar}{2}\,\sigma_i
```

we get

```math
[S_i, S_j]
= \frac{\hbar^2}{4}[\sigma_i, \sigma_j]
= \frac{\hbar^2}{4}\cdot 2i\,\epsilon_{ijk}\,\sigma_k
= i\hbar\,\epsilon_{ijk}\,\frac{\hbar}{2}\sigma_k
= i\hbar\,\epsilon_{ijk}\,S_k
```

That is,

<table border="1" align="center"><tr><td markdown="1">

```math
[S_i, S_j] = i\hbar\,\epsilon_{ijk}\,S_k
```

</td></tr></table>

This is precisely the **angular momentum commutation relation**.

Why is this commutation relation important — that is, why does satisfying it constitute proof of "being angular momentum" — is explained in the next document [NOTE2.md](NOTE2.md) where we derive the general rotation operator, and discussed in detail in [NOTE4.md](NOTE4.md).

Here we state only the conclusion. The three Pauli matrices are established as the operators for spin 1/2 in the following threefold sense:

- Their form is determined by experimental facts (two-valued measurement, 50-50 statistics)
- That form automatically satisfies the angular momentum commutation relations
- Moreover, in 2 dimensions, this is essentially the only representation satisfying the commutation relations (uniqueness of the 2-dimensional irreducible representation of $\mathrm{SU}(2)$)

---

## Summary: What Is Experimental Fact and What Is Convention

Let us organize what was used in the derivation.

### Experimental Facts (Cannot Be Changed)

- The result of measurement in each direction is two-valued ($+1$ and $-1$)
- Re-measurement in the same direction reproduces the result
- Measurements in perpendicular directions give 50-50 probability (for a general angle, $\cos^2(\theta/2)$)
- Interposing a measurement in one direction destroys information about the other

### Conventions (Other Choices Are Possible)

- The choice of basis $\vert {+z}\rangle = (1,0)^T$, $\vert {-z}\rangle = (0,1)^T$
- Writing the $x$-direction eigenstates with real coefficients ($\phi = 0$)
- The right-hand rule places $y$ at 90 degrees counterclockwise from $x$ ($\phi = \pi/2$) — the correspondence between relative phase and real-space azimuthal angle is confirmed by the Bloch sphere in [NOTE3.md](NOTE3.md) and the rotation operator in [NOTE4.md](NOTE4.md)

### Derived Results

- The matrix forms of $\sigma_z, \sigma_x, \sigma_y$
- That $S_i = \hbar\sigma_i/2$ satisfies the angular momentum commutation relations
- By the uniqueness of the 2-dimensional irreducible representation, this is the only representation for spin 1/2

---

## Logical Structure (Review)

```
Stern–Gerlach experiment: beam splits into two
    ↓
Two eigenstates |+z⟩, |−z⟩ become the basis
    ↓
Writing the measurement operator gives σ_z
    ↓
x-measurement gives 50-50 → the form of |+x⟩ is constrained to |a|=|b|=1/√2
    ↓
Relative phase e^{iφ} remains → choose φ=0 as the convention for x
    ↓
σ_x is determined
    ↓
y-direction requires φ≠0 → real numbers are insufficient → φ=π/2 gives i
    ↓
σ_y is determined
    ↓
Computing the three commutation relations → matches the angular momentum algebra
    ↓
Uniqueness of the 2-dim irreducible representation of SU(2) → confirmed as spin 1/2 operators
```

Once the minimal quantum-mechanical framework (complex vector space, Born rule, etc.) is accepted, experimental facts narrow down the matrix forms, conventions fix the remaining freedom, and commutation relations guarantee the identification with spin — the Pauli matrices do not descend from the sky, but are determined naturally, guided by experiment.

---
