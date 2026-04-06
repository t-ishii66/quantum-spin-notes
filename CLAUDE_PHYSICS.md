# 回転演算子 $U(\theta,\mathbf{n}) = \exp(-i\theta J_{\mathbf{n}}/\hbar)$ の導出

## この文書の方針

この文書は、前提知識をほぼ仮定せずに、

$$
U(\theta,\mathbf{n})
=
\exp\!\left(
-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}
\right)
$$

がなぜこの形になるかを、一つの流れで説明する。

必要な前提は次の三つだけである。

1. 量子状態はベクトルで表される
2. 物理量はエルミート演算子で表される
3. 確率は保存される（状態ベクトルの長さが変わらない）

---

## 全体の筋

流れは4段階ある。

1. **小さな回転は「ほぼ何もしない」** → $U = I + (\text{小さい何か})$ と書ける
2. **確率保存が形を絞る** → その「何か」は $-iG/\hbar$ の形でなければならない
3. **小さな回転の積み重ねが指数関数を生む** → $U = \exp(-i\theta G/\hbar)$
4. **$G$ が何かを決める** → 回転を正しく作る $G$ は角運動量である

この4段階がすべてであり、各段階に飛躍はない。

---

## 第1段階：小さな回転を式で書く

方向 $\mathbf{n}$ のまわりに、ごく小さな角度 $\delta\theta$ だけ回すことを考える。

この回転は「ほぼ何もしない」変換なので、対応する演算子は恒等演算子 $I$ に近い。したがって

$$
U(\delta\theta) = I + \delta\theta \cdot K + O(\delta\theta^2)
$$

と書ける。ここで $K$ はまだ正体不明の演算子であり、$O(\delta\theta^2)$ は小さな角度の二次以上で効く補正である。

この段階では $K$ に何の制約もない。次の段階で絞る。

---

## 第2段階：確率保存が形を決める

量子力学では、状態ベクトルの長さが確率の合計に対応する。回転しても確率は変わらないはずなので、$U$ はユニタリ演算子でなければならない。

$$
U^\dagger U = I
$$

これを一次の式に代入する。

$$
(I + \delta\theta\, K^\dagger)(I + \delta\theta\, K) = I
$$

一次まで展開すると

$$
I + \delta\theta(K + K^\dagger) + O(\delta\theta^2) = I
$$

したがって

$$
K + K^\dagger = 0
$$

つまり $K$ は**反エルミート**でなければならない。

反エルミート演算子は、エルミート演算子 $G$ を使って

$$
K = -\frac{i}{\hbar}\,G
$$

と書ける。$\hbar$ を入れるのは、$G$ に角運動量と同じ次元を持たせるためである（角度 $\delta\theta$ は無次元なので、$\delta\theta \cdot G/\hbar$ が全体で無次元になる）。

したがって微小回転は

$$
\boxed{
U(\delta\theta) = I - \frac{i}{\hbar}\,\delta\theta\,G + O(\delta\theta^2)
}
$$

の形に限られる。ここで $G$ はエルミート、すなわち物理量（オブザーバブル）である。

---

## 第3段階：積み重ねが指数関数を生む

### なぜ指数関数が出るのか

ここが核心の一つである。指数関数は天から降ってくるのではなく、**同じ操作を何度も繰り返す** と自然に現れる。

有限の角度 $\theta$ の回転を作りたい。これを $N$ 等分して

$$
\delta\theta = \frac{\theta}{N}
$$

とする。角度 $\theta$ の回転は、角度 $\delta\theta$ の回転を $N$ 回重ねたものだから

$$
U(\theta) = \bigl[U(\delta\theta)\bigr]^N
$$

である。前節の結果を代入すると

$$
U(\theta) = \left(I - \frac{i}{\hbar}\frac{\theta}{N}\,G\right)^N
$$

ここで $N$ を大きくする。すると各回の回転はどんどん小さくなり、二次以上の項は消えていく。$N \to \infty$ の極限では

$$
U(\theta)
=
\lim_{N\to\infty}
\left(I - \frac{i}{\hbar}\frac{\theta}{N}\,G\right)^N
$$

### 数としての指数関数との比較

普通の数 $a$ に対して

$$
e^a = \lim_{N\to\infty}\left(1 + \frac{a}{N}\right)^N
$$

が成り立つ。これは「$1 + a/N$ を $N$ 回掛ける」という操作の極限が $e^a$ になるという、指数関数の定義そのものである。

演算子でもまったく同じ形が成り立つ。$a$ を $-i\theta G/\hbar$ に置き換えれば

$$
\boxed{
U(\theta,\mathbf{n})
=
\exp\!\left(-\frac{i}{\hbar}\,\theta\,G_{\mathbf{n}}\right)
}
$$

が得られる。

### ここまでのまとめ

ここまでで使った仮定は

1. 微小回転は $I$ に近い（一次まで展開できる）
2. 確率保存（ユニタリ性）

