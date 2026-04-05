# PHYSICS8: ポアソン括弧を具体例で理解する

## 目的

この文書は、ポアソン括弧

$$
\{f,g\}
$$

が何をしている記号なのかを、一般論よりも**具体例**を通して理解するためのメモである。

とくに知りたいのは次の点である。

- ポアソン括弧は何を計算しているのか
- どうして「変換の生成子」という話が出てくるのか
- 角運動量がなぜ回転の生成子になるのか

ここではできるだけ、抽象的な一般論を先に置かない。  
まず具体例を見て、あとから意味を整理する。

---

## 結論

先に短く言うと、

**ポアソン括弧は、「ある量が、別の量によってどう微小に変化するか」を教える道具である。**

たとえば角運動量 $L_z$ とポアソン括弧を取ると、

- `x` は `-y` 方向へ少し動く
- `y` は `+x` 方向へ少し動く

という形が出てきて、これはまさに `z` 軸まわりの回転そのものである。  
この意味で、角運動量は回転の生成子である。

---

## 1. まずは一番具体的な設定

3 次元空間を動く粒子を考える。  
位置を

$$
\mathbf r=(x,y,z)
$$

運動量を

$$
\mathbf p=(p_x,p_y,p_z)
$$

で表す。

古典力学では、位置と運動量を合わせた

$$
(x,y,z,p_x,p_y,p_z)
$$

が状態を指定する。  
この空間を位相空間と呼ぶ。

ここで、位置や運動量から作られる任意の量

$$
f(x,y,z,p_x,p_y,p_z)
$$

を考える。

---

## 2. ポアソン括弧の定義

ポアソン括弧は、二つの量 `f,g` から新しい量を作る演算で、

$$
\{f,g\}
=
\sum_i
\left(
\frac{\partial f}{\partial q_i}\frac{\partial g}{\partial p_i}
-\frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q_i}
\right)
$$

と定義される。  
ここで

$$
(q_1,q_2,q_3)=(x,y,z),\qquad
(p_1,p_2,p_3)=(p_x,p_y,p_z)
$$

である。

見た目は少し重いが、やっていることは

- `f` が座標にどう依るか
- `g` が運動量にどう依るか

を掛け合わせ、

- `f` が運動量にどう依るか
- `g` が座標にどう依るか

の項を引いているだけである。

まだ意味は分からなくてもよい。  
まずは実際に計算してみる。

---

## 3. いちばん簡単な例

まず

$$
\{x,p_x\}
$$

を計算する。

定義から

$$
\{x,p_x\}
=
\frac{\partial x}{\partial x}\frac{\partial p_x}{\partial p_x}
-\frac{\partial x}{\partial p_x}\frac{\partial p_x}{\partial x}
=1\cdot1-0\cdot0=1
$$

である。

同様に

$$
\{x,p_y\}=0,\qquad
\{y,p_x\}=0
$$

である。

つまりポアソン括弧は、

- `x` と $p_x$
- `y` と $p_y$
- `z` と $p_z$

のような対応する組に対して特別な役割を持っている。

これは量子力学での交換関係

$$
[x,p_x]=i\hbar
$$

に対応する古典版だと思ってよい。

---

## 4. 「生成子」とは何か

ここでポアソン括弧の意味を言う。

古典力学では、ある量 `G` が変換の生成子であるとは、

$$
\delta f=\varepsilon\,\{f,G\}
$$

によって、任意の量 `f` の微小変化が決まるということである。  
$\varepsilon$ は小さなパラメータである。

つまり `G` が分かれば、

- `x` がどう動くか
- `y` がどう動くか
- $p_x$ がどう動くか
- $p_y$ がどう動くか

などが、一斉に読める。

とくに位置ベクトル

$$
\mathbf r=(x,y,z)
$$

に対しては、成分ごとに

$$
\delta x=\varepsilon\{x,G\},\qquad
\delta y=\varepsilon\{y,G\},\qquad
\delta z=\varepsilon\{z,G\}
$$

なので、まとめて

$$
\delta\mathbf r=\varepsilon\,\{\mathbf r,G\}
$$

と書いてよい。

この意味で `G` は「変換を作るもの」、すなわち生成子である。

---

## 5. 具体例: $L_z$ が回転を作る

ここで角運動量の `z` 成分

$$
L_z=xp_y-yp_x
$$

を考える。

これが本当に `z` 軸まわりの回転を生成するかを見よう。

### `x` はどう変わるか

$$
\{x,L_z\}
=
\frac{\partial x}{\partial x}\frac{\partial L_z}{\partial p_x}
-\frac{\partial x}{\partial p_x}\frac{\partial L_z}{\partial x}
=
1\cdot(-y)-0\cdot p_y
=-y
$$

