# STORY3: もつれからベルの不等式へ至る流れ

## 目的

この文書は、`PHYSICS2.md` で導入した

- 状態ベクトル
- パウリ行列
- 方向 $\mathbf{n}$ に沿った測定 $\mathbf{n}\cdot\boldsymbol{\sigma}$

を既知として、そこから

1. 2粒子系をどう書くか
2. もつれとは何か
3. なぜベルの不等式が現れるのか
4. 量子力学がどこで古典的な直観を越えるのか

を、一つの流れとして整理するためのメモである。

狙いは、最初から

- 「ベル違反とは不思議な超能力だ」
- 「もつれとは遠隔で情報が飛ぶことだ」

といった印象で話を始めることではない。  
むしろ、

1. まず2粒子系の数学を作る
2. その中で、積状態では説明できない相関をもつ状態を見つける
3. その相関に対して古典的説明の上限を作る
4. 量子予言がその上限を越えることを示す

という順番をはっきりさせることにある。

---

## 出発点: 1粒子から2粒子へ

`PHYSICS2.md` では、1個の二状態系を

```math
\mathcal{H}\cong\mathbb{C}^2
```
で表し、方向 $\mathbf{n}$  に沿った測定を

```math
\mathbf{n}\cdot\boldsymbol{\sigma}
=
n_x\sigma_x+n_y\sigma_y+n_z\sigma_z
```
と書いた。  
固有値は `+1,-1` であり、観測結果はこの二値に対応していた。

では、粒子が二つあるときはどうするか。

直感的には、

- 左の粒子に対する情報
- 右の粒子に対する情報

を同時に持てる必要がある。  
そのため量子力学では、2粒子系の状態空間を

```math
\mathcal{H}_L\otimes\mathcal{H}_R
\cong
\mathbb{C}^2\otimes\mathbb{C}^2
\cong
\mathbb{C}^4
```
というテンソル積空間で表す。

`z` 基底を使えば、基底状態は

```math
|+z\rangle_L|+z\rangle_R,\quad
|+z\rangle_L|-z\rangle_R,\quad
|-z\rangle_L|+z\rangle_R,\quad
|-z\rangle_L|-z\rangle_R
```
の4つである。  
略して

```math
|++\rangle,\quad |+-\rangle,\quad |-+\rangle,\quad |--\rangle
```
と書いてもよい。

ここで大事なのは、二つの粒子があるなら、状態空間は「2本のラベルの組」では終わらないという点である。  
1粒子のときと同様に、ここでも重ね合わせが許されるので、一般状態は

```math
|\Psi\rangle
=
c_{++}|++\rangle
+c_{+-}|+-\rangle
+c_{-+}|-+\rangle
+c_{--}|--\rangle
```
と書ける。

---

## 実験 1: 分裂した二つの球を同時に測る

Aliceが黒い球を二つに分ける。  
左に一つ、右に一つ置く。  
Bobが左を、Charlieが右を叩く。

まず二人は、同じ向き `z` で同時に測った。

すると、

- 左が `Yay` なら右は `Oops`
- 左が `Oops` なら右は `Yay`

となる。  
少なくとも理想化したこのモデルでは、同じ結果が揃うことはない。

Aliceが言う。  
「あべこべで連動してる」

Bobがうなずく。  
「少なくとも独立ではない」

Charlieはノートに書く。  
「同方向の同時測定で、強い反相関がある」

## Physics Note 1: 積状態と相関

もし左と右が本当に独立なら、全状態は

```math
|\psi\rangle_L\otimes|\phi\rangle_R
```
という積状態で書ける。  
このとき左右の同時確率は、各側の確率の積で決まる。

たとえば左が

```math
|\psi\rangle_L=\alpha|+\rangle_L+\beta|-\rangle_L
```
右が

```math
|\phi\rangle_R=\gamma|+\rangle_R+\delta|-\rangle_R
```
なら、

```math
|\psi\rangle_L\otimes|\phi\rangle_R
=
\alpha\gamma|++\rangle
+\alpha\delta|+-\rangle
+\beta\gamma|-+\rangle
+\beta\delta|--\rangle
```
である。

ここで係数が

