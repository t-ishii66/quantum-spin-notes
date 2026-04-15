# 回転演算子 $U(\theta,\mathbf{n}) = \exp(-i\theta J_{\mathbf{n}}/\hbar)$ の導出

> **シリーズ構成**: [実験からパウリ行列へ](NOTE1.md) → 本文書（NOTE2.md）→ [ブロッホ球](NOTE3.md) → [θ/2 の由来](NOTE4.md) → [ベルの不等式](NOTE5.md)

## この文書の方針

[NOTE1.md](NOTE1.md) では、シュテルン・ゲルラッハ実験の二値測定からパウリ行列 $\sigma_x, \sigma_y, \sigma_z$ を導き、交換関係 $[\sigma_i, \sigma_j] = 2i\epsilon_{ijk}\sigma_k$ を確認した。

この文書では、より一般的な問いに答える。回転を量子力学の演算子で表すと、なぜ

```math
U(\theta,\mathbf{n})
=
\exp\!\left(
-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}
\right)
```

の形になるのかを、一つの流れで説明する。

出発点となる前提は次の三つである。

1. 量子状態はベクトルで表される
2. 物理量はエルミート演算子で表される
3. 確率は保存される（状態ベクトルの長さが変わらない）

途中で、回転の合成がユニタリ演算子の積に対応することや、同じ軸まわりの回転が連続的な群をなすことなど、対称変換を扱うための標準的な仮定も使う。それらは使う場面でその都度述べる。

---

## 全体の筋

流れは4段階ある。

1. **小さな回転は「ほぼ何もしない」** → $U = I + (\text{小さい何か})$ と書ける
2. **確率保存が形を絞る** → その「何か」は $-iG/\hbar$ の形でなければならない
3. **小さな回転の積み重ねが指数関数を生む** → $U = \exp(-i\theta G/\hbar)$
4. **$G$ が何かを決める** → 回転を正しく作る $G$ は角運動量である

この4段階の流れで、回転演算子の形が自然に決まっていく。

---

## 第1段階：小さな回転を式で書く

方向 $\mathbf{n}$ のまわりに、ごく小さな角度 $\delta\theta$ だけ回すことを考える。

この回転は「ほぼ何もしない」変換なので、対応する演算子は恒等演算子 $I$ に近い。したがって

```math
U(\delta\theta) = I + \delta\theta \cdot K + O(\delta\theta^2)
```

と書ける。ここで $K$ はまだ正体不明の演算子であり、 $O(\delta\theta^2)$ は小さな角度の二次以上で効く補正である。

この段階では $K$ に何の制約もない。次の段階で絞る。

---

## 第2段階：確率保存が形を決める

量子力学では、状態ベクトルの長さが確率の合計に対応する。回転した後の状態を $\vert\phi'\rangle = U\vert\phi\rangle$ と書くと、回転しても確率は変わらないという要請は

```math
\langle\phi'\vert\phi'\rangle = \langle\phi\vert\phi\rangle
```

である。左辺を展開すると

```math
\langle\phi'\vert\phi'\rangle = \langle\phi\vert U^\dagger U\vert\phi\rangle
```

これが任意の $\vert\phi\rangle$ に対して $\langle\phi\vert\phi\rangle$ と等しくなるためには

```math
U^\dagger U = I
```

でなければならない。この条件を満たす $U$ をユニタリ演算子と呼ぶ。

これを一次の式に代入する。

```math
(I + \delta\theta\, K^\dagger)(I + \delta\theta\, K) = I
```

一次まで展開すると

```math
I + \delta\theta(K + K^\dagger) + O(\delta\theta^2) = I
```

したがって

```math
K + K^\dagger = 0
```

つまり $K$ は**反エルミート**でなければならない（ $\dagger$ は転置して複素共役を取る操作で、 $K^\dagger = -K$ を満たす演算子を反エルミートと呼ぶ。逆に $G^\dagger = G$ を満たすものがエルミートである）。

反エルミート演算子は、エルミート演算子 $G$ を使って

```math
K = -\frac{i}{\hbar}\,G
```