したがって

$$
\delta x=\delta\phi\,\{x,L_z\}=-y\,\delta\phi
$$

である。

### `y` はどう変わるか

$$
\{y,L_z\}
=
\frac{\partial y}{\partial y}\frac{\partial L_z}{\partial p_y}
=
1\cdot x
=x
$$

したがって

$$
\delta y=\delta\phi\,\{y,L_z\}=x\,\delta\phi
$$

である。

### `z` はどう変わるか

$$
\{z,L_z\}=0
$$

なので

$$
\delta z=0
$$

である。

まとめると、

$$
\delta x=-y\,\delta\phi,\qquad
\delta y=x\,\delta\phi,\qquad
\delta z=0
$$

となる。

これはまさに、`z` 軸まわりの微小回転そのものである。

したがって

**$L_z$ は `z` 軸まわりの回転の生成子である。**

---

## 6. なぜ「回転そのもの」だと言えるのか

微小な `z` 軸回転の回転行列は

$$
R_z(\delta\phi)\approx
\begin{pmatrix}
1 & -\delta\phi & 0\\
\delta\phi & 1 & 0\\
0 & 0 & 1
\end{pmatrix}
$$

である。

これを

$$
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
$$

に作用させると

$$
\begin{pmatrix}
x-y\,\delta\phi\\
y+x\,\delta\phi\\
z
\end{pmatrix}
$$

になる。  
したがって

$$
\delta x=-y\,\delta\phi,\qquad
\delta y=x\,\delta\phi,\qquad
\delta z=0
$$

であり、これはポアソン括弧から得た結果と完全に一致する。

だから $L_z$ は、単に何か立派そうな保存量なのではなく、**実際に回転を生み出している量** だと分かる。

ただし、ここで読者は自然にこう思うはずである。

- `z` 軸ではうまくいった
- では `x` 軸や `y` 軸でも本当に同じことが起きるのか

この確認もしておこう。

### `x` 軸まわり

`x` 軸方向の角運動量は

$$
L_x=yp_z-zp_y
$$

である。

このとき

$$
\{x,L_x\}=0
$$

であり、さらに

$$
\{y,L_x\}
=
\frac{\partial y}{\partial y}\frac{\partial L_x}{\partial p_y}
=
1\cdot(-z)
=-z
$$

$$
\{z,L_x\}
=
\frac{\partial z}{\partial z}\frac{\partial L_x}{\partial p_z}
=
1\cdot y
=y
$$

だから

$$
\delta x=0,\qquad
\delta y=-z\,\delta\phi,\qquad
\delta z=y\,\delta\phi
$$

となる。

これは微小回転行列

$$
R_x(\delta\phi)\approx
\begin{pmatrix}
1 & 0 & 0\\
0 & 1 & -\delta\phi\\
0 & \delta\phi & 1
\end{pmatrix}
$$

が与える変化と一致している。

### `y` 軸まわり

`y` 軸方向の角運動量は

$$
L_y=zp_x-xp_z
$$

である。

このとき

$$
\{y,L_y\}=0
$$

であり、さらに

$$
\{x,L_y\}
=
\frac{\partial x}{\partial x}\frac{\partial L_y}{\partial p_x}
=
1\cdot z
=z
$$

$$
\{z,L_y\}
=
\frac{\partial z}{\partial z}\frac{\partial L_y}{\partial p_z}
=
1\cdot(-x)
=-x
$$

だから

$$
\delta x=z\,\delta\phi,\qquad
\delta y=0,\qquad
\delta z=-x\,\delta\phi
$$

となる。

これは微小回転行列

$$
R_y(\delta\phi)\approx
\begin{pmatrix}
1 & 0 & \delta\phi\\
0 & 1 & 0\\
-\delta\phi & 0 & 1
\end{pmatrix}
$$

が与える変化と一致している。

### 3 軸そろえて見ると

ここまでを並べると、

$$
L_x \Rightarrow
\begin{cases}
\delta x=0\\
\delta y=-z\,\delta\phi\\
\delta z=y\,\delta\phi
\end{cases}
$$

$$
L_y \Rightarrow
\begin{cases}
\delta x=z\,\delta\phi\\
\delta y=0\\
\delta z=-x\,\delta\phi
\end{cases}
$$

$$
L_z \Rightarrow
\begin{cases}
\delta x=-y\,\delta\phi\\
\delta y=x\,\delta\phi\\
\delta z=0
\end{cases}
$$

となっていて、各成分がそれぞれ対応する軸まわりの微小回転をきちんと生み出していることが分かる。

したがって、角運動量は `z` 軸だけで偶然うまくいったのではなく、**3 次元空間の回転そのものの生成子** なのである。

### 一般の軸 $\mathbf n$ へどう拡張するか