```math
c_{++}=\alpha\gamma,\quad
c_{+-}=\alpha\delta,\quad
c_{-+}=\beta\gamma,\quad
c_{--}=\beta\delta
```
のように因数分解できるなら、その状態は積状態である。

しかし一般の4成分状態は、必ずしもこの形にはならない。  
特に、積状態に書き直せない状態を**もつれ状態**と呼ぶ。

---

## 実験 2: 反相関だけなら古典でも作れそうに見える

Aliceが首をかしげる。  
「でも、最初から“左は上、右は下”って決まってただけかもしれないよね？」

Bobが答える。  
「同じ向きで反対が出るだけなら、それでも説明できそうに見える」

Charlieが続ける。  
「問題は、測定方向を変えたときにも、同じ一組の仕込みで全部説明できるかどうかだ」

そこで三人は、左右の測定方向を少しずつ変えていく。  
すると結果はこうだった。

- 同じ向きなら、ほぼ完全な反相関
- 近い向きなら、かなり強い反相関
- 直交に近づくと、反相関は弱まる
- 反対向きまで回すと、今度は相関の符号が反転する

Bobが言う。  
「一組の隠れた答え表だけで、この角度依存を全部支えられるのかが本題だ」

---

## 実験 3: 特別な二粒子状態を探す

同じ向きで必ず反対が出るなら、`z` 基底だけを見る限り

```math
|+-\rangle,\qquad |-+\rangle
```
が有力に見える。  
しかしこれらのどちらか一方を最初から持っているだけなら、`x` や `y` 方向に測定を回したときの対称性が壊れてしまう。

そこで Charlie は言う。  
「どの方向を特別扱いしない反相関がほしいなら、$|+-\rangle$ と $|-+\rangle$ を等重みで混ぜた状態をまず疑うべきだ」

その候補は

```math
|\Psi^-\rangle
=
\frac{1}{\sqrt2}\Bigl(
|+z\rangle_L|-z\rangle_R
-|-z\rangle_L|+z\rangle_R
\Bigr)
```
である。  
略記すれば

```math
|\Psi^-\rangle=\frac{1}{\sqrt2}(|+-\rangle-|-+\rangle)
```
となる。

Aliceが言う。  
「足し算じゃなくて、引き算なんだ」

Charlieがうなずく。  
「ここでは相対位相の `-` が本質だ。これが回転に対して特別に安定な反相関を作る」

## Physics Note 2: singlet 状態

この状態

```math
|\Psi^-\rangle=\frac{1}{\sqrt2}(|+-\rangle-|-+\rangle)
```
は、二つのスピン `1/2` の**singlet 状態**と呼ばれる。

まず、これは積状態ではない。  
もし

```math
|\Psi^-\rangle=(\alpha|+\rangle+\beta|-\rangle)\otimes(\gamma|+\rangle+\delta|-\rangle)
```
と書けるなら、

```math
\alpha\gamma=0,\qquad
\beta\delta=0,\qquad
\alpha\delta=\frac1{\sqrt2},\qquad
\beta\gamma=-\frac1{\sqrt2}
```
を同時に満たさねばならないが、これは不可能である。  
したがって $|\Psi^-\rangle$ はもつれ状態である。

また、`z` 方向で同時測定すると

- $|+-\rangle$ が確率 `1/2`
- $|-+\rangle$ が確率 `1/2`
- $|++\rangle,|--\rangle$ は確率 `0`

となる。  
つまり同じ方向では、必ず反対の結果が出る。

さらに重要なのは、この状態が `z` 基底だけで特別な意味を持つのではなさそうだ、という点である。  
もし本当に「どの方向も特別でない反相関」を表しているなら、`z` 以外の方向でも同様の規則が出てほしい。  
この期待が正しいかどうかは、次の節で相関関数

```math
E(\mathbf{a},\mathbf{b})
```
を実際に計算することで確かめる。

---

## 実験 4: 局所測定を式で書く

ここで `PHYSICS2.md` の道具がそのまま使える。  
左で方向 $\mathbf{a}$ を測るなら、その演算子は