の二つだけである。この二つから、回転演算子が指数関数の形になることが出た。

残る問題はただ一つ：**$G$ は何か。**

---

## 第4段階：$G$ の正体を決める

### 回転演算子に求められること

回転演算子 $U$ は、物理量を正しく回さなければならない。

たとえば位置の演算子 $\hat{x}, \hat{y}, \hat{z}$ を考える。$z$ 軸まわりに角度 $\delta\phi$ だけ回すなら、位置の演算子は

$$
\hat{x} \to \hat{x} - \hat{y}\,\delta\phi, \qquad
\hat{y} \to \hat{y} + \hat{x}\,\delta\phi, \qquad
\hat{z} \to \hat{z}
$$

と変わるべきである。これは古典的な $z$ 軸まわりの回転行列

$$
R_z(\phi) =
\begin{pmatrix}
\cos\phi & -\sin\phi & 0 \\
\sin\phi & \cos\phi & 0 \\
0 & 0 & 1
\end{pmatrix}
$$

を微小角 $\delta\phi$ で一次まで展開した

$$
R_z(\delta\phi) \approx
\begin{pmatrix}
1 & -\delta\phi & 0 \\
\delta\phi & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
$$

そのものである。

### 量子力学で演算子を変換するしくみ

回転によって状態が変わるとする。回転前の状態を $|\psi\rangle$、回転後の状態を $|\psi'\rangle$ とすれば

$$
|\psi'\rangle = U|\psi\rangle
$$

である。このとき、物理量 $\hat{A}$ の期待値は回転後に

$$
\langle\psi'|\hat{A}|\psi'\rangle
=
\langle\psi|U^\dagger \hat{A}\, U|\psi\rangle
$$

となる。これは「状態を回す代わりに、演算子を $U^\dagger \hat{A}\, U$ に置き換えても同じ期待値が得られる」ということである。したがって、回転に伴う演算子の変換は

$$
\hat{A} \to U^\dagger \hat{A}\, U
$$

と書ける。微小回転 $U = I - (i/\hbar)\delta\phi\,G_z$ を代入する。まず $U^\dagger$ は

$$
U^\dagger = I + \frac{i}{\hbar}\delta\phi\,G_z
$$

である（$G_z$ がエルミートなので $-i$ が $+i$ に変わる）。これを使うと

$$
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
$$

となる。したがって演算子の変化は

$$
\delta\hat{A} = \frac{i}{\hbar}\delta\phi\,[G_z, \hat{A}]
$$

で与えられる。

### $G_z$ に課される条件

$z$ 軸まわりの回転を正しく再現するには

$$
\frac{i}{\hbar}[G_z, \hat{x}] = -\hat{y}, \qquad
\frac{i}{\hbar}[G_z, \hat{y}] = +\hat{x}, \qquad
\frac{i}{\hbar}[G_z, \hat{z}] = 0
$$

が成り立たなければならない。書き直すと

$$
[G_z, \hat{x}] = i\hbar\,\hat{y}, \qquad
[G_z, \hat{y}] = -i\hbar\,\hat{x}, \qquad
[G_z, \hat{z}] = 0
$$

である。

### 軌道角運動量がこの条件を満たす

ここで

$$
\hat{L}_z = \hat{x}\hat{p}_y - \hat{y}\hat{p}_x
$$

を試す。必要なのは正準交換関係

$$
[\hat{x}, \hat{p}_x] = i\hbar, \qquad
[\hat{x}, \hat{p}_y] = 0, \qquad \text{etc.}
$$

だけである。実際に計算すると

$$
[\hat{L}_z, \hat{x}]
= [\hat{x}\hat{p}_y - \hat{y}\hat{p}_x,\, \hat{x}]
= -\hat{y}[\hat{p}_x, \hat{x}]
= -\hat{y}(-i\hbar)
= i\hbar\,\hat{y}
$$

同様に

$$
[\hat{L}_z, \hat{y}]
= [\hat{x}\hat{p}_y,\, \hat{y}]
= \hat{x}[\hat{p}_y, \hat{y}]
= \hat{x}(-i\hbar)
= -i\hbar\,\hat{x}
$$

$$
[\hat{L}_z, \hat{z}] = 0
$$

三つとも条件を満たす。したがって

$$
G_z = \hat{L}_z
$$

である。同様の計算で $G_x = \hat{L}_x$, $G_y = \hat{L}_y$ も確かめられる。

### 一般の軸 $\mathbf{n}$ への拡張

ここまでで $x, y, z$ の各軸まわりの生成子が $\hat{L}_x, \hat{L}_y, \hat{L}_z$ であることが分かった。では斜めの軸 $\mathbf{n}$ ではどうか。

鍵は、微小回転が角度について一次で効くことである。一般の軸 $\mathbf{n} = (n_x, n_y, n_z)$ まわりの微小回転は、各座標軸まわりの微小回転の重ね合わせとして書ける。

