# ベルの不等式：量子力学が古典的直観を越える場所

> **シリーズ構成**: [実験からパウリ行列へ](CLAUDE_PHYSICS.md) → [回転演算子](CLAUDE_PHYSICS2.md) → [θ/2 の由来](CLAUDE_PHYSICS3.md) → 本文書（CLAUDE_PHYSICS4.md）

## この文書の方針

この文書は、CLAUDE_PHYSICS シリーズの知識だけを使って、ベルの不等式を導く。

使う道具は

- 状態ベクトルと測定（[CLAUDE_PHYSICS.md](CLAUDE_PHYSICS.md)）
- パウリ行列 $\sigma_x, \sigma_y, \sigma_z$ と方向 $\mathbf{n}$ の測定 $\mathbf{n}\cdot\boldsymbol{\sigma}$ （[CLAUDE_PHYSICS.md](CLAUDE_PHYSICS.md)）
- スピン回転と固有状態の変換（[CLAUDE_PHYSICS3.md](CLAUDE_PHYSICS3.md)）

だけである。新たに導入するのは「2粒子系の状態をどう書くか」だけで、それ以外は既知の道具の組み合わせで話が進む。

---

## 全体の筋

流れは6段階ある。

1. **2粒子の状態空間** → 1粒子ずつ 2 次元なので、合わせて 4 次元になる
2. **シングレット状態** → 完全に反相関する特別な2粒子状態
3. **量子力学の予測** → Alice と Bob が異なる方向で測ったときの相関を計算する
4. **古典的な説明の試み** → 「粒子は最初から答えを持っていた」という仮説
5. **CHSH 不等式** → その仮説から導かれる相関の上限 $\vert S\vert \leq 2$
6. **量子力学の破り** → 量子力学は $\vert S\vert = 2\sqrt{2}$ を予測し、上限を超える

---

## 第1段階：2粒子の状態空間

### 1粒子の復習

[CLAUDE_PHYSICS.md](CLAUDE_PHYSICS.md) で見たように、1粒子のスピン状態は 2 次元空間に住んでいる。 $z$ 基底は

```math
\vert {+z}\rangle = \begin{pmatrix}1\\0\end{pmatrix}, \qquad
\vert {-z}\rangle = \begin{pmatrix}0\\1\end{pmatrix}
```

であり、任意の状態は $\alpha\vert {+z}\rangle + \beta\vert {-z}\rangle$ と書ける。

### 2粒子を同時に記述する

いま、2つのスピン 1/2 粒子がある。Alice が1番目の粒子を、Bob が2番目の粒子を持っているとする。

2粒子系の状態を書くには、両方の粒子の状態を同時に指定する必要がある。たとえば「Alice の粒子が $\vert {+z}\rangle$ で、Bob の粒子が $\vert {-z}\rangle$ 」という状態を

```math
\vert {+z}\rangle \otimes \vert {-z}\rangle
```

と書く。 $\otimes$ は「テンソル積」と呼ばれるが、ここでは「かつ」と読めばよい。表記を短くするために

```math
\vert {+z}\rangle\vert {-z}\rangle \quad \text{あるいは} \quad \vert {+z},{-z}\rangle
```

とも書く。

### 基底は4つ

各粒子に $\vert {+z}\rangle$ と $\vert {-z}\rangle$ の2通りがあるので、2粒子系の基底は $2 \times 2 = 4$ 個になる。

```math
\vert {+z}\rangle\vert {+z}\rangle, \qquad
\vert {+z}\rangle\vert {-z}\rangle, \qquad
\vert {-z}\rangle\vert {+z}\rangle, \qquad
\vert {-z}\rangle\vert {-z}\rangle
```

任意の2粒子状態は、この4つの線形結合で書ける。

### 積状態ともつれ状態

もし2粒子の状態が

```math
\vert \Psi\rangle = \vert \psi\rangle_A \otimes \vert \phi\rangle_B
```

のように「Alice の状態」と「Bob の状態」の積に分解できるなら、これを**積状態**と呼ぶ。積状態では、Alice と Bob の粒子はそれぞれ独立な状態を持っている。