```math
\mathbf{a}\cdot\boldsymbol{\sigma}\otimes I
```
である。  
右で方向 $\mathbf{b}$ を測るなら

```math
I\otimes \mathbf{b}\cdot\boldsymbol{\sigma}
```
である。

左右同時の相関を調べたいなら、結果 $\pm1$ の積の平均

```math
E(\mathbf{a},\mathbf{b})
=
\left\langle\Psi\middle|
(\mathbf{a}\cdot\boldsymbol{\sigma})\otimes(\mathbf{b}\cdot\boldsymbol{\sigma})
\middle|\Psi\right\rangle
```
を考えればよい。

Aliceが聞く。  
「なんでこれが“相関”なの？」

Bobが答える。  
「左も右も結果は $\pm1$ だろ。だから積は

- 同符号なら `+1`
- 反対符号なら `-1`

になる。これを平均すれば、相関の強さと符号がそのまま入る」

## Physics Note 3: 相関関数

左の測定結果を $A_{\mathbf{a}}\in\{+1,-1\}$、右の結果を $B_{\mathbf{b}}\in\{+1,-1\}$ とする。  
すると相関関数は

```math
E(\mathbf{a},\mathbf{b})=\langle A_{\mathbf{a}}B_{\mathbf{b}}\rangle
```
である。

- いつも同じ結果なら `E=+1`
- いつも反対なら `E=-1`
- 無相関に近ければ $E\approx0$

量子力学では、この平均は

```math
E(\mathbf{a},\mathbf{b})
=
\langle\Psi|
(\mathbf{a}\cdot\boldsymbol{\sigma})\otimes(\mathbf{b}\cdot\boldsymbol{\sigma})
|\Psi\rangle
```
で与えられる。

singlet 状態 $|\Psi^-\rangle$ に対しては、結果は

```math
E(\mathbf{a},\mathbf{b})=-\mathbf{a}\cdot\mathbf{b}
```
になる。  
この式は重要なので、少し丁寧に導いておく。

まず

```math
\mathbf{a}\cdot\boldsymbol{\sigma}
=a_x\sigma_x+a_y\sigma_y+a_z\sigma_z,
\qquad
\mathbf{b}\cdot\boldsymbol{\sigma}
=b_x\sigma_x+b_y\sigma_y+b_z\sigma_z
```
だから、

```math
(\mathbf{a}\cdot\boldsymbol{\sigma})\otimes(\mathbf{b}\cdot\boldsymbol{\sigma})
=
\sum_{i,j\in\{x,y,z\}} a_i b_j\,(\sigma_i\otimes\sigma_j)
```
と展開できる。  
したがって必要なのは、singlet に対する

```math
\langle\Psi^-|\sigma_i\otimes\sigma_j|\Psi^-\rangle
```
を知ることである。

ここで

```math
|\Psi^-\rangle=\frac{1}{\sqrt2}(|+-\rangle-|-+\rangle)
```
を使って直接計算すると、

```math
(\sigma_z\otimes\sigma_z)|\Psi^-\rangle=-|\Psi^-\rangle
```
である。実際、

```math
\sigma_z|+\rangle=|+\rangle,\qquad
\sigma_z|-\rangle=-|-\rangle
```
なので

```math
\begin{aligned}
(\sigma_z\otimes\sigma_z)|+-\rangle&=-|+-\rangle,\\
(\sigma_z\otimes\sigma_z)|-+\rangle&=-|-+\rangle
\end{aligned}
```
となり、両方の成分に `-1` がかかる。

同様に

```math
\sigma_x|+\rangle=|-\rangle,\qquad
\sigma_x|-\rangle=|+\rangle
```
を使うと

```math
\begin{aligned}
(\sigma_x\otimes\sigma_x)|+-\rangle&=|-+\rangle,\\
(\sigma_x\otimes\sigma_x)|-+\rangle&=|+-\rangle
\end{aligned}
```
だから

```math
(\sigma_x\otimes\sigma_x)|\Psi^-\rangle=-|\Psi^-\rangle
```
となる。  
`y` についても

```math
\sigma_y|+\rangle=i|-\rangle,\qquad
\sigma_y|-\rangle=-i|+\rangle
```
より