と書ける。 $\hbar$ を入れるのは、 $G$ に角運動量と同じ次元を持たせるためである（角度 $\delta\theta$ は無次元なので、 $\delta\theta \cdot G/\hbar$ が全体で無次元になる）。

したがって微小回転は

```math
\boxed{
U(\delta\theta) = I - \frac{i}{\hbar}\,\delta\theta\,G + O(\delta\theta^2)
}
```

の形に限られる。ここで $G$ はエルミートな演算子である。この $G$ が何の物理量に対応するかは、第4段階で角運動量として同定される。

---

## 第3段階：積み重ねが指数関数を生む

### なぜ指数関数が出るのか

ここが核心の一つである。指数関数は天から降ってくるのではなく、**同じ操作を何度も繰り返す** と自然に現れる。

有限の角度 $\theta$ の回転を作りたい。これを $N$ 等分して

```math
\delta\theta = \frac{\theta}{N}
```

とする。角度 $\theta$ の回転は、角度 $\delta\theta$ の回転を $N$ 回重ねたものだから

```math
U(\theta) = \bigl[U(\delta\theta)\bigr]^N
```

である。前節の結果を代入すると

```math
U(\theta) = \left(I - \frac{i}{\hbar}\frac{\theta}{N}\,G\right)^N
```

ここで $N$ を大きくする。すると各回の回転はどんどん小さくなり、二次以上の項は消えていく。 $N \to \infty$ の極限では

```math
U(\theta)
=
\lim_{N\to\infty}
\left(I - \frac{i}{\hbar}\frac{\theta}{N}\,G\right)^N
```

### 数としての指数関数との比較

普通の数 $a$ に対して

```math
e^a = \lim_{N\to\infty}\left(1 + \frac{a}{N}\right)^N
```

が成り立つ。これは「 $1 + a/N$ を $N$ 回掛ける」という操作の極限が $e^a$ になるという、指数関数の定義そのものである。

演算子でもまったく同じ形が成り立つ。 $a$ を $-i\theta G/\hbar$ に置き換えれば

```math
\boxed{
U(\theta,\mathbf{n})
=
\exp\!\left(-\frac{i}{\hbar}\,\theta\,G_{\mathbf{n}}\right)
}
```

が得られる。

### ここまでのまとめ

ここまでで使った仮定は

1. 微小回転は $I$ に近い（一次まで展開できる）
2. 確率保存（ユニタリ性）

の二つだけである。この二つから、回転演算子が指数関数の形になることが出た。

残る問題はただ一つ：**$G$ は何か。**

---

## 第4段階： $G$ の正体を決める

### 回転演算子に求められること

回転演算子 $U$ は、物理量を正しく回さなければならない。

たとえば位置の演算子 $\hat{x}, \hat{y}, \hat{z}$ を考える。 $z$ 軸まわりに角度 $\delta\phi$ だけ回すなら、位置の演算子は

```math
\hat{x} \to \hat{x} - \hat{y}\,\delta\phi, \qquad
\hat{y} \to \hat{y} + \hat{x}\,\delta\phi, \qquad
\hat{z} \to \hat{z}
```

と変わるべきである。これは古典的な $z$ 軸まわりの回転行列

```math
R_z(\phi) =
\begin{pmatrix}
\cos\phi & -\sin\phi & 0 \\
\sin\phi & \cos\phi & 0 \\
0 & 0 & 1
\end{pmatrix}
```

を微小角 $\delta\phi$ で一次まで展開した

```math
R_z(\delta\phi) \approx
\begin{pmatrix}
1 & -\delta\phi & 0 \\
\delta\phi & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
```

そのものである。

### 量子力学で演算子を変換するしくみ

回転によって状態が変わるとする。回転前の状態を $\vert \psi\rangle$ 、回転後の状態を $\vert \psi'\rangle$ とすれば

```math
\vert \psi'\rangle = U\vert \psi\rangle
```

である。このとき、物理量 $\hat{A}$ の期待値は回転後に

```math
\langle\psi'\vert \hat{A}\vert \psi'\rangle
=
\langle\psi\vert U^\dagger \hat{A}\, U\vert \psi\rangle
```

となる。これは「状態を回す代わりに、演算子を $U^\dagger \hat{A}\, U$ に置き換えても同じ期待値が得られる」ということである。したがって、回転に伴う演算子の変換は

