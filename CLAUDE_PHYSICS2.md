# 実験事実からパウリ行列を導く

## この文書の方針

この文書は、パウリ行列 $\sigma_x, \sigma_y, \sigma_z$ を「便利な道具」として天下りに置くのではなく、実験事実から一歩ずつ導く。

必要な前提は次の三つだけである。

1. ある種の粒子に磁場をかけると、進路が**ちょうど2本**に分かれる（シュテルン・ゲルラッハ実験）
2. 量子力学では、状態はベクトル、物理量はエルミート演算子で表される
3. 測定で値 $a$ が確定的に出る状態は、その演算子の固有値 $a$ に属する固有ベクトルである

この三つから出発して、パウリ行列の形がすべて決まることを示す。

---

## 全体の筋

流れは5段階ある。

1. **$z$ 方向の測定が二値** → 2次元空間と $\sigma_z$ が決まる
2. **$x$ 方向の測定が半々** → $\sigma_x$ の固有状態が決まる（位相の自由度が残る）
3. **位相規約を選ぶ** → $\sigma_x$ の行列が確定する
4. **$y$ 方向が必要** → 複素数が避けられず、$\sigma_y$ が確定する
5. **交換関係の検証** → 3つの行列がスピン演算子であることが分かる

---

## 第1段階：$z$ 方向の測定から $\sigma_z$ へ

### 実験事実

粒子線を $z$ 方向の不均一磁場に通すと、スクリーン上に2本のスポットが現れる。上側と下側の2つだけである。

ここから分かることは

- この内部自由度は $z$ 方向について2値しか返さない
- したがって状態空間は（少なくとも）2次元である

最小のモデルとして、2次元の複素ベクトル空間を採用する。

### 固有状態を置く

$z$ 測定で上側に出た粒子をもう一度 $z$ 方向で測ると、必ず上側になる。下側も同様に再現される。したがって

- $z$ 測定には2つの確定状態がある
- 一方が「必ず上（$+1$）」、他方が「必ず下（$-1$）」を返す

この2状態を $|{+z}\rangle$, $|{-z}\rangle$ と書く。両者は完全に区別可能なので直交し、確率1の状態なので正規化されている。

```math
\langle{+z}|{+z}\rangle = 1, \qquad
\langle{-z}|{-z}\rangle = 1, \qquad
\langle{+z}|{-z}\rangle = 0
```

### 測定演算子を作る

$z$ 測定の結果を $+1$, $-1$ に対応させると、測定演算子は

```math
\hat{Z} = (+1)|{+z}\rangle\langle{+z}| + (-1)|{-z}\rangle\langle{-z}|
```

と書ける。実際に固有値方程式を確かめると

```math
\hat{Z}|{+z}\rangle = +|{+z}\rangle, \qquad
\hat{Z}|{-z}\rangle = -|{-z}\rangle
```

となり、確かに $|{+z}\rangle$ は固有値 $+1$、$|{-z}\rangle$ は固有値 $-1$ に属する。

### 行列表示

この2状態を計算基底に選ぶ。

```math
|{+z}\rangle = \begin{pmatrix}1\\0\end{pmatrix}, \qquad
|{-z}\rangle = \begin{pmatrix}0\\1\end{pmatrix}
```

すると $\hat{Z}$ の行列表示は

```math
\sigma_z =
\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}
```

である。これが最初のパウリ行列 $\sigma_z$ であり、「$z$ 方向の測定で2値が出る」という事実をそのまま行列にしたものにすぎない。

### 任意の状態

2次元空間の基底が決まったので、この系の任意の状態は

```math
|\psi\rangle = \alpha|{+z}\rangle + \beta|{-z}\rangle
= \begin{pmatrix}\alpha\\\beta\end{pmatrix}
```

と書ける。ここで $\alpha, \beta$ は $|\alpha|^2 + |\beta|^2 = 1$ を満たす複素数である。

---

## 第2段階：$x$ 方向の測定から固有状態の形へ

