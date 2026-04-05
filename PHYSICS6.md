# PHYSICS6: 空間回転の行列とスピン回転の行列はどう違うか

## 目的

この文書は、Alice の黒い球をスピン `1/2` の模型として読むとき、

- 古典物理での空間回転はどんな行列で書かれるのか
- スピン `1/2` の回転はどんな行列で書かれるのか
- その二つは何が同じで、何が違うのか

を整理するためのメモである。

`PHYSICS5.md` では、

- ブロッホベクトルは空間回転に対して古典ベクトルのように回る
- しかし状態ベクトル（スピノル）は半角で変換される

という点を確認した。  
ここではその内容を、行列を並べてはっきり比較する。

---

## 結論

先に要点だけ書く。

1. 古典物理での空間回転は、3 次元ベクトルに作用する `3×3` の回転行列で表される  
2. スピン `1/2` の回転は、2 成分状態ベクトルに作用する `2×2` のユニタリ行列で表される  
3. 古典回転行列には回転角 $\theta$ がそのまま入る  
4. スピン回転行列には $\theta/2$ が入る  
5. それでも、スピン状態から作られるブロッホベクトルは、結果として古典ベクトルと同じ角度 $\theta$ だけ回る

したがって、

**空間回転の行列とスピン回転の行列は同じものではない。**  
**しかし後者は前者を量子状態の側から実現しており、ブロッホベクトルのレベルでは同じ回転として見える。**

---

## 1. 古典物理での空間回転

まず、古典物理でベクトル

```math
\mathbf r=
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
```
を回すことを考える。

たとえば `z` 軸まわりに角度 $\theta$ だけ回す回転は、

```math
R_z(\theta)=
\begin{pmatrix}
\cos\theta & -\sin\theta & 0\\
\sin\theta & \cos\theta & 0\\
0 & 0 & 1
\end{pmatrix}
```
で表される。

この行列を掛けると、

```math
\mathbf r' = R_z(\theta)\mathbf r
```
であり、具体的には

```math
\begin{pmatrix}
x'\\
y'\\
z'
\end{pmatrix}
=
\begin{pmatrix}
\cos\theta & -\sin\theta & 0\\
\sin\theta & \cos\theta & 0\\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
```
となる。

つまり

```math
x'=x\cos\theta-y\sin\theta,\qquad
y'=x\sin\theta+y\cos\theta,\qquad
z'=z
```
である。

これは、`xy` 平面の中で普通に角度 $\theta$ だけ回していることを意味する。

同様に、`x` 軸まわりや `y` 軸まわりの回転もそれぞれ

```math
R_x(\theta)=
\begin{pmatrix}
1 & 0 & 0\\
0 & \cos\theta & -\sin\theta\\
0 & \sin\theta & \cos\theta
\end{pmatrix},
\qquad
R_y(\theta)=
\begin{pmatrix}
\cos\theta & 0 & \sin\theta\\
0 & 1 & 0\\
-\sin\theta & 0 & \cos\theta
\end{pmatrix}
```
で与えられる。

## Physics Note 1: 古典回転行列の特徴

古典的な空間回転行列の特徴は次の通りである。

- `3×3` 行列である  
- 実行列である  
- ベクトルの長さを保つ  
- 回転角 $\theta$ がそのまま行列要素に入る

つまりこれは、3 次元空間のベクトルをそのまま回すための行列である。

---

## Physics Bridge: 古典角運動量はなぜ回転の生成子か

ここで、なぜ後で量子回転の式に角運動量が現れるのかを、古典側から一度見ておく。

古典力学では、位置と運動量から角運動量

```math
\mathbf L=\mathbf r\times \mathbf p
```
を作る。  
成分で書けば

```math
L_x=yp_z-zp_y,\qquad
L_y=zp_x-xp_z,\qquad
L_z=xp_y-yp_x
```
である。

たとえば `z` 軸まわりの微小回転 $\delta\phi$ を考える。  
古典回転行列は

```math
R_z(\delta\phi)=
\begin{pmatrix}
\cos\delta\phi & -\sin\delta\phi & 0\\
\sin\delta\phi & \cos\delta\phi & 0\\
0 & 0 & 1
\end{pmatrix}
```
である。  
微小角では

```math
\cos\delta\phi \approx 1,\qquad
\sin\delta\phi \approx \delta\phi
```
なので、

```math
R_z(\delta\phi)\approx
\begin{pmatrix}
1 & -\delta\phi & 0\\
\delta\phi & 1 & 0\\
0 & 0 & 1
\end{pmatrix}
```
となる。  
これを

```math
\mathbf r=
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
```
に作用させると、