```math
\hat{A} \to U^\dagger \hat{A}\, U
```

と書ける。ここでは「回転後の状態での期待値を、回転前の状態で計算する」という方向の置き換えを使っている（教科書によっては $U \hat{A}\, U^\dagger$ と書く流儀もあるが、符号が逆になるだけで物理は同じである）。微小回転 $U = I - (i/\hbar)\delta\phi\,G_z$ を代入する。まず $U^\dagger$ は

```math
U^\dagger = I + \frac{i}{\hbar}\delta\phi\,G_z
```

である（ $G_z$ がエルミートなので $-i$ が $+i$ に変わる）。これを使うと

```math
\begin{aligned}
U^\dagger \hat{A}\, U
&=
\left(I + \frac{i}{\hbar}\delta\phi\,G_z\right)
\hat{A}
\left(I - \frac{i}{\hbar}\delta\phi\,G_z\right) \\
&=
\hat{A}
- \frac{i}{\hbar}\delta\phi\,\hat{A}G_z
+ \frac{i}{\hbar}\delta\phi\,G_z\hat{A}
+ O(\delta\phi^2) \\
&=
\hat{A}
+ \frac{i}{\hbar}\delta\phi\,(G_z\hat{A} - \hat{A}G_z)
+ O(\delta\phi^2) \\
&=
\hat{A} + \frac{i}{\hbar}\delta\phi\,[G_z, \hat{A}]
+ O(\delta\phi^2)
\end{aligned}
```

となる。したがって演算子の変化は

```math
\delta\hat{A} = \frac{i}{\hbar}\delta\phi\,[G_z, \hat{A}]
```

で与えられる。

### $G_z$ に課される条件

$z$ 軸まわりの回転を正しく再現するには

```math
\frac{i}{\hbar}[G_z, \hat{x}] = -\hat{y}, \qquad
\frac{i}{\hbar}[G_z, \hat{y}] = +\hat{x}, \qquad
\frac{i}{\hbar}[G_z, \hat{z}] = 0
```

が成り立たなければならない。書き直すと

```math
[G_z, \hat{x}] = i\hbar\,\hat{y}, \qquad
[G_z, \hat{y}] = -i\hbar\,\hat{x}, \qquad
[G_z, \hat{z}] = 0
```

である。

### 軌道角運動量がこの条件を満たす

ここで

```math
\hat{L}_z = \hat{x}\hat{p}_y - \hat{y}\hat{p}_x
```

を試す。必要なのは正準交換関係

```math
[\hat{x}, \hat{p}_x] = i\hbar, \qquad
[\hat{x}, \hat{p}_y] = 0, \qquad \text{etc.}
```

だけである。実際に計算すると

```math
[\hat{L}_z, \hat{x}]
= [\hat{x}\hat{p}_y - \hat{y}\hat{p}_x,\, \hat{x}]
= -\hat{y}[\hat{p}_x, \hat{x}]
= -\hat{y}(-i\hbar)
= i\hbar\,\hat{y}
```

同様に

```math
[\hat{L}_z, \hat{y}]
= [\hat{x}\hat{p}_y,\, \hat{y}]
= \hat{x}[\hat{p}_y, \hat{y}]
= \hat{x}(-i\hbar)
= -i\hbar\,\hat{x}
```

```math
[\hat{L}_z, \hat{z}] = 0
```

三つとも条件を満たす。したがって

```math
G_z = \hat{L}_z
```

である。同様の計算で $G_x = \hat{L}_x$, $G_y = \hat{L}_y$ も確かめられる。

### 一般の軸 $\mathbf{n}$ への拡張

ここまでで $x, y, z$ の各軸まわりの生成子が $\hat{L}_x, \hat{L}_y, \hat{L}_z$ であることが分かった。では斜めの軸 $\mathbf{n}$ ではどうか。

鍵は、微小回転が角度について一次で効くことである。一般の軸 $\mathbf{n} = (n_x, n_y, n_z)$ まわりの微小回転は、各座標軸まわりの微小回転の重ね合わせとして書ける。

古典的な $\mathbf{n}$ 軸まわりの微小回転は、外積を使って

