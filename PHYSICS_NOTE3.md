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

ここで $\theta$ ではなく $\theta/2$ を使うのはなぜか。もちろん $\cos\eta$, $\sin\eta$ と置いて $\eta = \theta/2$ としても同じだが、 $\theta$ と書く理由がある。

[PHYSICS_NOTE.md](PHYSICS_NOTE.md) で見たように、方向 $\mathbf{n}$（ $z$ 軸から角度 $\theta$ ）の固有状態は

```math
\vert {+n}\rangle = \cos\frac{\theta}{2}\vert {+z}\rangle + e^{i\phi}\sin\frac{\theta}{2}\vert {-z}\rangle
```

の形をしていた。つまり**空間的な角度 $\theta$ に対して、状態ベクトルの係数には $\theta/2$ が入る**。この対応を保つために、パラメータを $\theta/2$ で書くのが自然である。こうすると、後で見るように、球面上の角度 $\theta$ がそのまま空間的な方向の角度に一致する。

### $\beta$ の位相

$\vert \beta\vert  = \sin(\theta/2)$ が決まったので、 $\beta$ は

```math
\beta = e^{i\phi}\sin\frac{\theta}{2}
```

と書ける。 $\phi$ （ $0 \leq \phi < 2\pi$ ）は $\beta$ の位相、すなわち2成分の**相対位相**である。

### 標準形

以上をまとめると、全体位相の自由度を除いた後、スピン 1/2 の一般の状態は

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

この絶対値の二乗を取る。 $\Delta\phi = \phi_r - \phi_n$ とおくと

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
P(+x) = \cos^2\frac{\pi/4}{} = \frac{1}{2}
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

2次元ヒルベルト空間では直交するベクトルは2つしかないが、3次元の実空間では正反対の2方向は1本の直線を成す。この「2次元の直交が3次元の反対方向に対応する」のは、状態ベクトルの係数に $\theta/2$ が入ることの帰結である。

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