しかし、4次元空間には積に分解できない状態も存在する。たとえば

```math
\frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle\vert {-z}\rangle - \vert {-z}\rangle\vert {+z}\rangle\bigr)
```

は、どのような $\vert \psi\rangle_A$ と $\vert \phi\rangle_B$ を持ってきても積の形に書けない。このような状態を**もつれ状態（エンタングル状態）**と呼ぶ。

---

## 第2段階：シングレット状態

### 定義

2粒子のもつれ状態の中で、最も重要なものの一つが**シングレット状態**である。

```math
\vert \Psi^-\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle\vert {-z}\rangle - \vert {-z}\rangle\vert {+z}\rangle\bigr)
```

ここで左のケットが Alice の粒子、右のケットが Bob の粒子である。

この状態は「Alice が $+z$ で Bob が $-z$ 」という成分と「Alice が $-z$ で Bob が $+z$ 」という成分の重ね合わせになっている。

### 同じ方向で測ると必ず逆になる

Alice と Bob が両方とも $z$ 方向で測定したとき、何が起こるかを見る。

$\vert \Psi^-\rangle$ の第1項 $\vert {+z}\rangle\vert {-z}\rangle$ は「Alice が $+1$ 、Bob が $-1$ 」を返し、第2項 $\vert {-z}\rangle\vert {+z}\rangle$ は「Alice が $-1$ 、Bob が $+1$ 」を返す。どちらの項でも、Alice と Bob の結果は逆である。

したがって、シングレット状態では $z$ 方向の測定に対して**完全な反相関**がある。Alice が $+1$ なら Bob は必ず $-1$ 、Alice が $-1$ なら Bob は必ず $+1$ である。

### 回転不変性：どの方向でも同じことが成り立つ

実は、シングレット状態には驚くべき性質がある。上の完全反相関は $z$ 方向に限らず、**任意の方向で成り立つ**。

これを確かめるには、任意の方向 $\mathbf{a}$ の固有状態で $\vert \Psi^-\rangle$ を書き直してみればよい。 $\mathbf{a}$ が $z$ 軸から角度 $\theta_a$ の方向にあるとする（ $xz$ 平面内とする）。

方向 $\mathbf{a}$ の固有状態 $\vert {+a}\rangle$ は、 $\vert {+z}\rangle$ を $y$ 軸まわりに $\theta_a$ だけ回転させたものである。[CLAUDE_PHYSICS3.md](CLAUDE_PHYSICS3.md) の回転行列

```math
U(\theta, \mathbf{n}) = \cos\frac{\theta}{2}\,I - i\sin\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
```

で $\mathbf{n} = \hat{y}$, $\theta = \theta_a$ とすると

