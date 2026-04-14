# ブロッホ球：スピン状態を球面で見る

> **シリーズ構成**: [実験からパウリ行列へ](PHYSICS_NOTE.md) → [回転演算子](PHYSICS_NOTE2.md) → 本文書（PHYSICS_NOTE3.md）→ [θ/2 の由来](PHYSICS_NOTE4.md) → [ベルの不等式](PHYSICS_NOTE5.md)

## この文書の方針

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) では、スピン 1/2 の状態が

```math
\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle
```

と書けること、相対位相 $\phi$ が物理的に意味を持つことを見た。 $\phi = 0$ が $x$ 方向、 $\phi = \pi/2$ が $y$ 方向に対応するという結果も得た。

この文書では、任意のスピン状態を**球面上の1点**として表す方法——ブロッホ球——を導入する。ブロッホ球は単なる視覚的な道具ではなく、測定確率・状態の直交性・回転の効果をすべて幾何学的に読み取れる、スピン 1/2 の物理を凝縮した表現である。

---

## 全体の筋

流れは4段階ある。

1. **一般の状態をパラメータ化する** → 2つの実数パラメータ（極角と方位角）で書ける
2. **球面上の点と対応させる** → ブロッホ球の定義
3. **測定確率を幾何学的に読む** → 内積と球面上の角度の関係
4. **特別な点の意味を確認する** → 北極・南極・赤道・対蹠点

---

## 第1段階：状態を2つの角度で書く

### 出発点

スピン 1/2 の一般の状態は

```math
\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle
```

であり、正規化条件 $\vert \alpha\vert ^2 + \vert \beta\vert ^2 = 1$ を満たす。 $\alpha, \beta$ は複素数なので、実数パラメータとしては4つある（各複素数の実部と虚部）。

### 全体位相を除く

量子力学では、状態ベクトル全体に共通の位相 $e^{i\gamma}$ を掛けても物理は変わらない。すべての測定確率が $\vert \langle\phi\vert \psi\rangle\vert ^2$ の形で計算され、全体位相は絶対値の二乗で消えるからである。

この自由度を使って、 $\alpha$ を実数かつ非負に選ぶことができる。すると $\alpha = \vert \alpha\vert $ であり、正規化条件 $\alpha^2 + \vert \beta\vert ^2 = 1$ から、 $\alpha$ と $\vert \beta\vert $ は1つのパラメータで決まる。

具体的には、ある角度 $\theta$ （ $0 \leq \theta \leq \pi$ ）を使って

```math
\alpha = \cos\frac{\theta}{2}, \qquad \vert \beta\vert  = \sin\frac{\theta}{2}
```

と置ける。正規化条件 $\cos^2(\theta/2) + \sin^2(\theta/2) = 1$ は自動的に満たされる。

### なぜ $\theta/2$ なのか

ここで $\theta$ ではなく $\theta/2$ を使うのはなぜか。もちろん $\cos\eta$, $\sin\eta$ と置いて $\eta = \theta/2$ としても同じだが、 $\theta$ と書く物理的な理由がある。それを見るために、空間の一般方向 $\mathbf{n}$ の測定に対応する固有状態を求めてみよう。

#### 一般方向の測定演算子

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) では $z$, $x$, $y$ 方向の測定演算子としてパウリ行列 $\sigma_z, \sigma_x, \sigma_y$ を導いた。空間の一般方向 $\mathbf{n} = (n_x, n_y, n_z)$ の測定演算子は、これらの線形結合

```math
\mathbf{n}\cdot\boldsymbol{\sigma}
= n_x\sigma_x + n_y\sigma_y + n_z\sigma_z
= \begin{pmatrix} n_z & n_x - in_y \\ n_x + in_y & -n_z \end{pmatrix}
```

で与えられる。方向 $\mathbf{n}$ を極座標で $n_x = \sin\theta\cos\phi$, $n_y = \sin\theta\sin\phi$, $n_z = \cos\theta$ と書くと、対角成分はそのまま $\pm\cos\theta$ になる。非対角成分は