### 実験事実

$z$ 方向で上側を選んだ粒子を、今度は $x$ 方向の装置に入れる。すると

- $x$ 方向の上と下が**半々**で出る

さらに

- $x$ で上を選んでもう一度 $x$ を測ると、必ず上になる
- しかしその後 $z$ を測ると、$z$ の結果は半々に戻る

つまり $z$ と $x$ は同時には確定せず、$x$ にも独自の2つの確定状態がある。

### $x$ の固有状態を $z$ 基底で表す

$x$ 方向にも2つの固有状態 $|{+x}\rangle$, $|{-x}\rangle$ がある。これらは同じ2次元空間の中に住んでいるので、$z$ 基底で書けるはずである。

```math
|{+x}\rangle = a|{+z}\rangle + b|{-z}\rangle
```

「$|{+z}\rangle$ を $x$ で測ると半々」という条件は

```math
|\langle{+x}|{+z}\rangle|^2 = \frac{1}{2}
```

を意味する。$\langle{+x}|{+z}\rangle = a^*$ なので $|a|^2 = 1/2$。正規化 $|a|^2 + |b|^2 = 1$ から $|b|^2 = 1/2$ も得られる。

したがって

```math
|{+x}\rangle = \frac{1}{\sqrt{2}}\bigl(e^{i\alpha}|{+z}\rangle + e^{i\beta}|{-z}\rangle\bigr)
```

の形になる。ここで $e^{i\alpha}$, $e^{i\beta}$ は絶対値1の位相因子である。

### 位相の自由度を数える

量子力学では、状態ベクトル全体に共通の位相 $e^{i\gamma}$ を掛けても物理は変わらない。この自由度を使って $e^{i\alpha} = 1$ と選ぶことができる。すると

```math
|{+x}\rangle = \frac{1}{\sqrt{2}}\bigl(|{+z}\rangle + e^{i\phi}|{-z}\rangle\bigr)
```

のように、**相対位相** $e^{i\phi}$ だけが残る。

つまり「$z$ から見て半々」という条件を満たす状態は無限に存在し、それらは相対位相 $\phi$ で区別される。

---

## 第3段階：位相規約を選んで $\sigma_x$ を確定する

### $\phi$ の選択は物理的に何を意味するか

相対位相 $\phi$ が異なる状態は、$z$ 測定では区別できない（どれも半々）。しかし別方向の測定をすれば区別できる。したがって $\phi$ は物理的に意味のある量であり、ブロッホ球でいえば赤道上の方位角に対応する。

ここで $x$ 軸方向を定義するにあたって、位相規約を選ぶ。**$z$ 基底で書いたとき実数係数になる方向を $x$ と呼ぶ** ことにする。すなわち

```math
\phi = 0
```

を選ぶ。すると

```math
|{+x}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}, \qquad
|{-x}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
```

となる。$|{-x}\rangle$ の形は、$|{+x}\rangle$ と直交する条件 $\langle{-x}|{+x}\rangle = 0$ から決まる（同じく $|{-z}\rangle$ 成分の符号だけが自由だが、$\phi = 0$ の規約のもとでは $-1$ になる）。

### なぜこれが「規約」なのか

「$\phi = 0$ を選ぶ」とは、3次元空間の中で $z$ 軸に対して垂直な一方向を、$x$ 軸と名付けるということである。$z$ 軸だけでは水平面内の向きは決まらないので、どこを $x$ と呼ぶかは規約として選ばなければならない。$\phi = 0$ はその選択であり、物理法則ではない。

### $\sigma_x$ を書き下す

$|{+x}\rangle$ が固有値 $+1$、$|{-x}\rangle$ が固有値 $-1$ を持つ演算子を作る。

```math
\hat{X} = (+1)|{+x}\rangle\langle{+x}| + (-1)|{-x}\rangle\langle{-x}|
```

これを $z$ 基底で行列にする。

