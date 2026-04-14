# スピン 1/2 の回転演算子になぜ $\theta/2$ が現れるのか

> **シリーズ構成**: [実験からパウリ行列へ](PHYSICS_NOTE.md) → [回転演算子](PHYSICS_NOTE2.md) → [ブロッホ球](PHYSICS_NOTE3.md) → 本文書（PHYSICS_NOTE4.md）→ [ベルの不等式](PHYSICS_NOTE5.md)

## この文書の方針

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で、パウリ行列 $\sigma_x, \sigma_y, \sigma_z$ を実験事実から導き、スピン演算子が $S_i = \hbar\sigma_i/2$ であること、交換関係 $[\sigma_i, \sigma_j] = 2i\epsilon_{ijk}\sigma_k$ を確認した。

[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で、回転演算子が

```math
U(\theta,\mathbf{n}) = \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

であることを導いた。

この文書では、この二つを接続する。具体的には

1. なぜパウリ行列が角運動量と同格なのか（交換関係の意味）
2. $\mathbf{J} = \mathbf{S} = \frac{\hbar}{2}\boldsymbol{\sigma}$ を代入すると $\theta/2$ が現れること
3. その結果として回転行列が具体的にどうなるか
4. $\theta/2$ の物理的な意味（360度で元に戻らない）

を、一つの流れで説明する。

---

## 第1段階：なぜパウリ行列が角運動量なのか

### 古典的な角運動量の二つの顔

古典力学では、角運動量は

```math
\mathbf{L} = \mathbf{r} \times \mathbf{p}
```

で定義される。これは「位置と運動量から作られる量」という**構成的な定義**である。

しかし [PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で見たように、 $\mathbf{L}$ にはもう一つの顔がある。それは**回転の生成子**としての役割である。 $z$ 軸まわりの微小回転 $\delta\phi$ に対して

```math
\delta\hat{x} = \frac{i}{\hbar}\delta\phi\,[G_z,\,\hat{x}]
```

という条件を満たす $G_z$ を探したら、 $G_z = \hat{L}_z$ だった。つまり角運動量は、「回転を作る量」でもある。

古典力学では、この二つの顔は同じものを指していた。しかし量子力学では、**回転の生成子であること** のほうがより根本的な定義になる。

### 量子力学における角運動量の定義

量子力学では、角運動量を次のように定義する。

> 3つのエルミート演算子 $J_x, J_y, J_z$ が
>
> $$[J_i, J_j] = i\hbar\,\epsilon_{ijk}\,J_k$$
>
> を満たすとき、 $\mathbf{J} = (J_x, J_y, J_z)$ を**角運動量**と呼ぶ。

なぜこれが定義になるのか。理由は、回転の生成子であるためにはこの交換関係を満たすことが**必要かつ十分**だからである。以下、必要性と十分性をそれぞれ具体的に見る。

### なぜ交換関係が必要なのか

空間の回転は、順序を変えると結果が変わる。これを具体的に見てみよう。

目の前にある本を手に取って、次の2通りを試してほしい。

- **順序 A:** まず $x$ 軸（左右方向）まわりに 90 度回し、次に $z$ 軸（鉛直方向）まわりに 90 度回す
- **順序 B:** 先に $z$ 軸まわりに 90 度、次に $x$ 軸まわりに 90 度

結果は異なる。回転は順序に依存する（非可換である）。

この「入れ替えたときのずれ」を、量子力学の演算子で捉えたい。微小回転を考える。 $x$ 軸まわりに $\delta\alpha$ 、 $y$ 軸まわりに $\delta\beta$ の微小回転を順に行うとする。[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) の形を使うと

```math
U(\delta\alpha, \hat{x}) = I - \frac{i}{\hbar}\delta\alpha\,G_x + O(\delta\alpha^2)
```

```math
U(\delta\beta, \hat{y}) = I - \frac{i}{\hbar}\delta\beta\,G_y + O(\delta\beta^2)
```

順序 A（ $x$ が先、 $y$ が後）の積を二次まで展開する。

```math
U(\delta\beta, \hat{y})\,U(\delta\alpha, \hat{x})
= I
- \frac{i}{\hbar}\delta\alpha\,G_x
- \frac{i}{\hbar}\delta\beta\,G_y
- \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,G_y G_x
+ \cdots
```

順序 B（ $y$ が先、 $x$ が後）は

```math
U(\delta\alpha, \hat{x})\,U(\delta\beta, \hat{y})
= I
- \frac{i}{\hbar}\delta\alpha\,G_x
- \frac{i}{\hbar}\delta\beta\,G_y
- \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,G_x G_y
+ \cdots
```

一次の項は同じである。差が出るのは二次の項で

```math
\text{順序 A} - \text{順序 B}
= -\frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,(G_y G_x - G_x G_y)
= \frac{1}{\hbar^2}\delta\alpha\,\delta\beta\,[G_x, G_y]
```

つまり、**2つの回転を入れ替えたときのずれは、生成子の交換子 $[G_x, G_y]$ で決まる。**

一方、古典幾何学では、 $x$ と $y$ の微小回転を入れ替えたときのずれは、 $z$ 軸まわりの微小回転になる。これを回転行列で直接確かめる。

$x$ 軸まわりの微小回転行列は（[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) の $z$ 軸版と同様に、 $\cos\delta\alpha \approx 1$, $\sin\delta\alpha \approx \delta\alpha$ を使う）

```math
R_x(\delta\alpha) \approx
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & -\delta\alpha \\
0 & \delta\alpha & 1
\end{pmatrix}
```

$y$ 軸まわりは

```math
R_y(\delta\beta) \approx
\begin{pmatrix}
1 & 0 & \delta\beta \\
0 & 1 & 0 \\
-\delta\beta & 0 & 1
\end{pmatrix}
```

順序 A（ $x$ が先、 $y$ が後）：

```math
R_y R_x \approx
\begin{pmatrix}
1 & \delta\alpha\,\delta\beta & \delta\beta \\
0 & 1 & -\delta\alpha \\
-\delta\beta & \delta\alpha & 1
\end{pmatrix}
```

順序 B（ $y$ が先、 $x$ が後）：

```math
R_x R_y \approx
\begin{pmatrix}
1 & 0 & \delta\beta \\
\delta\alpha\,\delta\beta & 1 & -\delta\alpha \\
-\delta\beta & \delta\alpha & 1
\end{pmatrix}
```

差を取ると（一次の項は同じなので、二次の項だけが残る）

```math
R_y R_x - R_x R_y \approx
\begin{pmatrix}
0 & \delta\alpha\,\delta\beta & 0 \\
-\delta\alpha\,\delta\beta & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
```

一方、 $z$ 軸まわりの微小回転行列は

```math
R_z(\delta\gamma) \approx
\begin{pmatrix}
1 & -\delta\gamma & 0 \\
\delta\gamma & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
```

であり、 $R_z - I$ は

```math
R_z(\delta\gamma) - I \approx
\begin{pmatrix}
0 & -\delta\gamma & 0 \\
\delta\gamma & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
```

見比べると、 $\delta\gamma = -\delta\alpha\,\delta\beta$ とすればぴったり一致する。つまり

```math
R_y R_x - R_x R_y \approx R_z(-\delta\alpha\,\delta\beta) - I
```

である。 $x$ と $y$ の微小回転の順序を入れ替えたときのずれは、 $z$ 軸まわりの微小回転になっている。

この古典の結果を、量子力学の生成子の言葉に翻訳する。 $i\hbar$ の係数まで含めて導出できることを見よう。

先ほどの量子力学の計算で、順序の差は

```math
\text{順序 A} - \text{順序 B}
= \frac{1}{\hbar^2}\,\delta\alpha\,\delta\beta\,[G_x, G_y]
```

だった。一方、古典の計算結果は「ずれが $z$ 軸まわりの角度 $\delta\gamma = -\delta\alpha\,\delta\beta$ の微小回転である」と言っている。量子力学では、 $z$ 軸まわりの微小回転は

```math
U(\delta\gamma, \hat{z}) = I - \frac{i}{\hbar}\,\delta\gamma\,G_z
```

なので、「ずれ」は

```math
U(\delta\gamma, \hat{z}) - I = -\frac{i}{\hbar}\,\delta\gamma\,G_z
= -\frac{i}{\hbar}\,(-\delta\alpha\,\delta\beta)\,G_z
= \frac{i}{\hbar}\,\delta\alpha\,\delta\beta\,G_z
```

両者を等しいと置く。

```math
\frac{1}{\hbar^2}\,\delta\alpha\,\delta\beta\,[G_x, G_y]
= \frac{i}{\hbar}\,\delta\alpha\,\delta\beta\,G_z
```

両辺から $\delta\alpha\,\delta\beta$ を消し、 $\hbar^2$ を掛けると

```math
[G_x, G_y] = i\hbar\,G_z
```

が出る。**$i\hbar$ は要請ではなく、導かれた係数である。** その起源を分解すると

- $i$ は、微小回転演算子を $U = I - \frac{i}{\hbar}\delta\theta\,G$ （ $G$ はエルミート）と書いたことから来る
- $\hbar$ は、同じ式の $1/\hbar$ の分母と二次の $1/\hbar^2$ の比から来る

同様に $y$ と $z$ 、 $z$ と $x$ の組み合わせでも同じ計算ができて

```math
[G_x, G_y] = i\hbar\,G_z, \qquad
[G_y, G_z] = i\hbar\,G_x, \qquad
[G_z, G_x] = i\hbar\,G_y
```

が導かれる。まとめると

```math
[G_i, G_j] = i\hbar\,\epsilon_{ijk}\,G_k
```

である。

つまりこの交換関係は、「 $x$ と $y$ の回転を入れ替えると $z$ の回転がずれとして出る」という3次元回転の幾何学的性質を、演算子の言葉に翻訳したものである。回転の生成子であるなら、この関係を満たさなければならない。

### なぜ交換関係が十分なのか

逆に、3つのエルミート演算子 $J_x, J_y, J_z$ がこの交換関係を満たしているとする。そこから本当に回転演算子が作れるか。

[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で見たように、有限回転は微小回転の積み重ねで作れる。

```math
U(\theta, \mathbf{n}) = \lim_{N\to\infty}\left(I - \frac{i}{\hbar}\frac{\theta}{N}\,\mathbf{n}\cdot\mathbf{J}\right)^N
= \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

ここで問題は、こうして作った $U$ が「本物の回転」として正しく振る舞うかである。つまり

- $x$ 軸まわりに $\alpha$ 回してから $y$ 軸まわりに $\beta$ 回した結果が
- 幾何学的に正しい合成回転になっているか

という問いである。

答えはこうである。有限回転の合成は、微小回転を何度も交互に重ねることに帰着する。そして微小回転どうしを入れ替えるたびに出てくるずれは、いま見たように交換子 $[G_i, G_j]$ で決まる。

交換関係が正しければ、微小回転の入れ替えのたびに出るずれは、幾何学の要求と一致する。微小回転を何万回積んでも、各ステップのずれが正しいなら、最終結果も正しい。

たとえるなら、交換関係はレンガの噛み合わせの規格のようなものである。レンガ1個1個の噛み合わせが正しければ、それを何段積んでも壁全体が正しく組み上がる。交換関係は各微小回転の「噛み合わせ」を規定しているので、それさえ合っていれば有限回転は自動的に正しくなる。

### 軌道角運動量はこの特殊例にすぎない

[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で導いた $\hat{L}_z = \hat{x}\hat{p}_y - \hat{y}\hat{p}_x$ は、位置と運動量を持つ粒子において、上の交換関係を満たす生成子を**具体的に構成した**ものである。

しかし交換関係の定義は、 $\mathbf{r} \times \mathbf{p}$ という構成法を要求していない。位置や運動量を一切持たない自由度でも、3つのエルミート演算子が交換関係を満たしさえすれば、それは角運動量である。

### パウリ行列はこの条件を満たす

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で直接計算したように

```math
[\sigma_i, \sigma_j] = 2i\,\epsilon_{ijk}\,\sigma_k
```

が成り立つ。したがって $S_i = \frac{\hbar}{2}\sigma_i$ とおけば

```math
[S_i, S_j] = i\hbar\,\epsilon_{ijk}\,S_k
```

が成り立つ。これは角運動量の定義そのものである。

しかも $S_i$ は $2 \times 2$ の行列であり、位置 $\hat{x}$ や運動量 $\hat{p}$ とは何の関係もない。つまり $\mathbf{S}$ は

- $\mathbf{r} \times \mathbf{p}$ から作られたのではない
- しかし回転の生成子としての交換関係を満たす
- したがって角運動量である

これが**スピン角運動量**と呼ばれるものの正体である。「空間を動き回ることに由来しない角運動量」であり、粒子の**内部自由度**に宿る角運動量である。

しかも $\mathbf{S}$ は $2 \times 2$ 行列なので、角運動量の2次元既約表現になっている。角運動量の理論では、既約表現は量子数 $j = 0, 1/2, 1, 3/2, \ldots$ で分類される。2次元に対応するのは $j = 1/2$ だけなので、パウリ行列から作った $\mathbf{S}$ は**スピン 1/2** の角運動量だと確定する。

### まとめ： $\boldsymbol{\sigma}$ が角運動量である理由

流れを整理する。

1. 回転の生成子は交換関係 $[J_i, J_j] = i\hbar\,\epsilon_{ijk}\,J_k$ を満たす（回転の幾何から要請される）
2. この交換関係を満たすものを角運動量と定義する（ $\mathbf{r} \times \mathbf{p}$ は特殊例にすぎない）
3. $S_i = \frac{\hbar}{2}\sigma_i$ はこの交換関係を満たす（[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で計算済み）
4. したがって $\mathbf{S}$ は角運動量であり、回転演算子 $U = \exp(-i\theta\,\mathbf{n}\cdot\mathbf{J}/\hbar)$ の $\mathbf{J}$ として使える

---

## 第2段階：代入して $\theta/2$ を出す

### 出発点

純粋なスピン自由度だけを扱う場合（空間的な運動は考えない）には

```math
\mathbf{J} = \mathbf{S}
```

である。前節で確認したように、スピン 1/2 のスピン演算子は

```math
S_i = \frac{\hbar}{2}\,\sigma_i \qquad (i = x, y, z)
```

なので

```math
\mathbf{n}\cdot\mathbf{J}
= \mathbf{n}\cdot\mathbf{S}
= n_x S_x + n_y S_y + n_z S_z
= \frac{\hbar}{2}(n_x\sigma_x + n_y\sigma_y + n_z\sigma_z)
= \frac{\hbar}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
```

である。これを回転演算子に代入すると

```math
U(\theta,\mathbf{n})
= \exp\!\left(-\frac{i}{\hbar}\,\theta\cdot\frac{\hbar}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
```

$\hbar$ が約分されて

```math
\boxed{
U(\theta,\mathbf{n})
= \exp\!\left(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}\right)
}
```

が得られる。

### $\theta/2$ はどこから来たか

ここで $\theta/2$ が出る仕組みを確認しておく。もとの式

```math
\exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

には $\hbar$ が分母にある。一方、スピン 1/2 では $\mathbf{J} = \frac{\hbar}{2}\boldsymbol{\sigma}$ なので、分子にも $\hbar$ が入っている。この二つの $\hbar$ が消え合い、後に残るのは $1/2$ だけである。

つまり $\theta/2$ の $1/2$ は、スピン 1/2 の「1/2」そのものである。スピン量子数が $s$ なら角運動量は $\hbar s$ のスケールを持つので、一般に指数の中に $s$ が現れる。 $s = 1/2$ だから $\theta/2$ になる。

---

## 第3段階：行列の指数関数を計算する

### パウリ行列の便利な性質

回転行列を具体的に書き下すには、 $\exp(-i\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma})$ を計算しなければならない。行列の指数関数は一般に複雑だが、パウリ行列には特別な性質がある。

まず $\mathbf{n}\cdot\boldsymbol{\sigma}$ を書き下す。 $\mathbf{n} = (n_x, n_y, n_z)$ として

```math
\mathbf{n}\cdot\boldsymbol{\sigma}
= n_x\begin{pmatrix}0&1\\1&0\end{pmatrix}
+ n_y\begin{pmatrix}0&-i\\i&0\end{pmatrix}
+ n_z\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= \begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
```

この行列を $M$ とおいて、 $M^2$ を計算する。

```math
M^2 = \begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
\begin{pmatrix}n_z & n_x - in_y \\ n_x + in_y & -n_z\end{pmatrix}
```

$(1,1)$ 成分：

```math
n_z^2 + (n_x - in_y)(n_x + in_y)
= n_z^2 + n_x^2 + n_y^2
= 1
```

（ $\mathbf{n}$ は単位ベクトルなので $n_x^2 + n_y^2 + n_z^2 = 1$ ）

$(1,2)$ 成分：

```math
n_z(n_x - in_y) + (n_x - in_y)(-n_z) = 0
```

同様に $(2,1) = 0$, $(2,2) = 1$ 。したがって

```math
(\mathbf{n}\cdot\boldsymbol{\sigma})^2 = I
```

これはパウリ行列に特有の性質であり、 $\mathbf{n}$ が単位ベクトルであることだけから出る。

### 指数関数の展開

$M^2 = I$ を使うと、 $M$ の冪は2通りしかない。

```math
M^0 = I, \quad M^1 = M, \quad M^2 = I, \quad M^3 = M, \quad \ldots
```

つまり偶数乗は $I$ 、奇数乗は $M$ である。

行列の指数関数の定義は

```math
e^{-i\alpha M}
= \sum_{k=0}^{\infty}\frac{(-i\alpha)^k}{k!}M^k
```

であり（ $\alpha = \theta/2$ とする）、これを偶数項と奇数項に分ける。

```math
= \sum_{k\,\text{even}}\frac{(-i\alpha)^k}{k!}\,I
\;+\;\sum_{k\,\text{odd}}\frac{(-i\alpha)^k}{k!}\,M
```

偶数項の係数は

```math
\sum_{k\,\text{even}}\frac{(-i\alpha)^k}{k!}
= 1 - \frac{\alpha^2}{2!} + \frac{\alpha^4}{4!} - \cdots
= \cos\alpha
```

奇数項の係数は

```math
\sum_{k\,\text{odd}}\frac{(-i\alpha)^k}{k!}
= -i\alpha + \frac{i\alpha^3}{3!} - \cdots
= -i\!\left(\alpha - \frac{\alpha^3}{3!} + \cdots\right)
= -i\sin\alpha
```

したがって

```math
e^{-i\alpha M} = \cos\alpha\,I - i\sin\alpha\,M
```

$\alpha = \theta/2$, $M = \mathbf{n}\cdot\boldsymbol{\sigma}$ を戻すと

```math
\boxed{
U(\theta,\mathbf{n})
= \cos\frac{\theta}{2}\,I
- i\sin\frac{\theta}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
}
```

これがスピン 1/2 の回転行列の完全な形である。

---

## 第4段階：具体例で確かめる

### 例1： $z$ 軸まわりの回転

$\mathbf{n} = (0,0,1)$ とすると $\mathbf{n}\cdot\boldsymbol{\sigma} = \sigma_z$ なので

```math
U(\theta, \hat{z})
= \cos\frac{\theta}{2}\begin{pmatrix}1&0\\0&1\end{pmatrix}
- i\sin\frac{\theta}{2}\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= \begin{pmatrix}
\cos\frac{\theta}{2} - i\sin\frac{\theta}{2} & 0 \\
0 & \cos\frac{\theta}{2} + i\sin\frac{\theta}{2}
\end{pmatrix}
```

オイラーの公式 $e^{-i\alpha} = \cos\alpha - i\sin\alpha$ を使うと

```math
U(\theta, \hat{z})
= \begin{pmatrix}
e^{-i\theta/2} & 0 \\
0 & e^{+i\theta/2}
\end{pmatrix}
```

$\vert {+z}\rangle$ と $\vert {-z}\rangle$ にそれぞれ逆符号の位相がつく。これだけでは「回転」のイメージが湧きにくいので、具体的な状態に作用させてみよう。

$\vert {+x}\rangle$ は [PHYSICS_NOTE.md](PHYSICS_NOTE.md) で導いたように

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
```

である。これにブロッホ球上で赤道上（ $x$ 方向）の状態だった。 $U(\theta, \hat{z})$ を作用させると

```math
U(\theta, \hat{z})\,\vert {+x}\rangle
= \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}e^{-i\theta/2}\\e^{+i\theta/2}\end{pmatrix}
```

全体位相 $e^{-i\theta/2}$ を括り出すと

```math
= \frac{e^{-i\theta/2}}{\sqrt{2}}\begin{pmatrix}1\\e^{+i\theta}\end{pmatrix}
```

全体位相は物理に影響しないので無視すると

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i\theta}\end{pmatrix}
```

が得られる。[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で見たように、この形は

```math
\frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

の赤道状態であり、 $\phi$ は赤道上の方位角だった。 $\phi = 0$ が $\vert {+x}\rangle$ 、 $\phi = \pi/2$ が $\vert {+y}\rangle$ だった。

上の結果では $\phi = \theta$ である。つまり、もとの $\vert {+x}\rangle$ （方位角 $0$ ）がブロッホ球の赤道上で方位角 $\theta$ の位置に移った。これはまさに $z$ 軸まわりに角度 $\theta$ だけ回転したことを意味する。

一方、 $\vert {+z}\rangle$ （北極）と $\vert {-z}\rangle$ （南極）に作用させると

```math
U(\theta, \hat{z})\,\vert {+z}\rangle = e^{-i\theta/2}\vert {+z}\rangle, \qquad
U(\theta, \hat{z})\,\vert {-z}\rangle = e^{+i\theta/2}\vert {-z}\rangle
```

どちらも全体位相が変わるだけで、ブロッホ球上では動かない。 $z$ 軸まわりの回転で北極と南極が動かないのは当然である。

### 例2： $x$ 軸まわりに 180 度回転

$\mathbf{n} = (1,0,0)$, $\theta = \pi$ とすると

```math
U(\pi, \hat{x})
= \cos\frac{\pi}{2}\,I - i\sin\frac{\pi}{2}\,\sigma_x
= 0\cdot I - i\cdot 1\cdot\sigma_x
= -i\sigma_x
= -i\begin{pmatrix}0&1\\1&0\end{pmatrix}
= \begin{pmatrix}0&-i\\-i&0\end{pmatrix}
```

これを $\vert {+z}\rangle$ に作用させると

```math
U(\pi, \hat{x})\vert {+z}\rangle
= \begin{pmatrix}0&-i\\-i&0\end{pmatrix}\begin{pmatrix}1\\0\end{pmatrix}
= \begin{pmatrix}0\\-i\end{pmatrix}
= -i\begin{pmatrix}0\\1\end{pmatrix}
= -i\,\vert {-z}\rangle
```

全体位相 $-i$ を除けば $\vert {-z}\rangle$ になっている。 $x$ 軸まわりの 180 度回転で、北極が南極に移る。ブロッホ球の絵で考えれば当然の結果である。

---

## 思考実験：古典的に $\theta$ 回したら、ブロッホ球上でも $\theta$ 動くか

### 問いの設定

いま、スピン 1/2 の粒子が状態 $\vert \psi\rangle$ にあり、ブロッホ球上のある点を指しているとする。

この粒子を**古典的に** $\theta$ だけ回転させたとする。たとえばブロッホ球そのものを手で $\theta$ だけ回すようなイメージである。

このとき、ブロッホベクトル（測定統計を表す矢印）は $\theta$ だけ動くか、それとも $\theta/2$ だけしか動かないか。

回転演算子には $\theta/2$ が入っているので、「ブロッホベクトルも半分しか動かないのでは？」と思うかもしれない。答えを確かめよう。

### 具体例で確かめる

$z$ 軸まわりに角度 $\theta$ だけ回転させる。例1で見たように

```math
U(\theta, \hat{z}) = \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
```

である。初期状態を $\vert {+x}\rangle$ （ブロッホ球の赤道上、方位角 $\phi = 0$ ）とする。

例1で計算したように、回転後の状態は（全体位相を除くと）

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i\theta}\end{pmatrix}
```

であり、方位角が $0 \to \theta$ に移った。つまり**ブロッホベクトルは $\theta$ だけ動いている**。 $\theta/2$ ではない。

もう一例。初期状態を $\vert {+y}\rangle$ （方位角 $\phi = \pi/2$ ）にする。

```math
U(\theta, \hat{z})\,\vert {+y}\rangle
= \begin{pmatrix}e^{-i\theta/2} & 0 \\ 0 & e^{+i\theta/2}\end{pmatrix}
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}e^{-i\theta/2}\\i\,e^{+i\theta/2}\end{pmatrix}
```

全体位相 $e^{-i\theta/2}$ を括り出すと

```math
= \frac{e^{-i\theta/2}}{\sqrt{2}}\begin{pmatrix}1\\i\,e^{i\theta}\end{pmatrix}
```

$i = e^{i\pi/2}$ なので $i\,e^{i\theta} = e^{i(\theta + \pi/2)}$ 。したがって全体位相を除くと

```math
\frac{1}{\sqrt{2}}\begin{pmatrix}1\\e^{i(\theta + \pi/2)}\end{pmatrix}
```

方位角が $\pi/2 \to \theta + \pi/2$ に移った。やはり**方位角の変化は $\theta$** であり、 $\theta/2$ ではない。

### なぜ $\theta/2$ ではなく $\theta$ なのか

状態ベクトルの中には確かに $\theta/2$ が入っている。 $\vert {+z}\rangle$ 成分には $e^{-i\theta/2}$ 、 $\vert {-z}\rangle$ 成分には $e^{+i\theta/2}$ がかかる。

しかしブロッホ球上の方位角を決めるのは、2成分の**相対位相**である。

```math
\frac{e^{+i\theta/2}}{e^{-i\theta/2}} = e^{i\theta}
```

$+\theta/2$ と $-\theta/2$ の差は $\theta$ になる。2成分に逆符号で $\theta/2$ ずつ位相がつくので、相対位相は $\theta$ 変化する。

これが、回転演算子に $\theta/2$ が入っているにもかかわらず、ブロッホベクトルが $\theta$ だけ動く仕組みである。

### 赤道だけでなく、一般の状態でも成り立つ

$z$ 軸まわりの回転について赤道上の状態で確かめたが、これは一般の状態でも同じである。

一般の状態 $\vert \psi\rangle = \cos(\alpha/2)\vert {+z}\rangle + e^{i\phi}\sin(\alpha/2)\vert {-z}\rangle$ （ブロッホ球の極角 $\alpha$ 、方位角 $\phi$ ）に $U(\theta, \hat{z})$ を作用させると

```math
U(\theta, \hat{z})\vert \psi\rangle
= e^{-i\theta/2}\cos\frac{\alpha}{2}\vert {+z}\rangle + e^{i(\phi+\theta/2)}\sin\frac{\alpha}{2}\vert {-z}\rangle
```

全体位相 $e^{-i\theta/2}$ を括り出すと

```math
= e^{-i\theta/2}\left(\cos\frac{\alpha}{2}\vert {+z}\rangle + e^{i(\phi+\theta)}\sin\frac{\alpha}{2}\vert {-z}\rangle\right)
```

極角 $\alpha$ は変わらず、方位角が $\phi \to \phi + \theta$ に変わった。 $z$ 軸まわりに $\theta$ だけ回転している。

### まとめ：二重構造

古典的に $\theta$ 回すと、

- **状態ベクトル**（スピノル）は $\theta/2$ の位相変化を受ける
- **ブロッホベクトル**（測定統計）は $\theta$ だけ回転する

この二重構造は、状態ベクトルからブロッホベクトルへの対応が多対一であることから来ている。 $\vert \psi\rangle$ と $e^{i\chi}\vert \psi\rangle$ （全体位相が違うだけ）はブロッホ球上で同じ点を指す。特に $\vert \psi\rangle$ と $-\vert \psi\rangle$ も同じ点になる。

数学の言葉では、スピン 1/2 の回転演算子は回転群 $\mathrm{SO}(3)$ そのものではなく、その**二重被覆**である $\mathrm{SU}(2)$ の表現になっている。 $\mathrm{SU}(2)$ の2つの元（ $U$ と $-U$ ）が $\mathrm{SO}(3)$ の1つの回転に対応する——だから状態ベクトルは $4\pi$ で一周するが、ブロッホベクトル（つまり物理的な測定統計）は $2\pi$ で一周する。

したがって、答えは明確である。

> 古典的に $\theta$ 回したら、ブロッホベクトルも $\theta$ 動く。 $\theta/2$ ではない。

---

## 第5段階：360 度回転で元に戻らない

### 計算

$\theta = 2\pi$ （360 度）を代入する。

```math
U(2\pi,\mathbf{n})
= \cos\pi\,I - i\sin\pi\,\mathbf{n}\cdot\boldsymbol{\sigma}
= (-1)\cdot I - i\cdot 0\cdot\mathbf{n}\cdot\boldsymbol{\sigma}
= -I
```

つまり、どの軸まわりでも 360 度回転すると

```math
\vert \psi\rangle \to -\vert \psi\rangle
```

になる。状態ベクトルは元に戻らず、**符号が反転する**。

ただし、物理状態としてはどうか。量子力学では $\vert \psi\rangle$ と $-\vert \psi\rangle$ は同じ射線（全体位相が違うだけ）なので、単独の測定ではすべての確率が一致し、区別できない。つまり「状態ベクトルは符号反転するが、物理的な観測量は変わらない」——この符号差が見えるのは、干渉実験で別の経路と比較したときだけである。

### 720 度で戻る

$\theta = 4\pi$ （720 度）を代入すると

```math
U(4\pi,\mathbf{n})
= \cos 2\pi\,I - i\sin 2\pi\,\mathbf{n}\cdot\boldsymbol{\sigma}
= (+1)\cdot I - 0
= I
```

720 度回転して初めて $\vert \psi\rangle \to \vert \psi\rangle$ に戻る。

### なぜ 360 度で戻らないのか

この原因は $\theta/2$ にある。回転角 $\theta$ に対して、行列の中には $\cos(\theta/2)$ と $\sin(\theta/2)$ が入っている。三角関数は $2\pi$ で一周するから、 $\theta/2 = 2\pi$ すなわち $\theta = 4\pi$ で一周する。

言い換えれば

- **古典的な回転**は $2\pi$ で一周する
- **スピン 1/2 の状態ベクトル**は $4\pi$ で一周する

この「半分の速さで回る」性質は、 $s = 1/2$ という値に直結している。

### 観測にかかるか

$\vert \psi\rangle$ と $-\vert \psi\rangle$ は、単独の測定では区別できない。確率は $\vert \langle\phi\vert \psi\rangle\vert ^2$ で計算され、全体位相 $-1$ は二乗で消えるからである。

しかし、ある粒子のスピンを2つの経路に分け、片方だけを 360 度回転してから再び合流させると、 $-1$ の符号差が**干渉**として観測される。これは中性子干渉実験で実際に確認されている。

---

## なぜ $1/2$ なのか：もう少し広い視点

### 角運動量量子数と回転の周期

一般に、角運動量量子数 $j$ を持つ系では

```math
U(\theta,\mathbf{n}) = \exp\!\left(-\frac{i}{\hbar}\,\theta\,\mathbf{n}\cdot\mathbf{J}\right)
```

であり、 $\mathbf{J}$ の固有値は $-j\hbar$ から $+j\hbar$ まで整数刻みで並ぶ。

$z$ 軸まわりの回転では $U = e^{-i\theta J_z/\hbar}$ であり、 $J_z$ の固有値 $m\hbar$ （ $m = -j, -j+1, \ldots, +j$ ）に対して各成分に $e^{-im\theta}$ がかかる。

全成分が元に戻る条件は $e^{-im\theta} = 1$ が全ての $m$ で成り立つことである。

- $j$ が整数（ $j = 0, 1, 2, \ldots$ ）なら $m$ も整数なので、 $\theta = 2\pi$ で全部戻る
- $j$ が半整数（ $j = 1/2, 3/2, \ldots$ ）なら $m$ に半整数が含まれるので、 $\theta = 2\pi$ では $e^{-i\cdot(1/2)\cdot 2\pi} = e^{-i\pi} = -1$ となり、戻らない。 $\theta = 4\pi$ で戻る

スピン 1/2 は $j = 1/2$ の最も単純な場合である。

ここでも 360 度回転と同じ注意が当てはまる。状態ベクトルとしての周期は半整数 $j$ で $4\pi$、整数 $j$ で $2\pi$ である。ただし半整数 $j$ の $2\pi$ 回転で生じる $-1$ は全体位相なので、単独の測定確率は変わらない。スピン 1/2 の場合には、ブロッホベクトルの向きは $2\pi$ で元に戻る。半整数 $j$ の符号反転が見えるのは干渉実験だけである。

---

## 全体の論理構造（振り返り）

```
回転の生成子は [J_i, J_j] = iℏε_{ijk}J_k を満たす（回転の幾何から）
    ↓