```math
\delta\mathbf{r} = \delta\theta\,(\mathbf{n}\times\mathbf{r})
```

と書ける。これを成分で展開すると

```math
\begin{aligned}
\delta x &= \delta\theta\,(n_y z - n_z y) \\
\delta y &= \delta\theta\,(n_z x - n_x z) \\
\delta z &= \delta\theta\,(n_x y - n_y x)
\end{aligned}
```

である。ここで、各座標軸まわりの微小回転の結果を並べたい。これは上の外積の式で $\mathbf{n}$ を各座標軸の単位ベクトルに置けば得られる。

$x$ 軸まわり（ $\mathbf{n} = (1, 0, 0)$ ）：

```math
\delta x = \delta\theta\,(0 \cdot z - 0 \cdot y) = 0, \qquad
\delta y = \delta\theta\,(0 \cdot x - 1 \cdot z) = -z\,\delta\theta, \qquad
\delta z = \delta\theta\,(1 \cdot y - 0 \cdot x) = +y\,\delta\theta
```

$y$ 軸まわり（ $\mathbf{n} = (0, 1, 0)$ ）：

```math
\delta x = \delta\theta\,(1 \cdot z - 0 \cdot y) = +z\,\delta\theta, \qquad
\delta y = 0, \qquad
\delta z = \delta\theta\,(0 \cdot y - 1 \cdot x) = -x\,\delta\theta
```

$z$ 軸まわり（ $\mathbf{n} = (0, 0, 1)$ ）：

```math
\delta x = \delta\theta\,(0 \cdot z - 1 \cdot y) = -y\,\delta\theta, \qquad
\delta y = \delta\theta\,(1 \cdot x - 0 \cdot z) = +x\,\delta\theta, \qquad
\delta z = 0
```

$z$ 軸の結果は196行目で回転行列から導いたものと一致している。これらを表にまとめると見通しがよい。

|  | $\delta x$ | $\delta y$ | $\delta z$ |
|:---:|:---:|:---:|:---:|
| $L_x$ が生成 | $0$ | $-z\,\delta\theta$ | $+y\,\delta\theta$ |
| $L_y$ が生成 | $+z\,\delta\theta$ | $0$ | $-x\,\delta\theta$ |
| $L_z$ が生成 | $-y\,\delta\theta$ | $+x\,\delta\theta$ | $0$ |

一般軸の各成分を、表の各行と突き合わせてみる。

$\delta x$ について：

```math
\delta x = \delta\theta\,(n_y z - n_z y)
= n_y \underbrace{(+z\,\delta\theta)}_{L_y\text{ の行}} + n_z \underbrace{(-y\,\delta\theta)}_{L_z\text{ の行}}
```

$\delta y$ について：

```math
\delta y = \delta\theta\,(n_z x - n_x z)
= n_z \underbrace{(+x\,\delta\theta)}_{L_z\text{ の行}} + n_x \underbrace{(-z\,\delta\theta)}_{L_x\text{ の行}}
```

$\delta z$ について：

```math
\delta z = \delta\theta\,(n_x y - n_y x)
= n_x \underbrace{(+y\,\delta\theta)}_{L_x\text{ の行}} + n_y \underbrace{(-x\,\delta\theta)}_{L_y\text{ の行}}
```

三つとも、表の $L_x$ の行に $n_x$ を掛けたもの、 $L_y$ の行に $n_y$ を掛けたもの、 $L_z$ の行に $n_z$ を掛けたものの和になっている（表の該当セルが $0$ の項は消えている）。

つまり一般軸の微小回転は、表の各行をそのまま使って

```math
\begin{pmatrix} \delta x \\ \delta y \\ \delta z \end{pmatrix}
=
n_x
\underbrace{
\begin{pmatrix} 0 \\ -z \\ +y \end{pmatrix}
}_{L_x\text{ の行}}
\delta\theta
\;+\;
n_y
\underbrace{
\begin{pmatrix} +z \\ 0 \\ -x \end{pmatrix}
}_{L_y\text{ の行}}
\delta\theta
\;+\;
n_z
\underbrace{
\begin{pmatrix} -y \\ +x \\ 0 \end{pmatrix}
}_{L_z\text{ の行}}
\delta\theta
```