```math
(\sigma_y\otimes\sigma_y)|\Psi^-\rangle=-|\Psi^-\rangle
```
が成り立つ。

したがって対角成分については

```math
\langle\Psi^-|\sigma_x\otimes\sigma_x|\Psi^-\rangle
=
\langle\Psi^-|\sigma_y\otimes\sigma_y|\Psi^-\rangle
=
\langle\Psi^-|\sigma_z\otimes\sigma_z|\Psi^-\rangle
=-1
```
である。

一方、混合成分は 0 になる。  
たとえば

```math
(\sigma_x\otimes\sigma_z)|\Psi^-\rangle
=
-\frac{1}{\sqrt2}\Bigl(|++\rangle+|--\rangle\Bigr)
```
であり、これは $|\Psi^-\rangle$ と直交している。  
したがって

```math
\langle\Psi^-|\sigma_x\otimes\sigma_z|\Psi^-\rangle=0
```
である。  
他の $i\neq j$ についても同様に 0 になる。

結局、

```math
\langle\Psi^-|\sigma_i\otimes\sigma_j|\Psi^-\rangle=-\delta_{ij}
```
が成り立つ。  
これを上の展開式に戻すと

```math
\begin{aligned}
E(\mathbf{a},\mathbf{b})
&=
\sum_{i,j}a_i b_j
\langle\Psi^-|\sigma_i\otimes\sigma_j|\Psi^-\rangle\\
&=
\sum_{i,j}a_i b_j(-\delta_{ij})\\
&=
-\sum_i a_i b_i\\
&=
-\mathbf{a}\cdot\mathbf{b}
\end{aligned}
```
となる。

したがって二つの測定方向のなす角を $\theta$ とすれば

```math
E(\theta)=-\cos\theta
```
である。

この式は重要で、次の3つを一気に含んでいる。

1. $\theta=0$ なら `E=-1`  
同方向では完全反相関。

2. $\theta=\pi/2$ なら `E=0`  
直交方向では平均相関が消える。

3. $\theta=\pi$ なら `E=+1`  
反対向きでは完全相関。

つまり「単一粒子では $\cos\theta$ が期待値に現れた」のと同じ幾何が、二粒子相関では $-\cos\theta$ として現れている。

---

## 実験 5: なぜこれが古典的に苦しいのか

Aliceはまだ納得しきれない。  
「でもさ、左右に行く前から、各方向に対する答えが決まってるだけかもしれない」

Charlieがうなずく。  
「その可能性をちゃんと潰すのがベルの仕事だ。  
“どの方向を聞かれても答えは最初から決まっていた”という模型に、超えられない上限を作る」

Bobがノートに四つの設定を書く。

- 左は `a` または `a'`
- 右は `b` または `b'`

ここで `a,a'` は**左側で選べる二つの測定方向**、`b,b'` は**右側で選べる二つの測定方向**を表す記号である。  
たとえば `a` は「左の装置をこの向きに合わせる」、`a'` は「左の装置を別の向きに合わせる」という意味で、`b,b'` も同様である。  
まだ結果そのものではなく、どの向きを測るかという**設定ラベル**だと思えばよい。

一回の試行で、実際に測るのは左右それぞれ一つだけ。  
しかし局所隠れ変数モデルでは、「もし別の向きを選んでも、その答えもすでに決まっていた」と考える。

このとき左の答えを

```math
A_a,\ A_{a'}\in\{\pm1\}
```
右の答えを

```math
B_b,\ B_{b'}\in\{\pm1\}
```
と書ける。  
ここで `A_a` は「左で設定 `a` を選んだときに返る結果」、`A_{a'}` は「左で設定 `a'` を選んだときに返る結果」である。  
同様に `B_b`,`B_{b'}` は右側の結果を表す。  
添字は“どの設定に対する答えか”を示しており、値そのものは

```math
+1=\text{Yay},\qquad -1=\text{Oops}
```
のどちらかである。

したがって、`a` と `A_a` は別物である。

- `a` は測定方向のラベル
- `A_a` はその方向で実際に返る結果

CHSH では、この区別が重要になる。

## Physics Note 4: CHSH の古典上限