ここで次の疑問が出てくる。

- `x`,`y`,`z` 軸まわりでは分かった
- では、斜めを向いた一般の軸 $\mathbf n$ まわりでは何が生成子になるのか

この点で大事なのは、微小回転は角度について一次で効くということである。  
したがって、一般軸まわりの微小回転は、各軸まわりの微小回転の**線形結合**として書けるはずである。

軸 $\mathbf n$ を

$$
\mathbf n=(n_x,n_y,n_z),\qquad |\mathbf n|=1
$$

とすると、その方向の角運動量成分

$$
L_{\mathbf n}=n_xL_x+n_yL_y+n_zL_z
$$

を考えるのが自然である。  
これはベクトルの内積を使えば

$$
L_{\mathbf n}=\mathbf n\cdot\mathbf L
$$

である。

すると、位置ベクトルの微小変化は

$$
\delta\mathbf r
=
\delta\theta\,\{\mathbf r,L_{\mathbf n}\}
=
\delta\theta\,\{\mathbf r,n_xL_x+n_yL_y+n_zL_z\}
$$

となる。

ポアソン括弧は第 2 引数について線形なので、

$$
\delta\mathbf r
=
\delta\theta\left(
n_x\{\mathbf r,L_x\}
+
n_y\{\mathbf r,L_y\}
+
n_z\{\mathbf r,L_z\}
\right)
$$

と分解できる。

つまり、一般軸まわりの微小回転は

- `x` 軸まわりの回転
- `y` 軸まわりの回転
- `z` 軸まわりの回転

を、その軸の成分 $n_x,n_y,n_z$ で重ね合わせたものになっている。

これが

$$
L_{\mathbf n}=\mathbf n\cdot\mathbf L
$$

という式の意味である。  
いきなりこの形を思いつくのではなく、**3 軸の結果をまとめて、一般軸へ線形に拡張したもの** だと見ると自然である。

したがって、一般軸 $\mathbf n$ まわりの回転に対しては

$$
\delta\mathbf r
=
\delta\theta\,\{\mathbf r,\mathbf n\cdot\mathbf L\}
$$

と書けばよい。

---

## 7. 量子力学への橋渡し

量子力学では、ポアソン括弧の役割を交換子が引き継ぐ。

ざっくり言えば

$$
\{f,g\}
\quad\longleftrightarrow\quad
\frac{1}{i\hbar}[F,G]
$$

という対応がある。

ここで大事なのは、「生成子」という言葉の意味が古典と量子でよく似ていることである。

古典では

$$
\delta f=\varepsilon\,\{f,G\}
$$

という形で、量 `G` が微小変換を作った。  
量子でも同様に、ある演算子 `G` が微小変換を作るなら、状態は

$$
|\psi\rangle \longrightarrow
\left(
I-\frac{i}{\hbar}\varepsilon G
\right)|\psi\rangle
$$

のように変わると考えるのが自然である。

ここで

- `I` は何もしない演算子
- $\varepsilon$ は微小な角度
- `G` が変換の向きを決める生成子

である。

古典で角運動量が回転の生成子だったのなら、量子でも回転の生成子は角運動量演算子 `J` であるべきだ、というのが自然な対応である。

したがって、軸 $\mathbf n$ まわりの微小回転は

$$
U(\delta\theta,\mathbf n)
\approx
I-\frac{i}{\hbar}\,\delta\theta\,J_{\mathbf n}
$$

と書けるはずである。  
ここで

$$
J_{\mathbf n}=\mathbf n\cdot\mathbf J
$$

は、その軸方向の角運動量成分である。

次に、この微小回転を何回も積み重ねて有限回転を作る。  
角度 $\theta$ を `N` 個に分けて

$$
\delta\theta=\frac{\theta}{N}
$$

とすると、

$$
U(\theta,\mathbf n)
=
\left[
U\!\left(\frac{\theta}{N},\mathbf n\right)
\right]^N
\approx
\left(
I-\frac{i}{\hbar}\frac{\theta}{N}J_{\mathbf n}
\right)^N
$$

となる。

そして $N\to\infty$ の極限を取ると、これは指数関数になって

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
$$

となる。

つまり、ここで指数関数が出てくるのは「何となく便利だから」ではない。  
**微小回転を何回も重ねて有限回転を作ると、指数関数の形が自然に現れる** のである。

したがって、古典で回転の生成子だった角運動量は、量子でも回転の生成子になる。  
この意味で量子回転演算子は

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
$$

となるのである。

---

## 最後に一行で言うと

ポアソン括弧は「ある量が別の量によってどう微小に変化するか」を教える道具であり、角運動量とのポアソン括弧がちょうど回転の微小変化を与えるので、角運動量は回転の生成子になる。