と分解できる。

ところで、量子力学では演算子の変化は

```math
\delta\hat{A} = \frac{i}{\hbar}\delta\theta\,[G_{\mathbf{n}},\, \hat{A}]
```

で与えられるのだった。ここで $\hat{A}$ は変化を調べたい演算子で、位置の各成分 $\hat{x}, \hat{y}, \hat{z}$ のいずれかを入れて使う。 $z$ 軸の場合は $G_z = \hat{L}_z$ で、 $\hat{A} = \hat{x}$ とすれば $[\hat{L}_z, \hat{x}]$ が $\delta\hat{x}$ を決め、 $\hat{A} = \hat{y}$ とすれば $[\hat{L}_z, \hat{y}]$ が $\delta\hat{y}$ を決めた。 $x$ 軸、 $y$ 軸まわりの回転についても同様だった。

いま上の分解は「一般軸の変化 = 各軸の変化の $n_x, n_y, n_z$ 重み付き和」と言っている。これを $\hat{A} = \hat{x}, \hat{y}, \hat{z}$ のそれぞれについて再現したい。交換子は第1引数について線形なので

```math
[n_x\hat{L}_x + n_y\hat{L}_y + n_z\hat{L}_z,\, \hat{A}]
=
n_x[\hat{L}_x, \hat{A}] + n_y[\hat{L}_y, \hat{A}] + n_z[\hat{L}_z, \hat{A}]
```

が成り立つ。右辺はまさに各軸の寄与を $n_x, n_y, n_z$ で重ね合わせたものである。したがって

```math
G_{\mathbf{n}} = n_x\hat{L}_x + n_y\hat{L}_y + n_z\hat{L}_z = \mathbf{n}\cdot\hat{\mathbf{L}}
```

とすれば、上の重ね合わせがそのまま再現される。

注意：この線形な重ね合わせが使えるのは微小回転（一次の範囲）だからである。有限の角度の回転は一般に非可換で（たとえば $x$ 軸まわりに 90 度回してから $z$ 軸まわりに 90 度回すのと、逆の順序では結果が違う）、単純に足し算で分解することはできない。

### 回転の生成子としての角運動量

ここまでの議論で、位置と運動量を持つ粒子の回転生成子は軌道角運動量 $\hat{\mathbf{L}}$ であることが分かった。回転の生成子を一般に $\mathbf{J}$ と書くと

```math
\boxed{
U(\theta,\mathbf{n})
=
\exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
}
```

これが導きたかった式である。

---

## スピン 1/2 への適用

純粋なスピン自由度だけを考える場合、スピン 1/2 では

```math
\mathbf{J} = \mathbf{S} = \frac{\hbar}{2}\boldsymbol{\sigma}
```

なので

```math
U(\theta,\mathbf{n})
=
\exp\!\left(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
```

となる。 $\hbar$ が消えて、半角 $\theta/2$ が現れる。なぜ $\theta/2$ が出るのか、その物理的意味は何か——これが次の文書 [NOTE4.md](NOTE4.md) の主題である。

---

## 全体の論理構造（振り返り）

```
小さな回転は I に近い
    ↓
確率保存 → U = I − (i/ℏ)δθ G （G はエルミート）
    ↓
小さな回転を N 回積む → U = exp(−iθG/ℏ)
    ↓
G は何か？ → 演算子を正しく回す条件を課す
    ↓
位置演算子の変換: δÂ = (i/ℏ)δθ [G, Â]
    ↓
z 軸回転の要件: [G_z, x̂] = iℏ ŷ,  [G_z, ŷ] = −iℏ x̂
    ↓
L_z = x̂p̂_y − ŷp̂_x がこれを満たす → G = 角運動量
    ↓
U(θ,n) = exp(−iθ n·J/ℏ)
```

量子力学の対称変換の枠組みを受け入れると、各ステップは直前のステップから自然に要請され、回転演算子の指数関数の形が導かれる。

---

**次の文書**: [NOTE3.md — ブロッホ球](NOTE3.md) では、スピン状態を球面上の点として視覚化する方法を導入する。