```math
n_x + in_y = \sin\theta\cos\phi + i\sin\theta\sin\phi = \sin\theta(\cos\phi + i\sin\phi) = \sin\theta\,e^{i\phi}
```

であり、もう一方は複素共役をとって

```math
n_x - in_y = \sin\theta\,e^{-i\phi}
```

となる。最後のステップではオイラーの公式 $e^{i\phi} = \cos\phi + i\sin\phi$ を使った。まとめると

```math
\mathbf{n}\cdot\boldsymbol{\sigma}
= \begin{pmatrix} \cos\theta & \sin\theta\,e^{-i\phi} \\ \sin\theta\,e^{i\phi} & -\cos\theta \end{pmatrix}
```

となる。

#### 固有状態を求める

この行列の固有値 $+1$ に属する固有状態 $\vert {+n}\rangle = \begin{pmatrix} a \\ b \end{pmatrix}$ を求める。固有値方程式の第1行は

```math
\cos\theta \cdot a + \sin\theta\,e^{-i\phi} \cdot b = a
```

整理すると

```math
\sin\theta\,e^{-i\phi} \cdot b = (1 - \cos\theta)\,a
```

ここで三角関数の半角公式を使う。

```math
1 - \cos\theta = 2\sin^2\frac{\theta}{2}, \qquad
\sin\theta = 2\sin\frac{\theta}{2}\cos\frac{\theta}{2}
```

代入すると

```math
2\sin\frac{\theta}{2}\cos\frac{\theta}{2}\,e^{-i\phi} \cdot b
= 2\sin^2\frac{\theta}{2} \cdot a
```

両辺を $2\sin(\theta/2)$ で割ると（ $\theta = 0$ の場合は後で別に確認する）

```math
\cos\frac{\theta}{2}\,e^{-i\phi} \cdot b = \sin\frac{\theta}{2} \cdot a
```

したがって $a$ と $b$ の比は

```math
\frac{b}{a} = \frac{\sin(\theta/2)}{\cos(\theta/2)}\,e^{i\phi}
```

正規化 $\vert a\vert ^2 + \vert b\vert ^2 = 1$ と、 $a$ を実数かつ非負に選ぶ自由度を使えば

```math
a = \cos\frac{\theta}{2}, \qquad b = e^{i\phi}\sin\frac{\theta}{2}
```

と決まる。つまり

```math
\vert {+n}\rangle = \cos\frac{\theta}{2}\vert {+z}\rangle + e^{i\phi}\sin\frac{\theta}{2}\vert {-z}\rangle
```

#### 既知の結果との整合

