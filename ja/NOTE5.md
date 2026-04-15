# ベルの不等式：量子力学が古典的直観を越える場所

> **シリーズ構成**: [実験からパウリ行列へ](NOTE1.md) → [回転演算子](NOTE2.md) → [ブロッホ球](NOTE3.md) → [θ/2 の由来](NOTE4.md) → 本文書（NOTE5.md）

## この文書の方針

この文書は、NOTE シリーズの知識だけを使って、ベルの不等式を導く。

使う道具は

- 状態ベクトルと測定（[NOTE1.md](NOTE1.md)）
- パウリ行列 $\sigma_x, \sigma_y, \sigma_z$ と方向 $\mathbf{n}$ の測定 $\mathbf{n}\cdot\boldsymbol{\sigma}$ （[NOTE1.md](NOTE1.md)）
- スピン回転と固有状態の変換（[NOTE4.md](NOTE4.md)）

である。新しい数学道具としては2粒子系のテンソル積を導入し、概念としては局所隠れ変数と CHSH の考え方を追加する。それ以外は既知の道具の組み合わせで話が進む。

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

[NOTE1.md](NOTE1.md) で見たように、1粒子のスピン状態は 2 次元空間に住んでいる。 $z$ 基底は

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

これを確かめるには、任意の方向 $\mathbf{a}$ の固有状態で $\vert \Psi^-\rangle$ を書き直してみればよい。ここでは計算を簡単にするため、方向を $xz$ 平面内に取る。シングレットは任意の空間回転に対して不変なので、一般の方向でも同じ結論になる。

$\mathbf{a}$ が $z$ 軸から角度 $\theta_a$ の方向にあるとする（ $\theta_a$ は $z$ 軸からの極角）。

方向 $\mathbf{a}$ の固有状態 $\vert {+a}\rangle$ は、 $\vert {+z}\rangle$ を $y$ 軸まわりに $\theta_a$ だけ回転させたものである。$z$ 軸から $\theta_a$ だけ傾いた方向に到達するには、$y$ 軸まわりにちょうど $\theta_a$ だけ回せばよいので、ここでは極角と回転角が同じ値になる。[NOTE4.md](NOTE4.md) の回転行列

```math
U(\theta, \mathbf{n}) = \cos\frac{\theta}{2}\,I - i\sin\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
```

で $\mathbf{n} = \hat{y}$, 回転角 $\theta = \theta_a$ とすると

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

である。空間的には $\theta_a$ だけ回転しているが、状態ベクトルの係数には $\theta_a/2$ が現れる。これは [NOTE4.md](NOTE4.md) で見たスピノルの半角構造そのものである。 $c = \cos(\theta_a/2)$, $s = \sin(\theta_a/2)$ と略記すると

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

$\mathbf{a}$ と $\mathbf{b}$ が同じ $xz$ 平面内にあるとし、 $z$ 軸からの角度をそれぞれ $\theta_a$, $\theta_b$ とする（ $\theta = \theta_b - \theta_a$ ）。[NOTE4.md](NOTE4.md) の回転から

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

同時確率 $P(A, B)$ は、Alice の測定確率 $P(A)$ と、Alice の結果を条件とした Bob の条件付き確率 $P(B \mid A)$ の積 $P(A, B) = P(A) \cdot P(B \mid A)$ で求まる。シングレット状態は回転不変なので、Alice がどの方向で測っても $+1$ と $-1$ は等確率 $P(A = +1) = P(A = -1) = 1/2$ である（どちらの向きも特別ではない）。したがって

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

これがベル不等式の議論全体の到達点となる核心的な結果である。

なぜこの結果が重要なのか。古典的な（隠れた変数を持つ）理論でも、相関 $E(\theta)$ の形自体は工夫次第でさまざまに作れる。しかし、4つの測定方向を適切に選んで相関を組み合わせると、古典理論では絶対に超えられない上限が存在する（CHSH 不等式）。量子力学の $E = -\cos\theta$ は、Born 則の $\cos^2(\theta/2)$, $\sin^2(\theta/2)$ という確率——状態ベクトルの内積から来る——が生み出す曲線であり、この上限を超えてしまう。次の段階でこれを定量的に見ていく。

### 確認

- $\theta = 0$ （同方向）： $E = -1$ （完全反相関） ✓
- $\theta = \pi$ （逆方向）： $E = +1$ （完全正相関） ✓
- $\theta = \pi/2$ （直交）： $E = 0$ （無相関） ✓

---

## 第4段階：古典的な説明の試み

### アインシュタインの問い

ここで立ち止まって考える。