```math
U(\theta_a, \hat{y})
= \cos\frac{\theta_a}{2}\,I - i\sin\frac{\theta_a}{2}\,\sigma_y
= \cos\frac{\theta_a}{2}\begin{pmatrix}1&0\\0&1\end{pmatrix}
- i\sin\frac{\theta_a}{2}\begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

$-i \cdot (-i) = i^2 = -1$ と $-i \cdot i = -i^2 = 1$ に注意すると

```math
= \begin{pmatrix}
\cos\frac{\theta_a}{2} & -\sin\frac{\theta_a}{2} \\[4pt]
\sin\frac{\theta_a}{2} & \cos\frac{\theta_a}{2}
\end{pmatrix}
```

これを $\vert {+z}\rangle$ に作用させる。

```math
\vert {+a}\rangle = U(\theta_a, \hat{y})\,\vert {+z}\rangle
= \begin{pmatrix}
\cos\frac{\theta_a}{2} & -\sin\frac{\theta_a}{2} \\[4pt]
\sin\frac{\theta_a}{2} & \cos\frac{\theta_a}{2}
\end{pmatrix}
\begin{pmatrix}1\\0\end{pmatrix}
= \begin{pmatrix}\cos\frac{\theta_a}{2}\\[4pt]\sin\frac{\theta_a}{2}\end{pmatrix}
```

すなわち

```math
\vert {+a}\rangle = \cos\frac{\theta_a}{2}\,\vert {+z}\rangle + \sin\frac{\theta_a}{2}\,\vert {-z}\rangle
```

同様に $\vert {-a}\rangle = U(\theta_a, \hat{y})\,\vert {-z}\rangle$ は

```math
\vert {-a}\rangle
= \begin{pmatrix}
\cos\frac{\theta_a}{2} & -\sin\frac{\theta_a}{2} \\[4pt]
\sin\frac{\theta_a}{2} & \cos\frac{\theta_a}{2}
\end{pmatrix}
\begin{pmatrix}0\\1\end{pmatrix}
= \begin{pmatrix}-\sin\frac{\theta_a}{2}\\[4pt]\cos\frac{\theta_a}{2}\end{pmatrix}
```

すなわち

```math
\vert {-a}\rangle = -\sin\frac{\theta_a}{2}\,\vert {+z}\rangle + \cos\frac{\theta_a}{2}\,\vert {-z}\rangle
```

である。空間的には $\theta_a$ だけ回転しているが、状態ベクトルの係数には $\theta_a/2$ が現れる。これは [CLAUDE_PHYSICS3.md](CLAUDE_PHYSICS3.md) で見たスピノルの半角構造そのものである。 $c = \cos(\theta_a/2)$, $s = \sin(\theta_a/2)$ と略記すると

```math
\vert {+a}\rangle\vert {-a}\rangle
= (c\vert {+z}\rangle + s\vert {-z}\rangle)(-s\vert {+z}\rangle + c\vert {-z}\rangle)
```

```math
= -cs\vert {+z}\rangle\vert {+z}\rangle + c^2\vert {+z}\rangle\vert {-z}\rangle - s^2\vert {-z}\rangle\vert {+z}\rangle + sc\vert {-z}\rangle\vert {-z}\rangle
```

```math
\vert {-a}\rangle\vert {+a}\rangle
= (-s\vert {+z}\rangle + c\vert {-z}\rangle)(c\vert {+z}\rangle + s\vert {-z}\rangle)
```

```math
= -sc\vert {+z}\rangle\vert {+z}\rangle - s^2\vert {+z}\rangle\vert {-z}\rangle + c^2\vert {-z}\rangle\vert {+z}\rangle + cs\vert {-z}\rangle\vert {-z}\rangle
```

差を取る。

```math
\vert {+a}\rangle\vert {-a}\rangle - \vert {-a}\rangle\vert {+a}\rangle
```

$\vert {+z}\rangle\vert {+z}\rangle$ の係数： $-cs - (-sc) = 0$

$\vert {+z}\rangle\vert {-z}\rangle$ の係数： $c^2 - (-s^2) = c^2 + s^2 = 1$

$\vert {-z}\rangle\vert {+z}\rangle$ の係数： $-s^2 - c^2 = -(s^2 + c^2) = -1$

$\vert {-z}\rangle\vert {-z}\rangle$ の係数： $sc - cs = 0$

したがって

```math
\vert {+a}\rangle\vert {-a}\rangle - \vert {-a}\rangle\vert {+a}\rangle
= \vert {+z}\rangle\vert {-z}\rangle - \vert {-z}\rangle\vert {+z}\rangle
```

両辺を $\sqrt{2}$ で割ると

```math
\boxed{
\frac{1}{\sqrt{2}}\bigl(\vert {+a}\rangle\vert {-a}\rangle - \vert {-a}\rangle\vert {+a}\rangle\bigr)
= \vert \Psi^-\rangle
}
```

シングレット状態は、 $z$ 基底で書いても $\mathbf{a}$ 基底で書いても同じ形になる。これが**回転不変性**である。

この結果から、Alice がどの方向 $\mathbf{a}$ で測定しても、Bob の粒子は Alice と反対の状態に決まる。

- Alice が $\mathbf{a}$ 方向で $+1$ を得る → Bob の粒子は $\vert {-a}\rangle$ になる
- Alice が $\mathbf{a}$ 方向で $-1$ を得る → Bob の粒子は $\vert {+a}\rangle$ になる

いずれも確率 $1/2$ である。

---

## 第3段階：異なる方向で測ったときの相関

### 問いの設定

Alice は方向 $\mathbf{a}$ で、Bob は方向 $\mathbf{b}$ で測定する。2つの方向の間の角度を $\theta$ とする。

同じ方向なら完全反相関（ $+1$ と $-1$ のペアが必ず出る）。では方向が異なるときは？

各測定の結果を $A = \pm 1$ （Alice）、 $B = \pm 1$ （Bob）とし、その積の期待値

```math
E(\mathbf{a}, \mathbf{b}) = \langle A \cdot B \rangle
```

を計算する。これが**相関**である。

- $E = -1$ ：完全反相関（必ず逆）
- $E = +1$ ：完全正相関（必ず同じ）
- $E = 0$ ：無相関

### 計算

回転不変性から、Alice が $\mathbf{a}$ 方向で測定したとき

- 結果が $+1$ （確率 $1/2$ ）→ Bob の粒子は $\vert {-a}\rangle$
- 結果が $-1$ （確率 $1/2$ ）→ Bob の粒子は $\vert {+a}\rangle$

Bob は方向 $\mathbf{b}$ で測定する。 $\mathbf{a}$ と $\mathbf{b}$ の間の角度を $\theta$ とする。

**Alice が $+1$ のとき（Bob の粒子は $\vert {-a}\rangle$ ）：**

Bob が $+1$ を得る確率は $\vert \langle{+b}\vert {-a}\rangle\vert ^2$ 、 $-1$ を得る確率は $\vert \langle{-b}\vert {-a}\rangle\vert ^2$ である。

$\mathbf{a}$ と $\mathbf{b}$ が同じ $xz$ 平面内にあるとし、 $z$ 軸からの角度をそれぞれ $\theta_a$, $\theta_b$ とする（ $\theta = \theta_b - \theta_a$ ）。[CLAUDE_PHYSICS3.md](CLAUDE_PHYSICS3.md) の回転から

```math
\vert {+b}\rangle = \cos\frac{\theta_b}{2}\vert {+z}\rangle + \sin\frac{\theta_b}{2}\vert {-z}\rangle
```

```math
\vert {-a}\rangle = -\sin\frac{\theta_a}{2}\vert {+z}\rangle + \cos\frac{\theta_a}{2}\vert {-z}\rangle
```

内積を計算する。

```math
\langle{+b}\vert {-a}\rangle
= -\cos\frac{\theta_b}{2}\sin\frac{\theta_a}{2} + \sin\frac{\theta_b}{2}\cos\frac{\theta_a}{2}
= \sin\frac{\theta_b - \theta_a}{2}
= \sin\frac{\theta}{2}
```

ここで加法定理 $\sin\alpha\cos\beta - \cos\alpha\sin\beta = \sin(\alpha - \beta)$ を使った。

同様に

```math
\langle{-b}\vert {-a}\rangle
= \sin\frac{\theta_b}{2}\sin\frac{\theta_a}{2} + \cos\frac{\theta_b}{2}\cos\frac{\theta_a}{2}
= \cos\frac{\theta_b - \theta_a}{2}
= \cos\frac{\theta}{2}
```

したがって

```math
P(B = +1 \mid A = +1) = \sin^2\frac{\theta}{2}, \qquad
P(B = -1 \mid A = +1) = \cos^2\frac{\theta}{2}
```

**Alice が $-1$ のとき（Bob の粒子は $\vert {+a}\rangle$ ）：**

同じ計算を繰り返す。

```math
\langle{+b}\vert {+a}\rangle
= \cos\frac{\theta_b}{2}\cos\frac{\theta_a}{2} + \sin\frac{\theta_b}{2}\sin\frac{\theta_a}{2}
= \cos\frac{\theta}{2}
```

```math
P(B = +1 \mid A = -1) = \cos^2\frac{\theta}{2}, \qquad
P(B = -1 \mid A = -1) = \sin^2\frac{\theta}{2}
```

### 相関を組み立てる

```math
E(\mathbf{a}, \mathbf{b})
= \sum_{A,B = \pm 1} A \cdot B \cdot P(A, B)
```

Alice の結果は等確率（各 $1/2$ ）なので

```math
E = \frac{1}{2}\Bigl[(+1)(+1)\sin^2\frac{\theta}{2} + (+1)(-1)\cos^2\frac{\theta}{2}\Bigr]
  + \frac{1}{2}\Bigl[(-1)(+1)\cos^2\frac{\theta}{2} + (-1)(-1)\sin^2\frac{\theta}{2}\Bigr]