```math
\mathbf r'=
R_z(\delta\phi)\mathbf r
\approx
\begin{pmatrix}
x-y\,\delta\phi\\
y+x\,\delta\phi\\
z
\end{pmatrix}
```
である。

したがって微小変化は

```math
\delta x=x'-x=-y\,\delta\phi,\qquad
\delta y=y'-y=x\,\delta\phi,\qquad
\delta z=0
```
となる。  
つまり `z` 軸まわりの回転では、`x` と `y` がこの形で混ざる。

古典力学では、ある量 $G$ が変換の生成子であるとは、「その微小変化が $G$ から作れる」という意味である。  
実際、ポアソン括弧を使うと

```math
\{f,g\}
=
\sum_i
\left(
\frac{\partial f}{\partial q_i}\frac{\partial g}{\partial p_i}
-\frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q_i}
\right)
```
と定義され、位相空間の中で「どの量がどの量を動かすか」を表す。  
ここで $q_i$ は座標、$p_i$ はそれに共役な運動量である。

古典力学では、微小な正準変換は

```math
\delta f = \varepsilon\,\{f,G\}
```
の形で書ける。  
つまり、ある量 $G$ が生成子であるとは、「どの物理量 $f$ の微小変化も、ポアソン括弧 $\{f,G\}$ から読める」ということである。

いま回転角を $\delta\phi$ とし、生成子候補を $L_z$ に取ると、

```math
\delta f = \delta\phi\,\{f,L_z\}
```
となる。  
では実際に `f=x,y,z` で計算してみよう。

まず

```math
L_z=xp_y-yp_x
```
なので、

```math
\{x,L_z\}
=
\frac{\partial x}{\partial x}\frac{\partial L_z}{\partial p_x}
-\frac{\partial x}{\partial p_x}\frac{\partial L_z}{\partial x}
=
1\cdot(-y)-0\cdot p_y
=-y
```
である。  
同様に

```math
\{y,L_z\}
=
\frac{\partial y}{\partial y}\frac{\partial L_z}{\partial p_y}
=x,
\qquad
\{z,L_z\}=0
```
となる。  
したがって

```math
\{x,L_z\}=-y,\qquad
\{y,L_z\}=x,\qquad
\{z,L_z\}=0
```
が確かに成り立つ。

これを微小変化の式へ戻すと

```math
\delta x=\delta\phi\,\{x,L_z\}=-y\,\delta\phi,\qquad
\delta y=\delta\phi\,\{y,L_z\}=x\,\delta\phi
```
となり、まさに `z` 軸まわりの回転そのものが出てくる。

この意味で、古典角運動量 $L_z$ は `z` 軸まわりの回転の生成子である。  
同様に $L_x,L_y$ はそれぞれ `x`,`y` 軸まわりの回転を生成する。

量子力学では、ポアソン括弧の役割を交換子が引き継ぐ。  
したがって、古典で回転の生成子だった角運動量は、量子でも回転の生成子として現れる。

この橋渡しがあるからこそ、量子回転を

```math
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
```
と書くのは自然なのである。

---

## 2. スピン `1/2` の回転行列

次に、スピン `1/2` の状態ベクトル

```math
|\psi\rangle=
\begin{pmatrix}
\alpha\\
\beta
\end{pmatrix}
```
を考える。  
これは 3 次元ベクトルではなく、2 成分の複素ベクトルである。

ここでいきなり回転行列の式を書くのではなく、まず「どんな条件を満たすべきか」を考える。

### 2-1. 回転行列に課したい条件

空間回転を量子状態に対応させるなら、少なくとも次の条件が必要である。

1. 角度 `0` の回転は何もしない  
2. 角度を続けて回したら、その効果は足し合わさる  
3. 確率が変わってはいけないので、状態のノルムを保つ

これを式で書けば、

```math
U(0)=I,\qquad
U(\theta_1)U(\theta_2)=U(\theta_1+\theta_2)
```
であり、さらに $U(\theta)$ はユニタリでなければならない。

その理由は、回転は「状態の見え方」を変えても、全確率そのものを変えてはいけないからである。  
量子状態の長さ

```math
\langle \psi|\psi\rangle
```
は全確率 1 に対応しているので、回転後も

```math
\langle \psi|\psi\rangle
=
\langle \psi|U(\theta)^\dagger U(\theta)|\psi\rangle
```
が元と同じ値を保たねばならない。  
これが任意の状態 $|\psi\rangle$ について成り立つためには

```math
U(\theta)^\dagger U(\theta)=I
```
でなければならない。  
これが「ユニタリである」という条件である。

このような「連続な1パラメータのユニタリ変換」は一般に

```math
U(\theta)=e^{-i\theta G}
```
という指数関数の形で書ける。  
ここで `G` はエルミートな生成子である。