Alice が方向 $\mathbf{a}$ で測定すると、Bob の粒子は即座に $\vert {-a}\rangle$ （または $\vert {+a}\rangle$ ）に決まる。Alice と Bob がどれほど離れていても、である。

しかし Bob 単独で見える測定統計は Alice が何をしようと変わらず、この相関を使って光より速く信号を送ることはできない（量子力学はこの意味で特殊相対論と矛盾しない）。

ならば、Bob の粒子は**最初から答えを持っていた**と考えるほうが自然ではないか。

これがアインシュタイン・ポドルスキー・ローゼン（EPR）の議論である。

### 隠れた変数の仮説

EPR の議論を数学的にまとめると、次のような仮説になる。

> 2つの粒子が作られた瞬間に、各粒子には測定結果が事前に決まっている——少なくとも、実験で選ばれうる方向については、測らなかった場合の値も同時に存在する。この事前の値を決めるのが隠れた変数 $\lambda$ である。

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

と書ける。ここで $\rho(\lambda)$ は $\lambda$ の確率分布（ $\int \rho\,d\lambda = 1$, $\rho \geq 0$ ）である。もう一つ暗黙の仮定がある。 $\rho(\lambda)$ は Alice と Bob がどの方向を選ぶかに依存しない——つまり測定方向の選択と隠れた変数は統計的に独立である。

問いはこうである。**この枠組みで、量子力学の予測 $E = -\cos\theta$ を再現できるか？**

### 1つの方向のペアなら問題ない

まず、隠れた変数でうまくいく場合を確認しよう。

Alice と Bob が同じ方向 $\mathbf{a}$ で測定する場合を考える。量子力学の予測は完全反相関（ $E = -1$ ）で、結果は次の2パターンしかない。

| Alice | Bob |
|:---:|:---:|
| $+1$ | $-1$ |
| $-1$ | $+1$ |

これは「粒子が作られた瞬間に、Alice の結果と Bob の結果が逆になるよう決まっていた」で完璧に説明できる。もつれを持ち出す必要すらない。

次に、Bob が角度をつけて方向 $\mathbf{b}$（ $\mathbf{a}$ から $\theta$ だけ傾いた方向）で測定する場合。Alice が $+1$ のとき、Bob は $+1$ を確率 $\sin^2(\theta/2)$ で、 $-1$ を確率 $\cos^2(\theta/2)$ で得る。一見、もつれの効果が見えそうだが——

この確率分布も隠れた変数で再現できる。たとえば「粒子ペアが作られる時点で、Alice が $\mathbf{a}$ で測ったら $+1$、Bob が $\mathbf{b}$ で測ったら確率 $\sin^2(\theta/2)$ で $+1$、確率 $\cos^2(\theta/2)$ で $-1$ になるような隠し指示書 $\lambda$ が封入されている」と考えればよい。 $\lambda$ の分布を適切に選べば、相関 $E(\mathbf{a}, \mathbf{b}) = -\cos\theta$ を正確に再現できる。

**つまり、1組の測定方向だけでは、「最初から決まっていた」と「もつれの結果その場で決まる」を実験的に区別できない。**

### では何が問題になるのか

困難は、**複数の方向について同時に整合的な指示書を作ろうとしたとき**に起こる。

具体的に考えよう。Alice は $\mathbf{a}$ か $\mathbf{a}'$ のどちらかを選び、Bob は $\mathbf{b}$ か $\mathbf{b}'$ のどちらかを選ぶ。隠れた変数の仮説では、粒子ペアが作られた瞬間に4つの値がすべて決まっている。

```math
A(\mathbf{a}, \lambda) = \pm 1, \quad
A(\mathbf{a}', \lambda) = \pm 1, \quad
B(\mathbf{b}, \lambda) = \pm 1, \quad
B(\mathbf{b}', \lambda) = \pm 1
```

ここが核心である。**実際の実験では、各ペアについて Alice は $\mathbf{a}$ か $\mathbf{a}'$ のどちらか一方しか測れない。Bob も同様である。** しかし隠れた変数の仮説は「測らなかった方の値も存在する」と主張する。

### 隠れた変数が制約を受ける理由

隠れた変数の仮説で決定的なのは、**Bob の値 $B(\mathbf{b}, \lambda)$ が、Alice の測定の選択に依存しない**ということである。

Alice が $\mathbf{a}$ を測ろうが $\mathbf{a}'$ を測ろうが、Bob の粒子が方向 $\mathbf{b}$ に対して返す値は同じ $B(\mathbf{b}, \lambda)$ である。なぜなら、粒子が作られた瞬間に値は決まっており、遠く離れた Alice の行動は Bob の結果に影響しないからである（局所性）。