実験で直接集計できるのは、まず4種類の平均相関である。

```math
E(a,b),\qquad E(a,b'),\qquad E(a',b),\qquad E(a',b')
```
たとえば $E(a,b)$ は、

- 左で設定 `a`
- 右で設定 `b`

を選んだ試行だけを集めて、結果の積の平均を取ったものである。  
つまり実験では、新しいもつれ対を何度も用意し、そのたびに設定をランダムに選んでデータを4つの組に分けて集計する。

ここで局所隠れ変数モデルを考える。  
各試行には、観測される前からその試行を特徴づける隠れた情報 $\lambda$ があるとしよう。  
そのとき結果は

```math
A(a,\lambda),\ A(a',\lambda)\in\{\pm1\},
\qquad
B(b,\lambda),\ B(b',\lambda)\in\{\pm1\}
```
のように書ける。

この記法では、たとえば $A(a,\lambda)$ は

- 試行に対応する隠れ変数が $\lambda$
- 左で設定 `a` を選んだ

ときに返る答えである。  
重要なのは、**1試行で全部を実測するわけではない**が、局所隠れ変数モデルでは「選ばれなかった設定に対する答えも、$\lambda$ の中にすでに入っている」と仮定することである。

この仮定のもとで、各 $\lambda$ ごとに補助量

```math
s(\lambda)
=
A(a,\lambda)B(b,\lambda)
+A(a,\lambda)B(b',\lambda)
+A(a',\lambda)B(b,\lambda)
-A(a',\lambda)B(b',\lambda)
```
を考える。  
これは実験で1回ごとに直接測る量ではなく、**局所隠れ変数モデルの内部で考える仮想的な量**である。  
これを整理すると

```math
s(\lambda)
=
A(a,\lambda)\bigl(B(b,\lambda)+B(b',\lambda)\bigr)
+A(a',\lambda)\bigl(B(b,\lambda)-B(b',\lambda)\bigr)
```
である。