この交換関係を満たすものが角運動量（r×p は特殊例）
    ↓
S_i = (ℏ/2)σ_i がこの交換関係を満たす → スピンは角運動量
    ↓
U(θ,n) = exp(−iθ n·J/ℏ) に J = S = (ℏ/2)σ を代入
    ↓
ℏ が消える → U = exp(−iθ/2 n·σ)
    ↓
(n·σ)² = I を示す → 指数関数を cos + sin に分解できる
    ↓
U = cos(θ/2) I − i sin(θ/2) n·σ
    ↓
θ = 2π で U = −I （360度で符号反転）
    ↓
θ = 4π で U = +I （720度で元に戻る）
```

$\theta/2$ の起源は $S_i = \hbar\sigma_i/2$ の $1/2$ であり、その $1/2$ はスピン量子数 $s = 1/2$ そのものである。そして $\mathbf{S}$ が角運動量として $\mathbf{J}$ に代入できるのは、 $\mathbf{r} \times \mathbf{p}$ という出自を持つからではなく、回転の交換関係を満たすからである。

---

**次の文書**: [PHYSICS_NOTE5.md — ベルの不等式](PHYSICS_NOTE5.md) では、本文書で整備した回転・固有状態の道具を使って、2粒子系の相関からベルの不等式を導く。