```

各項を整理する。

```math
= \frac{1}{2}\Bigl[\sin^2\frac{\theta}{2} - \cos^2\frac{\theta}{2}\Bigr]
+ \frac{1}{2}\Bigl[-\cos^2\frac{\theta}{2} + \sin^2\frac{\theta}{2}\Bigr]
```

```math
= \sin^2\frac{\theta}{2} - \cos^2\frac{\theta}{2}
```

ここで $\cos\theta = \cos^2(\theta/2) - \sin^2(\theta/2)$ なので

```math
\boxed{
E(\mathbf{a}, \mathbf{b}) = -\cos\theta = -\mathbf{a}\cdot\mathbf{b}
}
```

### 確認

- $\theta = 0$ （同方向）： $E = -1$ （完全反相関） ✓
- $\theta = \pi$ （逆方向）： $E = +1$ （完全正相関） ✓
- $\theta = \pi/2$ （直交）： $E = 0$ （無相関） ✓

---

## 第4段階：古典的な説明の試み

### アインシュタインの問い

ここで立ち止まって考える。

Alice が方向 $\mathbf{a}$ で測定すると、Bob の粒子は即座に $\vert {-a}\rangle$ （または $\vert {+a}\rangle$ ）に決まる。Alice と Bob がどれほど離れていても、である。

しかし Alice の測定が Bob の粒子に物理的な影響を与えるわけではない（特殊相対論により、光より速い影響伝達はない）。

ならば、Bob の粒子は**最初から答えを持っていた**と考えるほうが自然ではないか。

これがアインシュタイン・ポドルスキー・ローゼン（EPR）の議論である。

### 隠れた変数の仮説

EPR の議論を数学的にまとめると、次のような仮説になる。

> 2つの粒子が作られた瞬間に、各粒子には**すべての方向に対する測定結果が事前に決まっている**。この事前の値を決めるのが隠れた変数 $\lambda$ である。

具体的には

- Alice が方向 $\mathbf{a}$ で測ると、結果は事前に決まった値 $A(\mathbf{a}, \lambda) = \pm 1$
- Bob が方向 $\mathbf{b}$ で測ると、結果は事前に決まった値 $B(\mathbf{b}, \lambda) = \pm 1$

ここで重要なのは**局所性**の仮定である。

- Alice の結果 $A(\mathbf{a}, \lambda)$ は、Bob の測定方向 $\mathbf{b}$ に依存しない
- Bob の結果 $B(\mathbf{b}, \lambda)$ は、Alice の測定方向 $\mathbf{a}$ に依存しない

つまり「Alice の選択が Bob の結果に影響しない」し、その逆もない。

各粒子ペアには異なる $\lambda$ が付随しうるので、相関は $\lambda$ の分布で平均して

```math
E(\mathbf{a}, \mathbf{b}) = \int A(\mathbf{a}, \lambda)\,B(\mathbf{b}, \lambda)\,\rho(\lambda)\,d\lambda
```

と書ける。ここで $\rho(\lambda)$ は $\lambda$ の確率分布（ $\int \rho\,d\lambda = 1$, $\rho \geq 0$ ）である。

問いはこうである。**この枠組みで、量子力学の予測 $E = -\cos\theta$ を再現できるか？**

---

## 第5段階：CHSH 不等式

### 4つの測定方向を選ぶ

ベルの不等式にはいくつかの形がある。ここでは最も使われる **CHSH (Clauser–Horne–Shimony–Holt)** の形を導く。

Alice は $\mathbf{a}$ と $\mathbf{a}'$ の2方向のどちらかを選び、Bob は $\mathbf{b}$ と $\mathbf{b}'$ の2方向のどちらかを選ぶ。各粒子ペアでは、Alice も Bob もどちらか一方しか測れない。

4つの相関から次の量を作る。

```math
S = E(\mathbf{a}, \mathbf{b}) - E(\mathbf{a}, \mathbf{b}') + E(\mathbf{a}', \mathbf{b}) + E(\mathbf{a}', \mathbf{b}')
```

### 隠れた変数なら $\vert S\vert \leq 2$

隠れた変数の仮説のもとでは、各粒子ペア（隠れた変数 $\lambda$ ）に対して4つの値

```math
A = A(\mathbf{a}, \lambda), \quad
A' = A(\mathbf{a}', \lambda), \quad
B = B(\mathbf{b}, \lambda), \quad
B' = B(\mathbf{b}', \lambda)
```

が**すべて同時に定まっている**。各値は $\pm 1$ である。

ここが決定的に重要なポイントである。量子力学では、Alice は $\mathbf{a}$ か $\mathbf{a}'$ のどちらか一方しか測れない。しかし隠れた変数の仮説では、測らなかった方の値も「存在する」と仮定している。

この仮定のもとで、各粒子ペアに対して次の量を考える。

```math
s(\lambda) = A B - A B' + A' B + A' B'
```

$AB'$ を括り出すと

```math
s(\lambda) = A(B - B') + A'(B + B')
```

ここで $B, B' = \pm 1$ なので、 $B - B'$ と $B + B'$ の組み合わせは次の2通りしかない。

$B = B'$ のとき： $B - B' = 0$, $B + B' = \pm 2$ なので

```math
s = A \cdot 0 + A' \cdot (\pm 2) = \pm 2
```

$B = -B'$ のとき： $B - B' = \pm 2$, $B + B' = 0$ なので

```math
s = A \cdot (\pm 2) + A' \cdot 0 = \pm 2
```

どちらの場合も $s(\lambda) = \pm 2$ であるから

```math
\vert s(\lambda)\vert = 2
```

が各粒子ペアで成り立つ。これを $\lambda$ について平均すると

```math
\vert S\vert = \left\vert \int s(\lambda)\,\rho(\lambda)\,d\lambda\right\vert 
\leq \int \vert s(\lambda)\vert \,\rho(\lambda)\,d\lambda
= 2\int \rho(\lambda)\,d\lambda
= 2
```

したがって

```math
\boxed{\vert S\vert \leq 2} \qquad \text{（CHSH 不等式）}
```

これは隠れた変数の仮説（局所性 + 実在性）だけから導かれる不等式であり、量子力学の法則を一切使っていない。

---

## 第6段階：量子力学は上限を超える

### 方向の選択

第3段階で $E(\mathbf{a}, \mathbf{b}) = -\cos\theta$ を導いた。この公式を使って $S$ を計算し、 $\vert S\vert > 2$ になる方向を探す。

4方向をすべて $xz$ 平面内に取り、 $z$ 軸からの角度で指定する。

```math
\mathbf{a}: 0^\circ, \qquad
\mathbf{b}: 45^\circ, \qquad
\mathbf{a}': 90^\circ, \qquad
\mathbf{b}': 135^\circ
```

つまり、4方向が 45 度ずつ等間隔に並んでいる。

### 各相関の計算

各ペアの間の角度と $E = -\cos\theta$ を計算する。

$E(\mathbf{a}, \mathbf{b})$ ： $\theta = 45^\circ$

```math
E(\mathbf{a}, \mathbf{b}) = -\cos 45^\circ = -\frac{1}{\sqrt{2}}
```

$E(\mathbf{a}, \mathbf{b}')$ ： $\theta = 135^\circ$

```math
E(\mathbf{a}, \mathbf{b}') = -\cos 135^\circ = -\left(-\frac{1}{\sqrt{2}}\right) = +\frac{1}{\sqrt{2}}
```

$E(\mathbf{a}', \mathbf{b})$ ： $\theta = 90^\circ - 45^\circ = 45^\circ$

```math
E(\mathbf{a}', \mathbf{b}) = -\cos 45^\circ = -\frac{1}{\sqrt{2}}
```

$E(\mathbf{a}', \mathbf{b}')$ ： $\theta = 135^\circ - 90^\circ = 45^\circ$

```math
E(\mathbf{a}', \mathbf{b}') = -\cos 45^\circ = -\frac{1}{\sqrt{2}}
```

### $S$ の計算

```math
S = E(\mathbf{a}, \mathbf{b}) - E(\mathbf{a}, \mathbf{b}') + E(\mathbf{a}', \mathbf{b}) + E(\mathbf{a}', \mathbf{b}')
```

```math
= \left(-\frac{1}{\sqrt{2}}\right) - \left(+\frac{1}{\sqrt{2}}\right) + \left(-\frac{1}{\sqrt{2}}\right) + \left(-\frac{1}{\sqrt{2}}\right)
```

```math
= -\frac{1}{\sqrt{2}} - \frac{1}{\sqrt{2}} - \frac{1}{\sqrt{2}} - \frac{1}{\sqrt{2}}
```

```math
= -\frac{4}{\sqrt{2}} = -2\sqrt{2}
```

したがって

```math
\boxed{\vert S\vert = 2\sqrt{2} \approx 2.83}
```

これは CHSH 不等式の上限 $2$ を明確に超えている。

### 何が起きたのか

CHSH 不等式は「各粒子がすべての方向に対する答えを事前に持っている」という仮定から導かれた。量子力学はこの上限を超える。

したがって、**少なくとも次の仮定の一方は誤りである**。

1. **実在性**：測定しなくても結果は事前に決まっている
2. **局所性**：Alice の選択は Bob の結果に影響しない

量子力学は、この二つを同時には認めない。これがベルの不等式の核心である。

### 実験

この予測は実験で繰り返し検証されている。光子の偏光や原子のスピンを使った実験で、量子力学の予測 $\vert S\vert = 2\sqrt{2}$ に一致する結果が得られており、CHSH 不等式 $\vert S\vert \leq 2$ は破れている。

---

## 補足： $2\sqrt{2}$ は量子力学の上限でもある

隠れた変数では $\vert S\vert \leq 2$ 。量子力学では $\vert S\vert = 2\sqrt{2}$ 。では、 $\vert S\vert $ はどこまで大きくなりうるか。

$A, B = \pm 1$ の4つの相関を自由に選べるなら、 $S$ の式の定義から最大値は $\vert S\vert = 4$ になりうる（4つの相関がすべて $\pm 1$ で揃えば）。

しかし量子力学ではこの $4$ に達することはなく、上限は $2\sqrt{2}$ である（Tsirelson の限界）。

```math
2 \quad \leq \quad 2\sqrt{2} \quad \leq \quad 4
```

```math
\text{古典上限} \qquad \text{量子上限} \qquad \text{数学的上限}
```

量子力学は古典を超えるが、数学的に可能な最大値にも達しない。この中間に位置することの物理的意味は、いまだに研究が続いている。

---

## 全体の論理構造（振り返り）

```
1粒子のスピン状態（2次元）  ← CLAUDE_PHYSICS.md
    ↓
2粒子は 2×2 = 4 次元（テンソル積）
    ↓
シングレット |Ψ⁻⟩ = (|+z⟩|−z⟩ − |−z⟩|+z⟩)/√2
    ↓
回転不変性：任意の基底で同じ形
    ↓
Alice が a で測ると Bob の粒子は |−a⟩ に決まる
    ↓
Bob が b で測る確率を Born 則で計算
    ↓
E(a,b) = −cos θ = −a·b    ← 量子力学の予測
    ↓
「実は最初から答えが決まっていた」仮説（隠れた変数）
    ↓
|A(B−B') + A'(B+B')| = 2  ← 各ペアで ±1 の代数
    ↓
平均して |S| ≤ 2   ← CHSH 不等式
    ↓
4方向を 45° 間隔に選ぶ → |S| = 2√2 > 2
    ↓
隠れた変数（局所性 + 実在性）は量子力学と両立しない
```