念のため、[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で求めた特殊な場合と合うか確認しよう。

- **$z$ 方向** （ $\theta = 0$ ）： $\cos 0 = 1$, $\sin 0 = 0$ なので $\vert {+n}\rangle = \vert {+z}\rangle$ $\checkmark$
- **$x$ 方向** （ $\theta = \pi/2$, $\phi = 0$ ）： $\cos(\pi/4) = \sin(\pi/4) = 1/\sqrt{2}$, $e^{i\cdot 0} = 1$ なので $\vert {+n}\rangle = \frac{1}{\sqrt{2}}(\vert {+z}\rangle + \vert {-z}\rangle) = \vert {+x}\rangle$ $\checkmark$
- **$y$ 方向** （ $\theta = \pi/2$, $\phi = \pi/2$ ）： $e^{i\pi/2} = i$ なので $\vert {+n}\rangle = \frac{1}{\sqrt{2}}(\vert {+z}\rangle + i\vert {-z}\rangle) = \vert {+y}\rangle$ $\checkmark$

#### $\theta/2$ の意味と $(\alpha, \beta)$ への接続

こうして、**空間的な方向の角度が $\theta$ のとき、状態ベクトルの係数には $\theta/2$ が入る**ことが分かった。これは偶然ではなく、スピン 1/2 の数学的構造から必然的に出てくる結果である（詳しくは [PHYSICS_NOTE4.md](PHYSICS_NOTE4.md) で扱う）。

ここで出発点に戻ろう。48行目で $\alpha = \cos(\theta/2)$, $\vert \beta\vert = \sin(\theta/2)$ と置いたが、いま固有状態の導出から $b = e^{i\phi}\sin(\theta/2)$ という形も得られた。これはまさに $\beta$ の完全な形を与えている——大きさが $\sin(\theta/2)$ で、位相が $e^{i\phi}$ である。つまり

```math
\alpha = \cos\frac{\theta}{2}, \qquad \beta = e^{i\phi}\sin\frac{\theta}{2}
```

ここで $\phi$ （ $0 \leq \phi < 2\pi$ ）は2成分の**相対位相**であり、$\theta$ と $\phi$ はそれぞれ方向 $\mathbf{n}$ の極角と方位角に対応する。

### 標準形

以上をまとめると、固有状態 $\vert {+n}\rangle$ の表式で方向 $\mathbf{n}$ を自由に動かせば任意の状態が得られるので、 $\vert {+n}\rangle$ を改めて $\vert \psi\rangle$ と書き直す。全体位相の自由度を除いた後、スピン 1/2 の一般の状態は

```math
\boxed{
\vert \psi\rangle = \cos\frac{\theta}{2}\vert {+z}\rangle + e^{i\phi}\sin\frac{\theta}{2}\vert {-z}\rangle
}
```

と、**2つの実数パラメータ $(\theta, \phi)$** だけで書ける。

- $\theta$ ： $0$ から $\pi$ の範囲（ $\vert {+z}\rangle$ 成分と $\vert {-z}\rangle$ 成分の割合を決める）
- $\phi$ ： $0$ から $2\pi$ の範囲（2成分の相対位相を決める）

---

## 第2段階：球面上の点との対応

### 2つの角度 → 球面上の1点

$(\theta, \phi)$ は、まさに球面の極座標（極角と方位角）と同じ形をしている。

- $\theta = 0$ ：北極
- $\theta = \pi$ ：南極
- $0 < \theta < \pi$ ：北極と南極の間のどこか
- $\phi$ ：赤道面内の方位

この対応をそのまま使って、スピン状態を単位球面上の1点として描いたものが**ブロッホ球**（Bloch sphere）である。

### ブロッホベクトル

球面上の点は、原点から球面への単位ベクトルで表せる。このベクトルを**ブロッホベクトル** $\mathbf{r}$ と呼ぶ。直交座標では

```math
\mathbf{r} = \begin{pmatrix} \sin\theta\cos\phi \\ \sin\theta\sin\phi \\ \cos\theta \end{pmatrix}
```

である。これは単位ベクトルなので $\vert \mathbf{r}\vert  = 1$ を満たす。

### 対応の表

| 状態 | $\theta$ | $\phi$ | ブロッホベクトル | 球面上の位置 |
|:---:|:---:|:---:|:---:|:---:|
| $\vert {+z}\rangle$ | $0$ | — | $(0, 0, 1)$ | 北極 |
| $\vert {-z}\rangle$ | $\pi$ | — | $(0, 0, -1)$ | 南極 |
| $\vert {+x}\rangle$ | $\pi/2$ | $0$ | $(1, 0, 0)$ | 赤道・ $x$ 方向 |
| $\vert {-x}\rangle$ | $\pi/2$ | $\pi$ | $(-1, 0, 0)$ | 赤道・ $-x$ 方向 |
| $\vert {+y}\rangle$ | $\pi/2$ | $\pi/2$ | $(0, 1, 0)$ | 赤道・ $y$ 方向 |
| $\vert {-y}\rangle$ | $\pi/2$ | $3\pi/2$ | $(0, -1, 0)$ | 赤道・ $-y$ 方向 |

### 検算

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で導いた固有状態と照合する。

$\vert {+x}\rangle$：標準形に $\theta = \pi/2$, $\phi = 0$ を代入すると

```math
\cos\frac{\pi/2}{2}\vert {+z}\rangle + e^{i \cdot 0}\sin\frac{\pi/2}{2}\vert {-z}\rangle
= \cos\frac{\pi}{4}\vert {+z}\rangle + \sin\frac{\pi}{4}\vert {-z}\rangle
= \frac{1}{\sqrt{2}}(\vert {+z}\rangle + \vert {-z}\rangle)
```

これは [PHYSICS_NOTE.md](PHYSICS_NOTE.md) の $\vert {+x}\rangle$ と一致する。 $\checkmark$

$\vert {+y}\rangle$：$\theta = \pi/2$, $\phi = \pi/2$ を代入すると

```math
\frac{1}{\sqrt{2}}(\vert {+z}\rangle + e^{i\pi/2}\vert {-z}\rangle)
= \frac{1}{\sqrt{2}}(\vert {+z}\rangle + i\vert {-z}\rangle)
```

これも [PHYSICS_NOTE.md](PHYSICS_NOTE.md) の $\vert {+y}\rangle$ と一致する。 $\checkmark$

$\vert {-x}\rangle$：$\theta = \pi/2$, $\phi = \pi$ を代入すると

```math
\frac{1}{\sqrt{2}}(\vert {+z}\rangle + e^{i\pi}\vert {-z}\rangle)
= \frac{1}{\sqrt{2}}(\vert {+z}\rangle - \vert {-z}\rangle)
```

一致する。 $\checkmark$

つまり、[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で「 $\phi = 0$ を $x$ 、 $\phi = \pi/2$ を $y$ と対応させた」という規約は、ブロッホ球の言葉では「赤道上の方位角がそのまま空間の方位角に対応する」ということだったのである。

---

## 第3段階：測定確率を球面上で読む

ここで視点を切り替える。第1段階では、任意の方向のスピン固有状態 $\vert {+n}\rangle$ を改めて $\vert \psi\rangle$ と書いた。次に問いたいのは、「この状態に対して、**$\vert \psi\rangle$ とは独立の別の方向 $\mathbf{n}$** のスピン測定を行ったら、結果はどうなるか」である。 $\mathbf{n}$ は測定装置の向きであり、状態 $\vert \psi\rangle$ とは無関係に自由に選べる。

2つの方向を区別するために、以降では $\vert \psi\rangle$ の角度を $(\theta_r, \phi_r)$、測定方向 $\vert {+n}\rangle$ の角度を $(\theta_n, \phi_n)$ と書く。

### Born 則の復習

状態 $\vert \psi\rangle$ に対して、方向 $\mathbf{n}$ のスピン測定で $+1$ が出る確率は

```math
P(+\mathbf{n}) = \vert \langle{+n}\vert \psi\rangle\vert ^2
```

である。

### 内積の計算

$\vert \psi\rangle$ のブロッホベクトルを $\mathbf{r}$ 、方向 $\mathbf{n}$ のブロッホベクトルを $\mathbf{n}$ とする（ $\vert {+n}\rangle$ は北極が $\mathbf{n}$ のブロッホ球の北極に対応する状態）。

$\vert \psi\rangle$ と $\vert {+n}\rangle$ をそれぞれ標準形で書くと

```math
\vert \psi\rangle = \cos\frac{\theta_r}{2}\vert {+z}\rangle + e^{i\phi_r}\sin\frac{\theta_r}{2}\vert {-z}\rangle
```

```math
\vert {+n}\rangle = \cos\frac{\theta_n}{2}\vert {+z}\rangle + e^{i\phi_n}\sin\frac{\theta_n}{2}\vert {-z}\rangle
```

内積を計算すると

```math
\langle{+n}\vert \psi\rangle = \cos\frac{\theta_n}{2}\cos\frac{\theta_r}{2} + e^{i(\phi_r - \phi_n)}\sin\frac{\theta_n}{2}\sin\frac{\theta_r}{2}
```

この絶対値の二乗を取る。 $\Delta\phi = \phi_r - \phi_n$ とおき、見通しをよくするために

```math
A = \cos\frac{\theta_n}{2}\cos\frac{\theta_r}{2}, \qquad
B = \sin\frac{\theta_n}{2}\sin\frac{\theta_r}{2}
```

と略記すると、内積は $\langle{+n}\vert \psi\rangle = A + e^{i\Delta\phi}B$ である。その絶対値の二乗は

```math
\vert A + e^{i\Delta\phi}B\vert ^2
= (A + e^{i\Delta\phi}B)(A + e^{-i\Delta\phi}B)
```

$A, B$ は実数なので $A^* = A$, $B^* = B$ であり、展開すると

```math
= A^2 + AB\,e^{-i\Delta\phi} + AB\,e^{i\Delta\phi} + B^2
= A^2 + B^2 + AB(e^{i\Delta\phi} + e^{-i\Delta\phi})
```

ここでオイラーの公式から $e^{i\Delta\phi} + e^{-i\Delta\phi} = 2\cos\Delta\phi$ なので

```math
= A^2 + B^2 + 2AB\cos\Delta\phi
```

$A, B$ を元に戻すと

```math
\vert \langle{+n}\vert \psi\rangle\vert ^2
= \cos^2\frac{\theta_n}{2}\cos^2\frac{\theta_r}{2} + \sin^2\frac{\theta_n}{2}\sin^2\frac{\theta_r}{2} + 2\cos\frac{\theta_n}{2}\cos\frac{\theta_r}{2}\sin\frac{\theta_n}{2}\sin\frac{\theta_r}{2}\cos\Delta\phi
```

### ブロッホベクトルの内積

一方、2つのブロッホベクトル $\mathbf{r}$ と $\mathbf{n}$ の内積は

```math
\mathbf{r}\cdot\mathbf{n} = \sin\theta_r\sin\theta_n\cos\Delta\phi + \cos\theta_r\cos\theta_n
```

である。ブロッホベクトルの間の角度を $\Theta$ とすると $\mathbf{r}\cdot\mathbf{n} = \cos\Theta$ なので

```math
\cos\Theta = \sin\theta_r\sin\theta_n\cos\Delta\phi + \cos\theta_r\cos\theta_n
```

### 2つの式を結びつける

半角の公式 $\cos^2(x/2) = (1 + \cos x)/2$ と $\sin^2(x/2) = (1 - \cos x)/2$ を使い、 $\sin\theta = 2\sin(\theta/2)\cos(\theta/2)$ を使って上の Born 則の式を整理すると

```math
\vert \langle{+n}\vert \psi\rangle\vert ^2 = \frac{1 + \cos\Theta}{2} = \cos^2\frac{\Theta}{2}
```

が得られる。ここで $\Theta$ はブロッホ球上の2点の間の角度（中心角）である。

### 確率の公式

```math
\boxed{
P(+\mathbf{n}) = \cos^2\frac{\Theta}{2}
}
```

```math
P(-\mathbf{n}) = 1 - \cos^2\frac{\Theta}{2} = \sin^2\frac{\Theta}{2}
```

つまり、**測定確率はブロッホ球上の角度 $\Theta$ だけで決まる**。この公式は [PHYSICS_NOTE.md](PHYSICS_NOTE.md) の Chapter 2 で登場した Born 則の確率と同じ形である。ブロッホ球の上では、2つの状態がどれだけ近いか（角度が小さいか）で測定結果の確率が決まる。

### 具体例で確認

$\vert {+z}\rangle$ の状態で $x$ 方向を測る。ブロッホ球上で北極 $(0,0,1)$ と赤道上 $(1,0,0)$ の角度は $\Theta = \pi/2$ なので

```math
P(+x) = \cos^2\frac{\pi}{4} = \frac{1}{2}
```

半々。[PHYSICS_NOTE.md](PHYSICS_NOTE.md) の実験事実と一致する。 $\checkmark$

$\vert {+z}\rangle$ の状態で $z$ 方向を測る。同じ点なので $\Theta = 0$。

```math
P(+z) = \cos^2 0 = 1
```

確定。再現性と一致する。 $\checkmark$

---

## 第4段階：直交状態と対蹠点

### 対蹠点の性質

ブロッホ球上で正反対の点（対蹠点）は $\Theta = \pi$ である。確率の公式に代入すると

```math
P = \cos^2\frac{\pi}{2} = 0
```

つまり、対蹠点にある状態への遷移確率はゼロである。これはまさに**直交**の条件 $\langle\phi\vert \psi\rangle = 0$ に対応する。

### 直交状態 = 対蹠点

ブロッホ球上で対蹠点にある2つの状態は直交する。逆も成り立つ。この対応を表にまとめると

| 状態のペア | 球面上の関係 | 角度 $\Theta$ | 内積 |
|:---:|:---:|:---:|:---:|
| $\vert {+z}\rangle$ と $\vert {-z}\rangle$ | 北極と南極 | $\pi$ | $0$ |
| $\vert {+x}\rangle$ と $\vert {-x}\rangle$ | $+x$ と $-x$ | $\pi$ | $0$ |
| $\vert {+y}\rangle$ と $\vert {-y}\rangle$ | $+y$ と $-y$ | $\pi$ | $0$ |

2次元ヒルベルト空間では、ある状態に直交する物理状態は全体位相を除いて一つに決まる。一方、ブロッホ球ではその直交状態が対蹠点として表される。この「2次元の直交が3次元の反対方向に対応する」のは、状態ベクトルの係数に $\theta/2$ が入ることの帰結である。

### ブロッホ球が伝えていること

ブロッホ球を一言でまとめれば、こうである。

> スピン 1/2 の物理状態は単位球面上の1点に対応し、2つの状態の区別しやすさは球面上の距離（角度）で測れる。

具体的には

- **同じ点**（ $\Theta = 0$ ）：同じ状態、測定確率 $1$
- **対蹠点**（ $\Theta = \pi$ ）：直交状態、測定確率 $0$
- **90度離れた点**（ $\Theta = \pi/2$ ）：半々の確率

この球面の上で回転を考えること——つまり「ブロッホベクトルがどう動くか」——が次の文書の主題になる。

---

## まとめ

| 概念 | ブロッホ球での表現 |
|:---|:---|
| 一般のスピン状態 | 球面上の1点 $(\theta, \phi)$ |
| $z$ 方向の固有状態 $\vert {\pm z}\rangle$ | 北極・南極 |
| 赤道上の状態 | $z$ 測定で半々になる状態（ $x$, $y$ 固有状態など） |
| 直交する状態 | 対蹠点（正反対の点） |
| 測定確率 | $\cos^2(\Theta/2)$ （ $\Theta$ = ブロッホ球上の角度） |
| 全体位相 $e^{i\gamma}$ | ブロッホ球上では見えない（同じ点に対応） |

---

## 全体の論理構造（振り返り）

```
一般の状態: α|+z⟩ + β|−z⟩ （複素数2つ）
    ↓
全体位相を除く → 実数パラメータ2つ (θ, φ) に減る
    ↓
(θ, φ) は球面の極座標 → ブロッホ球
    ↓
PHYSICS_NOTE.md の固有状態が球面上の自然な位置に乗る
    ↓
Born 則 → 測定確率 = cos²(Θ/2)　← 球面上の角度だけで決まる
    ↓
直交 = 対蹠点、同一 = 同じ点
```

ブロッホ球はスピン 1/2 の物理を幾何学に翻訳する辞書である。次の文書では、この球面上で回転がどう作用するかを見ていく。

---

**次の文書**: [PHYSICS_NOTE4.md — スピン 1/2 の回転演算子になぜ θ/2 が現れるのか](PHYSICS_NOTE4.md) では、ブロッホ球の上で回転演算子がどう働くかを具体的に計算し、スピノルとブロッホベクトルの二重構造を明らかにする。