なぜエルミートでなければならないかも、ユニタリ条件から分かる。  
実際、

```math
U(\theta)=e^{-i\theta G}
```
なら

```math
U(\theta)^\dagger=e^{+i\theta G^\dagger}
```
である。  
これが常に

```math
U(\theta)^\dagger U(\theta)=I
```
を満たすためには、少なくとも微小角 $\theta$ について一次の項が打ち消し合わねばならない。  
そこで

```math
U(\theta)\approx I-i\theta G,\qquad
U(\theta)^\dagger\approx I+i\theta G^\dagger
```
と展開すると、

```math
U(\theta)^\dagger U(\theta)
\approx
I+i\theta(G^\dagger-G)
```
となる。  
これが任意の微小角で恒等行列に等しいためには

```math
G^\dagger=G
```
でなければならない。  
これが `G` がエルミートである理由である。

したがって、スピン回転の本質的な問いは、

**「スピン `1/2` に対して、回転の生成子 `G` は何か」**

という問いに変わる。

### 2-2. 回転の生成子は角運動量である

ここで重要な一般原理を使う。  
量子力学では、空間回転を生成するのは角運動量である。

したがって、ある軸まわりに角度 $\theta$ だけ回す回転は、一般に

```math
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
```
と書かれる。  
ここで

```math
J_{\mathbf n}=\mathbf n\cdot\mathbf J
```
は、その方向の角運動量成分である。

これは古典力学で「回転の生成子が角運動量である」と言うのに対応する、量子版の主張である。

今扱っているのはスピン `1/2` なので、回転の生成子は軌道角運動量ではなくスピン演算子

```math
\mathbf S=(S_x,S_y,S_z)
```
になる。  
そして `PHYSICS2.md` で見たように、

```math
S_i=\frac{\hbar}{2}\sigma_i
\qquad (i=x,y,z)
```
である。

したがって、`z` 軸まわりの回転生成子は

```math
S_z=\frac{\hbar}{2}\sigma_z
```
であり、これを一般式へ代入すると

```math
U_z(\theta)
=
\exp\!\left(
-\frac{i}{\hbar}\theta S_z
\right)
=
\exp\!\left(
-i\frac{\theta}{2}\sigma_z
\right)
```
となる。

ここで `1/2` が出るのは、「そう置きたいから」ではない。  
スピン `1/2` の角運動量固有値が

```math
\pm\frac{\hbar}{2}
```
だからである。  
つまり半角は、スピン `1/2` であることそのものから出ている。

実験室固定の `z` 軸に対して

```math
|0\rangle = |+z\rangle,\qquad
|1\rangle = |-z\rangle
```
と置けば、これらは `S_z` の固有状態であり、

```math
S_z|0\rangle=+\frac{\hbar}{2}|0\rangle,\qquad
S_z|1\rangle=-\frac{\hbar}{2}|1\rangle
```
を満たす。  
したがって `z` 軸まわりの回転をかけると、

```math
U_z(\theta)|0\rangle=e^{-i\theta/2}|0\rangle,\qquad
U_z(\theta)|1\rangle=e^{+i\theta/2}|1\rangle
```
となる。

ここで初めて、

- `|0\rangle` と `|1\rangle` が反対向きの位相を受け取ること
- 半角 `\theta/2` が現れること

の両方が、スピン `1/2` の角運動量固有値から自然に理解できる。

### 2-3. 一般方向へ拡張する

同じ議論を `x`,`y`,`z` の各方向に対して行えば、回転の生成子はそれぞれ

```math
\frac{1}{\hbar}S_x=\frac12\sigma_x,\qquad
\frac{1}{\hbar}S_y=\frac12\sigma_y,\qquad
\frac{1}{\hbar}S_z=\frac12\sigma_z
```
である。  
したがって、単位ベクトル `\mathbf n=(n_x,n_y,n_z)` 方向の回転では

```math
J_{\mathbf n}=S_{\mathbf n}=\mathbf n\cdot\mathbf S
```
であり、

```math
S_{\mathbf n}
=
\frac{\hbar}{2}\,\mathbf n\cdot\boldsymbol{\sigma}
```
だから、

したがって、この状態に空間回転 `\theta` を作用させるとき、対応する行列は

```math
U(\theta,\mathbf n)
=
\exp\!\left(
-i\frac{\theta}{2}\,\mathbf n\cdot\boldsymbol{\sigma}
\right)
```
である。  
ここで

```math
\mathbf n\cdot\boldsymbol{\sigma}
=
n_x\sigma_x+n_y\sigma_y+n_z\sigma_z
```
であり、

