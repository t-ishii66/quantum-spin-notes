# ブロッホ球の物理学的に正確な説明

## 目的

この文書は、物語本文とは独立に、2準位量子系の**純粋状態**に対する
ブロッホ球を物理学的に正しく整理するための補助資料である。

## 1. 何を表しているのか

ブロッホ球は、**1量子ビット**あるいは一般に**2準位系**の状態を幾何学的に表す方法である。

基底を

$$
|0\rangle,\quad |1\rangle
$$

とする。純粋状態は一般に

$$
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle,\qquad
\alpha,\beta\in\mathbb{C},\qquad
|\alpha|^2+|\beta|^2=1
$$

と書ける。

ただし物理的に意味があるのはベクトルそのものではなく、全体位相

$$
|\psi\rangle \sim e^{i\gamma}|\psi\rangle
$$

まで同一視した状態である。したがって、正規化された複素2成分ベクトルの自由度は
最終的に実数2個になり、これを球面上の2つの角度で表せる。

## 2. 純粋状態の標準形

全体位相を除くと、任意の純粋状態は

$$
|\psi\rangle=
\cos\frac{\theta}{2}|0\rangle
+e^{i\phi}\sin\frac{\theta}{2}|1\rangle
$$

と書ける。ここで

$$
0\le \theta \le \pi,\qquad 0\le \phi < 2\pi
$$

である。

このときブロッホベクトルは

$$
\mathbf{r}=(x,y,z)
=
(\sin\theta\cos\phi,\ \sin\theta\sin\phi,\ \cos\theta)
$$

で与えられ、長さは

$$
|\mathbf{r}|=1
$$

となる。つまり**純粋状態は球面上の点**に対応する。

注意:
- $\theta=0,\pi$ では北極・南極に対応し、このとき $\phi$ は物理的に意味を持たない。
- $\phi$ は全体位相ではなく、基底成分の**相対位相**である。

## 3. パウリ行列とブロッホベクトル

ブロッホ球で現れる3つの座標は、パウリ行列の期待値として読むと分かりやすい。
ここで

$$
\boldsymbol{\sigma}=(\sigma_x,\sigma_y,\sigma_z)
$$

はパウリ行列で、

$$
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
$$

である。

純粋状態 $|\psi\rangle$ に対して、ブロッホベクトル $\mathbf{r}$ の成分は

$$
r_i=\langle\psi|\sigma_i|\psi\rangle
\qquad (i=x,y,z)
$$

で与えられる。これは各パウリ演算子の期待値そのものである。

これを成分ごとに確かめてみる。純粋状態を

$$
|\psi\rangle=
\cos\frac{\theta}{2}|0\rangle
+e^{i\phi}\sin\frac{\theta}{2}|1\rangle
$$

とし、列ベクトルで