```math
|{+x}\rangle\langle{+x}|
= \frac{1}{2}\begin{pmatrix}1\\1\end{pmatrix}(1\;1)
= \frac{1}{2}\begin{pmatrix}1&1\\1&1\end{pmatrix}
```

```math
|{-x}\rangle\langle{-x}|
= \frac{1}{2}\begin{pmatrix}1\\-1\end{pmatrix}(1\;{-1})
= \frac{1}{2}\begin{pmatrix}1&-1\\-1&1\end{pmatrix}
```

したがって

```math
\hat{X}
= \frac{1}{2}\begin{pmatrix}1&1\\1&1\end{pmatrix}
- \frac{1}{2}\begin{pmatrix}1&-1\\-1&1\end{pmatrix}
= \begin{pmatrix}0&1\\1&0\end{pmatrix}
```

これが

```math
\sigma_x = \begin{pmatrix}0&1\\1&0\end{pmatrix}
```

である。

### 検算

固有値方程式を直接確かめる。

```math
\sigma_x\,|{+x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= +1 \cdot |{+x}\rangle \quad\checkmark
```

```math
\sigma_x\,|{-x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\1\end{pmatrix}
= -1 \cdot |{-x}\rangle \quad\checkmark
```

---

## 第4段階：$y$ 方向には複素数が必要

### なぜ $y$ は $x$ と同じではないのか

3次元空間には $z$ に垂直な方向が2つ（$x$ と $y$）ある。$z$ から見れば $x$ も $y$ も対等で、どちらも

- $|{+z}\rangle$ を測ると半々

を与える。ならば $x$ と $y$ は同じものではないか？

答えは否である。$x$ と $y$ は**異なる方向**の測定なので、**異なる固有状態**を持たなければならない。しかし「$z$ から見て半々」という条件だけでは $|a|^2 = |b|^2 = 1/2$ しか言えず、差は相対位相にしかない。

$x$ はすでに $\phi = 0$ を使った。$y$ が $x$ と異なるなら、$\phi \neq 0$ でなければならない。

### $y$ を $\phi = \pi/2$ に対応させる

$x$ 軸から 90 度回転した方向が $y$ 軸である。赤道上の方位角で $x$ を $\phi = 0$ に取ったので、$y$ は

```math
\phi = \frac{\pi}{2}
```

に対応する。$e^{i\pi/2} = i$ なので

```math
|{+y}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}, \qquad
|{-y}\rangle = \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
```

となる。

### なぜ $i$ が出るのか

$i$ は突然の思いつきではない。一般の「$z$ から見て半々」の状態は

```math
|\psi(\phi)\rangle = \frac{1}{\sqrt{2}}\bigl(|{+z}\rangle + e^{i\phi}|{-z}\rangle\bigr)
```

であり、$\phi$ は赤道上の方位角だった。$x$ が $\phi = 0$ なら、そこから 90 度回った $y$ は $\phi = \pi/2$ であり

```math
e^{i\pi/2} = i
```

になるだけである。

### 実数では足りない理由

もし係数を実数に限ると、相対位相は $+1$ か $-1$ しかない。$+1$ はすでに $x$ が使っている。$-1$ を使うと $|{-x}\rangle$ と同じ状態になってしまう。

つまり実数だけでは、$z$ に垂直な独立方向を1つしか表せない。3次元空間の3方向を2次元複素ベクトルで表すには、$i$ がどうしても必要になる。

### 測定統計の検算

この $|{+y}\rangle$, $|{-y}\rangle$ が実験事実と矛盾しないかを確かめる。

$|{+x}\rangle$ を $y$ で測る：

```math
\langle{+y}|{+x}\rangle
= \frac{1}{\sqrt{2}}(1,\,-i) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{2}(1 - i)
```

```math
|\langle{+y}|{+x}\rangle|^2
= \left|\frac{1-i}{2}\right|^2
= \frac{1+1}{4}
= \frac{1}{2} \quad\checkmark
```

$|{+y}\rangle$ を $x$ で測る：