古典的な $\mathbf{n}$ 軸まわりの微小回転は、外積を使って

$$
\delta\mathbf{r} = \delta\theta\,(\mathbf{n}\times\mathbf{r})
$$

と書ける。これを成分で展開すると

$$
\begin{aligned}
\delta x &= \delta\theta\,(n_y z - n_z y) \\
\delta y &= \delta\theta\,(n_z x - n_x z) \\
\delta z &= \delta\theta\,(n_x y - n_y x)
\end{aligned}
$$

である。ここで、すでに示した各軸まわりの結果を並べてみる。

$$
\begin{array}{c|ccc}
 & \delta x & \delta y & \delta z \\
\hline
L_x\text{ が生成} & 0 & -z\,\delta\theta & +y\,\delta\theta \\
L_y\text{ が生成} & +z\,\delta\theta & 0 & -x\,\delta\theta \\
L_z\text{ が生成} & -y\,\delta\theta & +x\,\delta\theta & 0
\end{array}
$$

一般軸の各成分を、表の各行と突き合わせてみる。

$\delta x$ について：

$$
\delta x = \delta\theta\,(n_y z - n_z y)
= n_y \underbrace{(+z\,\delta\theta)}_{L_y\text{ の行}} + n_z \underbrace{(-y\,\delta\theta)}_{L_z\text{ の行}}
$$

$\delta y$ について：

$$
\delta y = \delta\theta\,(n_z x - n_x z)
= n_z \underbrace{(+x\,\delta\theta)}_{L_z\text{ の行}} + n_x \underbrace{(-z\,\delta\theta)}_{L_x\text{ の行}}
$$

$\delta z$ について：

$$
\delta z = \delta\theta\,(n_x y - n_y x)
= n_x \underbrace{(+y\,\delta\theta)}_{L_x\text{ の行}} + n_y \underbrace{(-x\,\delta\theta)}_{L_y\text{ の行}}
$$

三つとも、表の $L_x$ の行に $n_x$ を掛けたもの、$L_y$ の行に $n_y$ を掛けたもの、$L_z$ の行に $n_z$ を掛けたものの和になっている（表の該当セルが $0$ の項は消えている）。

つまり一般軸の微小回転は、表の各行をそのまま使って

$$
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
$$

と分解できる。

ところで、量子力学では演算子の変化は

$$
\delta\hat{A} = \frac{i}{\hbar}\delta\theta\,[G_{\mathbf{n}},\, \hat{A}]
$$

で与えられるのだった。$z$ 軸の場合は $G_z = \hat{L}_z$ で、$[G_z, \hat{x}]$ が $\delta\hat{x}$ を決めた。$x$ 軸、$y$ 軸も同様だった。

いま上の分解は「一般軸の変化 = 各軸の変化の $n_x, n_y, n_z$ 重み付き和」と言っている。交換子は第1引数について線形なので

$$
[n_x\hat{L}_x + n_y\hat{L}_y + n_z\hat{L}_z,\, \hat{A}]
=
n_x[\hat{L}_x, \hat{A}] + n_y[\hat{L}_y, \hat{A}] + n_z[\hat{L}_z, \hat{A}]
$$

が成り立つ。右辺はまさに各軸の寄与を $n_x, n_y, n_z$ で重ね合わせたものである。したがって

$$
G_{\mathbf{n}} = n_x\hat{L}_x + n_y\hat{L}_y + n_z\hat{L}_z = \mathbf{n}\cdot\hat{\mathbf{L}}
$$

とすれば、上の重ね合わせがそのまま再現される。

### スピンがある場合

ここまでは位置と運動量だけを持つ粒子（軌道角運動量のみ）の話だった。

しかしスピンのように、位置を持たないが回転に対して変換する内部自由度もある。そのような場合も含めて、回転の生成子を**全角運動量** $\mathbf{J}$ と書く。

$$
\mathbf{J} = \hat{\mathbf{L}} + \hat{\mathbf{S}}
$$

したがって一般に

$$
\boxed{
U(\theta,\mathbf{n})
=
\exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
}
$$

これが導きたかった式である。

---

## スピン 1/2 への適用

スピン 1/2 では

$$
\mathbf{J} = \mathbf{S} = \frac{\hbar}{2}\boldsymbol{\sigma}
$$

なので

$$
U(\theta,\mathbf{n})
=
\exp\!\left(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
$$

となる。$\hbar$ が消えて、半角 $\theta/2$ が現れる。これが PHYSICS5.md や PHYSICS6.md で現れたスピン回転の式である。

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
L_z = x̂p̂_y − ŷp̂_x がこれを満たす
    ↓
G = J = L + S （スピンを含む全角運動量）
    ↓
U(θ,n) = exp(−iθ n·J/ℏ)
```

どの段階にも「天下り」はない。各ステップは、直前のステップから自然に要請される。