```math
\sigma_x=
\begin{pmatrix}
0&1\\
1&0
\end{pmatrix},
\quad
\sigma_y=
\begin{pmatrix}
0&-i\\
i&0
\end{pmatrix},
\quad
\sigma_z=
\begin{pmatrix}
1&0\\
0&-1
\end{pmatrix}
```
である。

この式は「突然そう定義する」のではなく、

- 連続な回転である
- ノルムを保つ
- `z` 回転では `|0\rangle,|1\rangle` が混ざらない
- `x,y,z` の3方向を対等に扱う

という条件を満たす最小の 2 次元表現として出てくる。

たとえば `z` 軸まわりの回転なら、

```math
U_z(\theta)=
\exp\!\left(-i\frac{\theta}{2}\sigma_z\right)
```
となる。

`\sigma_z` は対角行列なので、指数関数もすぐ計算できて

```math
U_z(\theta)=
\begin{pmatrix}
e^{-i\theta/2} & 0\\
0 & e^{+i\theta/2}
\end{pmatrix}
```
である。

同様に

```math
U_x(\theta)=\exp\!\left(-i\frac{\theta}{2}\sigma_x\right),\qquad
U_y(\theta)=\exp\!\left(-i\frac{\theta}{2}\sigma_y\right)
```
が、それぞれ `x`,`y` 軸まわりのスピン回転を与える。

## Physics Note 2: スピン回転行列の特徴

スピン `1/2` の回転行列の特徴は次の通りである。

- `2×2` 行列である  
- 複素行列である  
- ユニタリである  
- 回転角として `\theta/2` が入る

つまりこれは、3 次元空間ベクトルを直接回す行列ではなく、**量子状態ベクトルを回す行列**である。

---

## 3. 何が違うのか

ここで古典回転とスピン回転の違いを並べる。

### 古典回転

- 対象は 3 次元ベクトル  
- 行列は `3×3`  
- 実直交行列  
- 回転角は $\theta$

### スピン回転

- 対象は 2 成分量子状態  
- 行列は `2×2`  
- 複素ユニタリ行列  
- 回転角は $\theta/2$

したがって、両者は見た目からして別物である。  
古典回転行列 `R` とスピン回転行列 `U` を「同じ行列だ」と思ってはいけない。

---

## 4. それでも、なぜ同じ回転に見えるのか

ここで大事なのがブロッホベクトルである。

状態 `|\psi\rangle` から

```math
\mathbf r=
(\langle \sigma_x\rangle,\langle \sigma_y\rangle,\langle \sigma_z\rangle)
```
を作ると、この `\mathbf r` は 3 次元ベクトルとして振る舞う。

そして状態にスピン回転

```math
|\psi\rangle \to U(\theta,\mathbf n)|\psi\rangle
```
を作用させると、対応するブロッホベクトルは

```math
\mathbf r \to R(\theta,\mathbf n)\mathbf r
```
と、古典回転行列によって回る。

つまり、

- スピノルには半角が入る
- しかしブロッホベクトルは全角で回る

のである。

ここが `PHYSICS5.md` で見た「二層構造」である。

---

## 5. 360° 回転と 720° 回転

この違いが最も印象的に現れるのが、360° 回転である。

古典ベクトルなら、360° 回せば元に戻る。  
ブロッホベクトルも、360° 回せば元に戻る。

しかしスピン `1/2` の状態ベクトルは

```math
U(2\pi,\mathbf n)=
\exp(-i\pi\,\mathbf n\cdot\boldsymbol{\sigma})
=-I
```
となるので、

```math
|\psi\rangle \to -|\psi\rangle
```
である。

つまり 360° では、状態ベクトルそのものはまだ本当に元へ戻っていない。  
720° 回して初めて

```math
U(4\pi,\mathbf n)=I
```
となり、状態ベクトルも完全に元へ戻る。

ただし `|\psi\rangle` と `-|\psi\rangle` は全体位相の違いであり、単独の測定統計は同じである。  
そのため、観測だけ見ていると 360° と 720° の違いは見えにくい。

---

## 6. Alice の黒い球に戻すと

Alice の黒い球をスピン模型として読むなら、

- 球を古典的に回す  
  -> スピン状態にも対応する回転が作用する

と読むべきである。

たとえば縦に 180° 回せば、ブロッホ球の北極 `|0\rangle` は南極 `|1\rangle` に移る。  
そのあとで実験室固定の `z` 軸を測れば、結果は `Oops!` である。

一方、球に貼りついた軸ごと一緒に読み直すなら、相対関係は保たれるので同じ結果になる。  
ここでも本質は、絶対方向ではなく状態と測定軸の相対関係である。

---

## 最後に一行で言うと

古典空間回転の行列 `R` とスピン回転の行列 `U` は別物だが、後者は量子状態を回すことで、ブロッホベクトルのレベルでは前者と同じ回転を実現している。