```math
\langle{+x}|{+y}\rangle
= \frac{1}{\sqrt{2}}(1,\,1) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{2}(1 + i)
```

```math
|\langle{+x}|{+y}\rangle|^2
= \left|\frac{1+i}{2}\right|^2
= \frac{1}{2} \quad\checkmark
```

$|{+y}\rangle$ を $z$ で測る：

```math
|\langle{+z}|{+y}\rangle|^2
= \left|\frac{1}{\sqrt{2}}\right|^2
= \frac{1}{2} \quad\checkmark
```

$x$, $y$, $z$ のどの2方向を選んでも、一方の固有状態を他方で測れば半々になる。この対称性は、$y$ を $\phi = \pi/2$ に取る選択が実験と整合することを示している。

### $\sigma_y$ を書き下す

$|{+y}\rangle$ が固有値 $+1$、$|{-y}\rangle$ が固有値 $-1$ を持つ演算子を作る。

```math
\hat{Y} = (+1)|{+y}\rangle\langle{+y}| + (-1)|{-y}\rangle\langle{-y}|
```

$z$ 基底で各項を計算する。

```math
|{+y}\rangle\langle{+y}|
= \frac{1}{2}\begin{pmatrix}1\\i\end{pmatrix}(1\;{-i})
= \frac{1}{2}\begin{pmatrix}1&-i\\i&1\end{pmatrix}
```

```math
|{-y}\rangle\langle{-y}|
= \frac{1}{2}\begin{pmatrix}1\\-i\end{pmatrix}(1\;{i})
= \frac{1}{2}\begin{pmatrix}1&i\\-i&1\end{pmatrix}
```

したがって

```math
\hat{Y}
= \frac{1}{2}\begin{pmatrix}1&-i\\i&1\end{pmatrix}
- \frac{1}{2}\begin{pmatrix}1&i\\-i&1\end{pmatrix}
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

これが

```math
\sigma_y = \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

である。

### 検算

```math
\sigma_y\,|{+y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-i^2\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= +1 \cdot |{+y}\rangle \quad\checkmark
```

```math
\sigma_y\,|{-y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-(-i)(-i)\\i\cdot 1 + 0\end{pmatrix}
```

もう少し丁寧にやる。

```math
\sigma_y\,|{-y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}0\cdot 1 + (-i)(-i)\\i\cdot 1 + 0\cdot(-i)\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}i^2\\i\end{pmatrix}
```

ここで $(-i)(-i) = i^2 = -1$ なので

```math
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\i\end{pmatrix}
= -\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= -1\cdot|{-y}\rangle \quad\checkmark
```

---

## 第5段階：3つの行列がスピン演算子になること

### ここまでの整理

実験事実と位相規約だけから、3つの行列が決まった。

```math
\sigma_z = \begin{pmatrix}1&0\\0&-1\end{pmatrix}, \qquad
\sigma_x = \begin{pmatrix}0&1\\1&0\end{pmatrix}, \qquad
\sigma_y = \begin{pmatrix}0&-i\\i&0\end{pmatrix}
```

これらは「各方向の二値測定を表す行列」として導入された。しかし、これらが角運動量の交換関係を満たすことを確かめると、もっと深い意味が見えてくる。

### 交換関係の計算

角運動量の3成分は

```math
[S_i, S_j] = i\hbar\,\epsilon_{ijk}\,S_k
```

を満たすべきである。ここで $\epsilon_{ijk}$ は完全反対称テンソル（$\epsilon_{xyz} = 1$, 添字の巡回入替で $+1$, 奇置換で $-1$, 重複で $0$）。

まず $[\sigma_x, \sigma_y]$ を直接計算する。

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

したがって

```math
[\sigma_x, \sigma_y]
= \sigma_x\sigma_y - \sigma_y\sigma_x
= \begin{pmatrix}2i&0\\0&-2i\end{pmatrix}
= 2i\begin{pmatrix}1&0\\0&-1\end{pmatrix}
= 2i\,\sigma_z
```