これは当たり前のように聞こえるが、重大な帰結をもたらす。相関 $E(\mathbf{a}, \mathbf{b})$ と相関 $E(\mathbf{a}', \mathbf{b})$ の計算に登場する $B$ は**同一の値**である。4つの値 $A, A', B, B'$ はすべて $\pm 1$ しか取れず、しかもそれらが4組の相関すべてで共有される。この制約から $\vert S\vert \leq 2$ という上限が生まれる。

### 量子力学ではなぜこの制約がないのか

量子力学では状況がまったく異なる。

シングレット状態から Alice が方向 $\mathbf{a}$ で測定して $+1$ を得ると、Bob の粒子は $\vert {-a}\rangle$ になる。一方、Alice が方向 $\mathbf{a}'$ で測定して $+1$ を得ると、Bob の粒子は $\vert {-a'}\rangle$ になる。

Bob が同じ方向 $\mathbf{b}$ を測っても、元の状態が $\vert {-a}\rangle$ か $\vert {-a'}\rangle$ かで**結果の確率分布が変わる**。

- $\vert {-a}\rangle$ を $\mathbf{b}$ で測る → $P(+1) = \sin^2(\theta_{ab}/2)$
- $\vert {-a'}\rangle$ を $\mathbf{b}$ で測る → $P(+1) = \sin^2(\theta_{a'b}/2)$

つまり、Alice の測定結果で条件づけると、Bob に割り当てる条件付き状態が $\vert {-a}\rangle$ または $\vert {-a'}\rangle$ に変わる。ただし重要な注意がある。Bob 単独の統計を見れば、Alice が何を選んでも $+1$ と $-1$ は常に半々である——この意味で、Alice の選択が Bob に「信号」を送ることはない。違いが現れるのは、Alice と Bob の結果を照合して**相関**を調べたときだけである。

隠れた変数では、4つの相関が「同じ $B$ の値を共有する」という代数的制約に縛られている。量子力学では、相関 $E(\mathbf{a}, \mathbf{b})$ を生む Bob の条件付き状態と、相関 $E(\mathbf{a}', \mathbf{b})$ を生む Bob の条件付き状態が異なるので、**4つの相関は、同時に定まった $A, A', B, B'$ の代数的制約には従わない**。この違いが $\vert S\vert > 2$ を可能にする。

次の段階で、この差がどれだけの違いを生むかを定量的に示す。

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

$A$ を含む項と $A'$ を含む項に分けて整理すると

```math
s(\lambda) = \underbrace{AB - AB'}_{A\text{ を含む項}} + \underbrace{A'B + A'B'}_{A'\text{ を含む項}}
= A(B - B') + A'(B + B')
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

これは隠れた変数の仮説——事前に値が決まっていること（実在性）、遠方の設定に依存しないこと（局所性）、測定方向の選択が $\lambda$ と独立であること——だけから導かれる不等式であり、量子力学の法則を一切使っていない。

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

CHSH 不等式は、測定結果が事前に決まっていて（実在性）、遠方の設定に依存せず（局所性）、測定方向の選択が自由である、という仮定から導かれた。量子力学はこの上限を超える。

したがって、**測定結果が事前に同時に決まっており、しかも遠方の測定設定に影響されない、という素朴な局所実在論は成り立たない**。よく短く言えば、局所性と実在性を同時には保てない。これがベルの不等式の核心である。

### 実験

この予測は実験で繰り返し検証されている。光子の偏光や原子・電子のスピンなど、対応する量子二値測定を使った実験で、CHSH 不等式の古典上限 $\vert S\vert \leq 2$ を明確に超える相関が観測されている。

---

## 補足： $2\sqrt{2}$ は量子力学の上限でもある

隠れた変数では $\vert S\vert \leq 2$ 。量子力学では $\vert S\vert = 2\sqrt{2}$ 。では、 $\vert S\vert $ はどこまで大きくなりうるか。

$A, B = \pm 1$ の4つの相関を自由に選べるなら、 $S$ の式の定義から最大値は $\vert S\vert = 4$ になりうる（4つの相関がすべて $\pm 1$ で揃えば）。

しかし量子力学ではこの $4$ に達することはなく、上限は $2\sqrt{2}$ である（Tsirelson の限界）。

```math
2 \quad \leq \quad 2\sqrt{2} \quad \leq \quad 4
```

```math
\text{古典上限} \qquad \text{量子上限} \qquad \text{代数的上限}
```

量子力学は古典を超えるが、代数的に可能な最大値にも達しない。この中間に位置することの物理的意味は、いまだに研究が続いている。

---

## 全体の論理構造（振り返り）

```
1粒子のスピン状態（2次元）  ← NOTE1.md
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
素朴な局所実在論は量子力学と両立しない
```


<img src="../images/end.png" width="400">