$$
|\psi\rangle=
\begin{pmatrix}
\cos\frac{\theta}{2}\\
e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix},
\qquad
\langle\psi|=
\begin{pmatrix}
\cos\frac{\theta}{2} &
e^{-i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
$$

と書く。

まず $x$ 成分は

$$
r_x=\langle\psi|\sigma_x|\psi\rangle
$$

である。$\sigma_x$ は上下の成分を入れ替えるので

$$
\sigma_x|\psi\rangle
=
\begin{pmatrix}
0&1\\
1&0
\end{pmatrix}
\begin{pmatrix}
\cos\frac{\theta}{2}\\
e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
=
\begin{pmatrix}
e^{i\phi}\sin\frac{\theta}{2}\\
\cos\frac{\theta}{2}
\end{pmatrix}
$$

したがって

$$
\begin{aligned}
r_x
&=
\begin{pmatrix}
\cos\frac{\theta}{2} &
e^{-i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
\begin{pmatrix}
e^{i\phi}\sin\frac{\theta}{2}\\
\cos\frac{\theta}{2}
\end{pmatrix} \\
&=
e^{i\phi}\cos\frac{\theta}{2}\sin\frac{\theta}{2}
+e^{-i\phi}\sin\frac{\theta}{2}\cos\frac{\theta}{2} \\
&=
\left(e^{i\phi}+e^{-i\phi}\right)\cos\frac{\theta}{2}\sin\frac{\theta}{2} \\
&=
2\cos\phi\cos\frac{\theta}{2}\sin\frac{\theta}{2} \\
&=
\sin\theta\cos\phi
\end{aligned}
$$

となる。

次に $y$ 成分は

$$
r_y=\langle\psi|\sigma_y|\psi\rangle
$$

である。$\sigma_y$ は成分を入れ替えると同時に位相因子 $\pm i$ を付けるので

$$
\sigma_y|\psi\rangle
=
\begin{pmatrix}
0&-i\\
i&0
\end{pmatrix}
\begin{pmatrix}
\cos\frac{\theta}{2}\\
e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
=
\begin{pmatrix}
-ie^{i\phi}\sin\frac{\theta}{2}\\
i\cos\frac{\theta}{2}
\end{pmatrix}
$$

よって

$$
\begin{aligned}
r_y
&=
\begin{pmatrix}
\cos\frac{\theta}{2} &
e^{-i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
\begin{pmatrix}
-ie^{i\phi}\sin\frac{\theta}{2}\\
i\cos\frac{\theta}{2}
\end{pmatrix} \\
&=
-ie^{i\phi}\cos\frac{\theta}{2}\sin\frac{\theta}{2}
+ie^{-i\phi}\sin\frac{\theta}{2}\cos\frac{\theta}{2} \\
&=
i\left(e^{-i\phi}-e^{i\phi}\right)\cos\frac{\theta}{2}\sin\frac{\theta}{2} \\
&=
2\sin\phi\cos\frac{\theta}{2}\sin\frac{\theta}{2} \\
&=
\sin\theta\sin\phi
\end{aligned}
$$

となる。

最後に $z$ 成分は

$$
r_z=\langle\psi|\sigma_z|\psi\rangle
$$

である。$\sigma_z$ は上成分に $+1$、下成分に $-1$ を掛けるので

$$
\sigma_z|\psi\rangle
=
\begin{pmatrix}
1&0\\
0&-1
\end{pmatrix}
\begin{pmatrix}
\cos\frac{\theta}{2}\\
e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
=
\begin{pmatrix}
\cos\frac{\theta}{2}\\
-e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
$$

したがって

$$
\begin{aligned}
r_z
&=
\begin{pmatrix}
\cos\frac{\theta}{2} &
e^{-i\phi}\sin\frac{\theta}{2}
\end{pmatrix}
\begin{pmatrix}
\cos\frac{\theta}{2}\\
-e^{i\phi}\sin\frac{\theta}{2}
\end{pmatrix} \\
&=
\cos^2\frac{\theta}{2}-\sin^2\frac{\theta}{2} \\
&=
\cos\theta
\end{aligned}
$$

となる。

以上より

$$
\mathbf{r}=
(\langle\psi|\sigma_x|\psi\rangle,\,
\langle\psi|\sigma_y|\psi\rangle,\,
\langle\psi|\sigma_z|\psi\rangle)
=
(\sin\theta\cos\phi,\ \sin\theta\sin\phi,\ \cos\theta)
$$

となり、2章で書いたブロッホベクトルの式が実際に導かれる。

純粋状態に限れば

$$
|\mathbf{r}|=1
$$

となり、状態はブロッホ球**面**上の点として表される。

## 4. 測定確率はどう読めるか

ブロッホ球で状態が点 $\mathbf{r}$ として表されているとき、「測定する」とは
別の方向 $\mathbf{n}$ を1つ選び、その方向に沿って

- 「$\mathbf{n}$ 向きの状態か」
- 「その反対向きの状態か」

のどちらかを判定することだと思えばよい。

たとえば $z$ 方向の測定なら、基底状態 $|0\rangle, |1\rangle$ を区別する測定になる。
$x$ 方向の測定なら、今度は $x$ 方向の固有状態を区別する。

直観的には、状態ベクトル $\mathbf{r}$ が測定方向 $\mathbf{n}$ にどれだけ
揃っているかが、結果の偏りを決める。

- $\mathbf{r}$ が $\mathbf{n}$ と同じ向きなら、`+` が確率 1
- $\mathbf{r}$ が $-\mathbf{n}$ なら、`-` が確率 1
- $\mathbf{r}$ が $\mathbf{n}$ に直交していれば、`+` と `-` は半々

この「どれだけ揃っているか」はベクトルの内積 $\mathbf{r}\cdot\mathbf{n}$ で表される。
だから測定確率は最終的にこの内積で書ける。

より厳密には、単位ベクトル $\mathbf{n}$ の方向にスピンを測る、あるいは 2値観測

$$
\mathbf{n}\cdot\boldsymbol{\sigma}
$$

を測るとする。これは「$\mathbf{n}$ 方向成分を測る演算子」で、固有値は $+1$ と $-1$
の2つだけを持つ。

つまり測定結果 `+` とは

$$
(\mathbf{n}\cdot\boldsymbol{\sigma})\,|+\!:\mathbf{n}\rangle
=+|+\!:\mathbf{n}\rangle
$$

を満たす固有状態に対応し、測定結果 `-` とは

$$
(\mathbf{n}\cdot\boldsymbol{\sigma})\,|-\!:\mathbf{n}\rangle
=-|-\!:\mathbf{n}\rangle
$$

を満たす固有状態に対応する。

射影演算子 $P_+(\mathbf{n}), P_-(\mathbf{n})$ は、それぞれ
「状態の中から `+` 成分だけを取り出すフィルター」
「状態の中から `-` 成分だけを取り出すフィルター」
だと思えばよい。

この2つは

- $P_+(\mathbf{n})+P_-(\mathbf{n})=I$
- $P_\pm(\mathbf{n})^2=P_\pm(\mathbf{n})$
- $P_+(\mathbf{n})P_-(\mathbf{n})=0$

を満たし、確かに 2つの結果をちょうど選り分ける。

2値演算子 $\mathbf{n}\cdot\boldsymbol{\sigma}$ の固有値が $\pm 1$ であることを使うと、
対応する射影演算子は

$$
P_\pm(\mathbf{n})=\frac{1}{2}\left(I\pm \mathbf{n}\cdot\boldsymbol{\sigma}\right)
$$

と書ける。

実際、この演算子を固有状態に作用させると

$$
P_+(\mathbf{n})|+\!:\mathbf{n}\rangle=|+\!:\mathbf{n}\rangle,\qquad
P_+(\mathbf{n})|-\!:\mathbf{n}\rangle=0
$$

となるので、`+` 成分だけを残すことが分かる。$P_-(\mathbf{n})$ も同様である。

純粋状態 $|\psi\rangle$ に対する測定確率はボルン則により

$$
p_\pm(\mathbf{n})
=\langle\psi|P_\pm(\mathbf{n})|\psi\rangle
=\frac{1\pm \mathbf{r}\cdot\mathbf{n}}{2}
$$

となる。

この最後の等式も、射影演算子の形を使うとそのまま導ける。実際

$$
P_\pm(\mathbf{n})=\frac12\left(I\pm \mathbf{n}\cdot\boldsymbol{\sigma}\right)
$$

なので

$$
\begin{aligned}
\langle\psi|P_\pm(\mathbf{n})|\psi\rangle
&=
\left\langle\psi\middle|
\frac12\left(I\pm \mathbf{n}\cdot\boldsymbol{\sigma}\right)
\middle|\psi\right\rangle \\
&=
\frac12\langle\psi|I|\psi\rangle
\pm
\frac12\langle\psi|\mathbf{n}\cdot\boldsymbol{\sigma}|\psi\rangle \\
&=
\frac12
\pm
\frac12\langle\psi|(n_x\sigma_x+n_y\sigma_y+n_z\sigma_z)|\psi\rangle \\
&=
\frac12
\pm
\frac12\left(
n_x\langle\psi|\sigma_x|\psi\rangle
+n_y\langle\psi|\sigma_y|\psi\rangle
+n_z\langle\psi|\sigma_z|\psi\rangle
\right) \\
&=
\frac12
\pm
\frac12\left(n_x r_x+n_y r_y+n_z r_z\right) \\
&=
\frac{1\pm \mathbf{r}\cdot\mathbf{n}}{2}
\end{aligned}
$$

となる。ここで

$$
\mathbf{r}=(r_x,r_y,r_z),\qquad
\mathbf{n}=(n_x,n_y,n_z)
$$

なので

$$
\mathbf{r}\cdot\mathbf{n}=r_xn_x+r_yn_y+r_zn_z
$$

である。

この式の意味はとても単純で、$\mathbf{r}\cdot\mathbf{n}$ が

- $+1$ なら必ず `+`
- $0$ なら半々
- $-1$ なら必ず `-`

になる、ということである。中間の値なら、そのぶんだけ確率が連続的に変わる。

特に $z$ 基底では

$$
p_+(z)=\frac{1+z}{2}=\cos^2\frac{\theta}{2},\qquad
p_-(z)=\frac{1-z}{2}=\sin^2\frac{\theta}{2}
$$

である。

この変形は、2章で

$$
z=\cos\theta
$$

と置いたことと、三角関数の半角公式

$$
\cos^2\frac{\theta}{2}=\frac{1+\cos\theta}{2},\qquad
\sin^2\frac{\theta}{2}=\frac{1-\cos\theta}{2}
$$

を使えばすぐに分かる。実際、

$$
\frac{1+z}{2}
=
\frac{1+\cos\theta}{2}
=
\cos^2\frac{\theta}{2}
$$

であり、同様に

$$
\frac{1-z}{2}
=
\frac{1-\cos\theta}{2}
=
\sin^2\frac{\theta}{2}
$$

となる。

同様に純粋状態

$$
|\psi\rangle=
\cos\frac{\theta}{2}|0\rangle
+e^{i\phi}\sin\frac{\theta}{2}|1\rangle
$$

に対して

$$
\langle \sigma_x\rangle=\sin\theta\cos\phi,\qquad
\langle \sigma_y\rangle=\sin\theta\sin\phi,\qquad
\langle \sigma_z\rangle=\cos\theta
$$

となる。つまり $\phi$ は $z$ 方向だけの測定では見えず、$x,y$ 方向の統計に現れる。

### 4.1 射影演算子は何をしているか

ここで射影演算子 $P$ は、「基底そのものを取り出す」というより、
**ある部分空間の成分だけを残し、それに直交する成分を消す演算子**
だと思うとよい。

たとえば 1 次元の部分空間、つまり 1 本の基底ベクトル $|0\rangle$ に対応する

$$
P=|0\rangle\langle 0|
$$

は、任意の状態

$$
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
$$

に作用して

$$
P|\psi\rangle=\alpha |0\rangle
$$

を与える。つまり $|0\rangle$ 方向の成分だけを残す。
この意味では「基底成分を取り出す」でほぼ正しいが、一般には
1 本の基底ベクトルではなく、もっと大きな部分空間への射影もあるので、
「部分空間成分を取り出す」と言うほうが正確である。

純粋状態に対するボルン則は

$$
p=\langle\psi|P|\psi\rangle
$$

であり、「状態 $|\psi\rangle$ の中に、測定結果 $P$ に対応する成分が
どれだけ含まれているか」を確率として読んでいる。

### 4.2 2粒子ならどう読むか

文脈によっては、1粒子の `+` / `-` ではなく、**2粒子系の同時測定結果**を
表すために

$$
P_{+-}(\mathbf{n})
$$

のような記号を使う。これは典型的には

- 第1粒子を方向 $\mathbf{n}$ に沿って測ると `+`
- 第2粒子を同じ方向 $\mathbf{n}$ に沿って測ると `-`

という**組み合わせ結果**に対応する射影演算子である。

2粒子ヒルベルト空間では、方向 $\mathbf{n}$ のスピン固有状態
$|+\!:\mathbf{n}\rangle,|-\!:\mathbf{n}\rangle$ を使って

$$
P_{+-}(\mathbf{n})
=
\bigl(|+\!:\mathbf{n}\rangle\langle+\!:\mathbf{n}|\bigr)
\otimes
\bigl(|-\!:\mathbf{n}\rangle\langle-\!:\mathbf{n}|\bigr)
$$

と書ける。つまり

$$
P_{+-}(\mathbf{n})
=
P_+(\mathbf{n})\otimes P_-(\mathbf{n})
$$

であり、「1粒子目で `+`、2粒子目で `-` という成分だけを取り出すフィルター」
になっている。

ここで「第1粒子」「第2粒子」という言い方は、テンソル積空間

$$
\mathcal{H}_1\otimes\mathcal{H}_2
$$

のそれぞれの因子に対応している。  
したがって

$$
P_+(\mathbf{n})\otimes P_-(\mathbf{n})
$$

は、

- 第1粒子の状態には $P_+(\mathbf{n})$ を作用させて `+` 成分だけを残す
- 第2粒子の状態には $P_-(\mathbf{n})$ を作用させて `-` 成分だけを残す

という意味を持つ。

つまり $P_{+-}(\mathbf{n})$ は、「2粒子全体の状態の中から
第1粒子が `+`、第2粒子が `-` であるような部分だけを選び出す射影」
になっている。

したがって

$$
\langle\Psi|P_{+-}(\mathbf{n})|\Psi\rangle
$$

は、

> 系全体が純粋状態 $|\Psi\rangle$ にあるとき、2粒子を方向 $\mathbf{n}$ に沿って同時測定して
> 結果が `(+,-)` になる確率

を表す。

ここで注意したいのは、**この 2 粒子の確率は一般には**

$$
\frac{1\pm \mathbf{r}\cdot\mathbf{n}}{2}
$$

**の形にはならない**ということである。  
この式は 1 粒子の

$$
\langle\psi|P_\pm(\mathbf{n})|\psi\rangle
$$

に対するものであり、2 粒子の

$$
\langle\Psi|P_{+-}(\mathbf{n})|\Psi\rangle
$$

では、ふつう第1粒子と第2粒子の相関まで含めて考える必要がある。

ただし、射影演算子を代入するところまでは丁寧に書ける。まず

$$
P_{+-}(\mathbf{n})
=
P_+(\mathbf{n})\otimes P_-(\mathbf{n})
=
\frac12\left(I+\mathbf{n}\cdot\boldsymbol{\sigma}\right)
\otimes
\frac12\left(I-\mathbf{n}\cdot\boldsymbol{\sigma}\right)
$$

なので

$$
\begin{aligned}
\langle\Psi|P_{+-}(\mathbf{n})|\Psi\rangle
&=
\left\langle\Psi\middle|
\frac12\left(I+\mathbf{n}\cdot\boldsymbol{\sigma}\right)
\otimes
\frac12\left(I-\mathbf{n}\cdot\boldsymbol{\sigma}\right)
\middle|\Psi\right\rangle \\
&=
\frac14
\left\langle\Psi\middle|
\left(I+\mathbf{n}\cdot\boldsymbol{\sigma}\right)
\otimes
\left(I-\mathbf{n}\cdot\boldsymbol{\sigma}\right)
\middle|\Psi\right\rangle \\
&=
\frac14
\Bigl(
\langle\Psi|I\otimes I|\Psi\rangle
-\langle\Psi|I\otimes(\mathbf{n}\cdot\boldsymbol{\sigma})|\Psi\rangle \\
&\qquad\qquad
+\langle\Psi|(\mathbf{n}\cdot\boldsymbol{\sigma})\otimes I|\Psi\rangle
-\langle\Psi|(\mathbf{n}\cdot\boldsymbol{\sigma})\otimes(\mathbf{n}\cdot\boldsymbol{\sigma})|\Psi\rangle
\Bigr)
\end{aligned}
$$

となる。

正規化された状態では

$$
\langle\Psi|I\otimes I|\Psi\rangle=1
$$

なので、最終的に

$$
\langle\Psi|P_{+-}(\mathbf{n})|\Psi\rangle
=
\frac14\Bigl(
1
-\langle I\otimes(\mathbf{n}\cdot\boldsymbol{\sigma})\rangle
+\langle (\mathbf{n}\cdot\boldsymbol{\sigma})\otimes I\rangle
-\langle (\mathbf{n}\cdot\boldsymbol{\sigma})\otimes(\mathbf{n}\cdot\boldsymbol{\sigma})\rangle
\Bigr)
$$

と書ける。ここで最後の項が**2 粒子の相関**を表しており、これがあるため、
一般には 1 粒子の場合のような単純な

$$
\frac{1\pm \mathbf{r}\cdot\mathbf{n}}{2}
$$

には縮約されない。

1粒子の式

$$
\langle\psi|P_\pm(\mathbf{n})|\psi\rangle
$$

と本質は同じで、違うのは「どの結果を選び出す射影か」だけである。
添字が増えているのは、測定結果が 1 個ではなく 2 個並んでいるからだと思えばよい。

## 5. スピン 1/2 との関係

ブロッホ球は、スピン 1/2 粒子の向きをそのまま古典的に表しているわけではない。
正確には、**2次元ヒルベルト空間の量子状態**を表している。

ただしスピン 1/2 の場合、

$$
\mathbf{r}
=
\bigl(
\langle\psi|\sigma_x|\psi\rangle,\,
\langle\psi|\sigma_y|\psi\rangle,\,
\langle\psi|\sigma_z|\psi\rangle
\bigr)
$$

という意味で、$\mathbf{r}$ を「スピン期待値の向き」と読むことができる。
この意味で幾何学的直観が得られる。

注意:
- 古典的なベクトルが空間中に実在して回っている、と解釈してはいけない。
- ブロッホベクトルは、測定統計を要約する量である。

## 6. ユニタリ時間発展は球の回転になる

ハミルトニアンが

$$
H=\frac{\hbar\Omega}{2}\,\mathbf{n}\cdot\boldsymbol{\sigma}
$$

の形なら、時間発展演算子は

$$
U(t)=e^{-iHt/\hbar}
$$

で与えられ、純粋状態は

$$
|\psi(t)\rangle=U(t)|\psi(0)\rangle
$$

と変化する。このときブロッホベクトル $\mathbf{r}$ は、実空間で
軸 $\mathbf{n}$ のまわりに角速度 $\Omega$ で回転する。

したがって、2準位系のユニタリ発展はブロッホ球上では回転として可視化できる。

## 7. 測定後状態

射影測定で結果 $+$ が得られたなら、状態更新は

$$
|\psi\rangle \to |\psi'\rangle=\frac{P_+(\mathbf{n})|\psi\rangle}{ \sqrt{\langle\psi|P_+(\mathbf{n})|\psi\rangle}}
$$

で与えられる。結果として、ブロッホベクトルは
$\mathbf{n}$ 方向の極へ移る。

つまりブロッホ球では
- ユニタリ発展は滑らかな回転
- 射影測定は一般に不連続な更新

として表される。

## 8. よくある誤解

### 8.1 ブロッホ球は多準位系にはそのまま使えない

ブロッホ球の単純な3次元表示は 2準位系に特有である。  
3準位以上では状態空間はもっと高次元で、同じ意味での球にはならない。

### 8.2 球面上の点が「隠れた実在の向き」を意味するわけではない

ブロッホ球は量子状態の表現であり、すべての測定軸に対して事前に値が
決まっているという古典像を保証しない。

### 8.3 位相は見えないのではなく、基底を変えると見える

全体位相は観測不能だが、相対位相 $\phi$ は観測基底を変えると
干渉や期待値の違いとして現れる。

## 9. 最低限のまとめ

- 2準位系の任意の純粋状態は
  $$
  |\psi\rangle=
  \cos\frac{\theta}{2}|0\rangle
  +e^{i\phi}\sin\frac{\theta}{2}|1\rangle
  $$
  と書ける。
- 純粋状態はブロッホ球面上の点 $\mathbf{r}$ に対応し、$|\mathbf{r}|=1$ を満たす。
- 測定確率は
  $$
  p_\pm(\mathbf{n})=\frac{1\pm \mathbf{r}\cdot\mathbf{n}}{2}
  $$
  で決まる。
- 射影演算子は、知りたい測定結果に対応する部分空間の成分だけを残す。
- ユニタリ発展はブロッホベクトルの回転として表される。

この5点を押さえると、ブロッホ球は「量子ビットの見た目の模型」ではなく、
2準位量子状態の厳密で便利な表現だと理解できる。