ここで $B(b,\lambda),B(b',\lambda)$ はそれぞれ $\pm1$ だから、

- $B(b,\lambda)+B(b',\lambda)$ は `0` または $\pm2$
- $B(b,\lambda)-B(b',\lambda)$ も `0` または $\pm2$

となり、しかもこの二つのうち片方が $\pm2$ なら、もう片方は `0` である。  
したがって必ず

```math
|s(\lambda)|\le2
```
である。

次に、$\lambda$ は各試行に埋め込まれている隠れた内部情報だと思えばよい。  
ただし実際の試行では、毎回まったく同じ $\lambda$ が現れるとは限らない。  
試行ごとに $\lambda$ はある分布に従ってばらついていると考えるのが自然であり、その重みを $\rho(\lambda)$ と書く。

```math
\rho(\lambda)\ge 0,\qquad
\int d\lambda\,\rho(\lambda)=1
```
このとき $A(a,\lambda)B(b,\lambda)$ は、「その試行の隠れ変数がたまたま $\lambda$ だったなら、左で `a`、右で `b` を選んだとき結果の積がどうなるか」を表している。  
したがって

```math
E(a,b)=\int d\lambda\,\rho(\lambda)\,A(a,\lambda)B(b,\lambda)
```
は、その積を $\lambda$ の分布で平均したもの、つまり設定 `(a,b)` に対する**平均相関**である。
  
他の3つの相関も同様である。したがって CHSH 量

```math
S
=
E(a,b)+E(a,b')+E(a',b)-E(a',b')
```
は

```math
S=\int d\lambda\,\rho(\lambda)\,s(\lambda)
```
となる。  
したがって

```math
|S|\le2
```
を得る。  
これが CHSH 形のベル不等式である。

ここで使った仮定は本質的に次の三つである。

1. 各設定に対する結果が、測定前から定まっている  
2. 左の結果は右の設定に依らず、右の結果は左の設定に依らない
3. 測定設定の選択は、隠れ変数 $\lambda$ の分布 $\rho(\lambda)$ と独立である

3つ目の仮定は**測定独立性**と呼ばれる。  
これは「どの向きを測るか」という実験者の選択が、あらかじめ粒子対に埋め込まれていた隠れ変数と不自然に相関していない、という仮定である。  
この仮定があるからこそ

```math
E(a,b)=\int d\lambda\,\rho(\lambda)\,A(a,\lambda)B(b,\lambda)
```
のように、同じ $\rho(\lambda)$ を使って4つの相関を同時に書ける。

つまり $|S|\le2$ は、**測定独立性を含む局所隠れ変数モデル**の上限である。

---

## 実験 6: 量子予言はどこまで行くか

Charlieは分度器を回しながら言う。  
「あとは量子相関 $E(\mathbf{a},\mathbf{b})=-\cos\theta$ を CHSH に代入するだけだ」

よく使われる配置として、

- $a=0^\circ$
- $a'=90^\circ$
- $b=45^\circ$
- $b'=-45^\circ$

を選ぶ。

このとき角度差はそれぞれ

- `a` と `b`: $45^\circ$
- `a` と `b'`: $45^\circ$
- `a'` と `b`: $45^\circ$
- `a'` と `b'`: $135^\circ$

なので

```math
\begin{aligned}
E(a,b)&=-\cos45^\circ=-\frac{\sqrt2}{2},\\
E(a,b')&=-\cos45^\circ=-\frac{\sqrt2}{2},\\
E(a',b)&=-\cos45^\circ=-\frac{\sqrt2}{2},\\
E(a',b')&=-\cos135^\circ=+\frac{\sqrt2}{2}.
\end{aligned}
```
したがって

```math
\begin{aligned}
S
&=
E(a,b)+E(a,b')+E(a',b)-E(a',b')\\
&=
-\frac{\sqrt2}{2}
-\frac{\sqrt2}{2}
-\frac{\sqrt2}{2}
-\frac{\sqrt2}{2}\\
&=-2\sqrt2
\end{aligned}
```
となり、

```math
|S|=2\sqrt2>2
```
である。

Aliceが目を見開く。  
「古典の上限を超えた」

Bobがうなずく。  
「でも無限に超えるわけじゃない。量子にも量子の上限がある」

Charlieが補足する。  
「その最大値 $2\sqrt2$ は Tsirelson bound と呼ばれる。  
つまり量子力学は古典より広いが、何でもありではない」

## Physics Note 5: 何が否定されるのか

実験で `|S|>2` が観測されたとき、否定されるのは

```math
\text{局所隠れ変数モデル}
```
である。

ただし、ここで直ちに言ってよいことと、まだ言えないことを分ける必要がある。

言ってよいこと:

- 左右の結果は、単純な「最初から埋め込まれた局所的答え表」では説明できない
- 量子状態は、個々の粒子が独立な性質を持つという古典像を超えている

まだ言えないこと:

- 右で何を測るかを左へ使って自由に通信できる
- 目に見える機械的信号が瞬時に飛んだ

ベル違反は「古典的局所実在論の限界」を示す。  
しかしそれは、そのまま「超光速通信ができる」という主張ではない。

---

## 物語としての一番自然な筋

ここまでを物語の順番としてまとめると、流れは次のようになる。

1. 1粒子の二状態系を $\mathbb{C}^2$ とパウリ行列で書く  
2. 2粒子系では状態空間が $\mathbb{C}^2\otimes\mathbb{C}^2$ に広がる  
3. 一般状態の中には、積状態では書けないもつれ状態がある  
4. singlet 状態は、どの方向でも同方向測定で完全反相関を与える  
5. 相関関数は $E(\mathbf{a},\mathbf{b})=-\mathbf{a}\cdot\mathbf{b}$ になる  
6. 局所隠れ変数モデルには CHSH 上限 $|S|\le2$ がある  
7. 量子予言は適切な角度設定で $|S|=2\sqrt2$ を与え、その上限を越える

この意味で、ベルの不等式は「不思議な相関がある」という話を、初めて定量的に古典と切り分ける道具である。

---

## 最後に一行で言うと

ベルの不等式が自然に現れるのは、

**「二粒子相関を、各地点の答えが最初から局所的に決まっている模型で説明できるか」**

と問うたとき、その模型には越えられない上限があり、もつれ状態の量子予言がその上限を実際に越えるからである。