同様に（同じ手順で行列を掛けるだけなので結果だけ示す）

```math
[\sigma_y, \sigma_z] = 2i\,\sigma_x, \qquad
[\sigma_z, \sigma_x] = 2i\,\sigma_y
```

これらをまとめると

```math
[\sigma_i, \sigma_j] = 2i\,\epsilon_{ijk}\,\sigma_k
```

である。

### スピン演算子への接続

ここで

```math
S_i = \frac{\hbar}{2}\,\sigma_i
```

と置くと

```math
[S_i, S_j]
= \frac{\hbar^2}{4}[\sigma_i, \sigma_j]
= \frac{\hbar^2}{4}\cdot 2i\,\epsilon_{ijk}\,\sigma_k
= i\hbar\,\epsilon_{ijk}\,\frac{\hbar}{2}\sigma_k
= i\hbar\,\epsilon_{ijk}\,S_k
```

となり、角運動量の交換関係が成り立つ。

### なぜこれで十分なのか

「交換関係を満たす」だけでは、パウリ行列がスピン 1/2 の演算子だと断言するには不十分に見えるかもしれない。実際、交換関係を満たすことは**必要条件**であって**十分条件**ではない。

しかし、次の数学的事実がある。

> 2次元空間において、角運動量の交換関係 $[S_i, S_j] = i\hbar\,\epsilon_{ijk}\,S_k$ を満たすエルミート行列の組は、ユニタリ基底変換を除いて本質的に一つしかない。

これは $\mathrm{SU}(2)$ の2次元既約表現の一意性という定理による。つまり、基底の取り方（座標軸の向き）を変えれば、交換関係を満たすどんなエルミート行列の組も $\hbar\sigma_i/2$ に一致する。

したがって、パウリ行列は

- 実験事実（二値測定、半々の統計）から形が決まる
- その形が角運動量の交換関係を自動的に満たす
- しかも2次元では、この交換関係を満たす表現は本質的にこれだけ

という三重の意味で、スピン 1/2 の演算子として確定する。

---

## まとめ：何が実験事実で、何が規約か

導出の中で使ったものを整理しておく。

### 実験事実（変えられない）

- 各方向の測定で結果が2値（$+1$ と $-1$）
- 同方向の再測定で結果が再現する
- 異方向の測定で確率が半々になる
- 一方の測定を挟むと他方の情報が失われる

### 規約（別の選び方もあり得る）

- $|{+z}\rangle = (1,0)^T$, $|{-z}\rangle = (0,1)^T$ という基底の取り方
- $x$ 方向の固有状態を実数係数で書く（$\phi = 0$）
- 右手系の約束で $y$ は $x$ から反時計回り 90 度（$\phi = \pi/2$）

### 導出された結果

- $\sigma_z, \sigma_x, \sigma_y$ の行列形
- $S_i = \hbar\sigma_i/2$ が角運動量の交換関係を満たすこと
- 2次元既約表現の一意性により、これがスピン 1/2 の唯一の表現であること

---

## 全体の論理構造（振り返り）

```
z方向の測定で2値が出る
    ↓
2つの固有状態 |+z⟩, |−z⟩ を基底にする
    ↓
測定演算子を書くと σ_z が出る
    ↓
x方向で測ると半々 → |+x⟩ の形が |a|=|b|=1/√2 に絞られる
    ↓
相対位相 e^{iφ} が残る → φ=0 を x と呼ぶ規約を選ぶ
    ↓
σ_x が確定する
    ↓
y方向にはφ≠0が必要 → 実数では足りない → φ=π/2 で i が出る
    ↓
σ_y が確定する
    ↓
3つの交換関係を計算 → 角運動量の代数と一致
    ↓
SU(2) の2次元既約表現の一意性 → スピン 1/2 の演算子として確定
```

どの段階にも天下りはない。実験事実が形を絞り、規約が残りの自由度を固定し、交換関係がスピンとの同定を保証する。
