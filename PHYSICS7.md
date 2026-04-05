# PHYSICS7: なぜ空間回転の生成子は角運動量なのか

## 目的

この文書は、

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right),
\qquad
J_{\mathbf n}=\mathbf n\cdot\mathbf J
$$

という回転演算子の形が、なぜ自然なのかを説明するためのメモである。

ここで知りたいのは、単に式の形ではない。  
知りたいのは、

- 回転演算子はなぜ指数関数になるのか
- その指数の中に、なぜ角運動量が入るのか
- なぜ `\mathbf n\cdot\mathbf J` という形になるのか

である。

---

## 結論

先に結論を言うと、流れは次の通りである。

1. 微小回転は「ほとんど恒等変換」なので、まず

$$
   U(\delta\theta,\mathbf n)=I+\delta\theta\,K_{\mathbf n}+O(\delta\theta^2)
   $$

   と一次まで展開できる  
   さらに確率保存から係数は反エルミートでなければならないので、
$$
   U(\delta\theta,\mathbf n)=I-\frac{i}{\hbar}\delta\theta\,G_{\mathbf n}
$$

   の形で書ける
2. それを何回も重ねると有限回転になり、指数関数
   $$
   U(\theta,\mathbf n)=\exp\!\left(-\frac{i}{\hbar}\theta\,G_{\mathbf n}\right)
   $$
   が出る
3. 空間回転に対して座標や運動量を正しく回す生成子を調べると、それは角運動量である
4. したがって
   $$
   G_{\mathbf n}=J_{\mathbf n}=\mathbf n\cdot\mathbf J
   $$
   となる

つまり、

**回転の生成子が角運動量であることは、回転を無限小から作ると自然に見えてくる。**

---

## 1. 微小回転から始める

まず、方向 $\mathbf n$ のまわりに、ごく小さな角度 $\delta\theta$ だけ回すことを考える。

このような微小変換は、「ほとんど何もしないが、少しだけ変える」ので、回転演算子はまず

$$
U(\delta\theta,\mathbf n)
=
I+\delta\theta\,K_{\mathbf n}
+O(\delta\theta^2)
$$

の形になるはずである。  
ここで $K_{\mathbf n}$ は、回転の一次の変化を決める行列である。  
$O(\delta\theta^2)$ は二次以上の小さな項であり、微小回転ではまず一次の項だけを見ればよい。

しかし量子力学では、回転は確率を保たなければならないので、`U` はユニタリでなければならない。  
そのため一次の係数は反エルミートであり、

$$
K_{\mathbf n}=-\frac{i}{\hbar}G_{\mathbf n}
$$

と書ける。  
ここで $G_{\mathbf n}$ はエルミートな演算子で、これを**生成子**と呼ぶ。

この形にしておく利点は、$G_{\mathbf n}$ が角運動量の次元を持つようになることである。  
実際、角度 $\delta\theta$ は無次元、$\hbar$ は角運動量の次元を持つので、

$$
\frac{\delta\theta}{\hbar}G_{\mathbf n}
$$

全体が無次元になり、指数関数や微小変換の係数として自然になる。

したがって微小回転は

$$
U(\delta\theta,\mathbf n)
=
I-\frac{i}{\hbar}\delta\theta\,G_{\mathbf n}
+O(\delta\theta^2)
$$

となる。

この時点では、まだ $G_{\mathbf n}$ が何かは決まっていない。  
ここから先で「回転として正しい変換を作るには、$G_{\mathbf n}$ が何でなければならないか」を調べる。

---

## 2. なぜ有限回転が指数関数になるのか

ここが最初の山場である。  
指数関数は、突然思いつきで導入するのではない。  
**微小回転を何回も重ねる** と、自然に指数関数になる。

まず、同じ軸 $\mathbf n$ のまわりの回転では、角度は足し合わさるべきである。  
したがって

$$
U(\theta_1,\mathbf n)\,U(\theta_2,\mathbf n)
=
U(\theta_1+\theta_2,\mathbf n)
$$

が成り立つ。

そこで、全体の角度 $\theta$ を `N` 等分して

$$
\delta\theta=\frac{\theta}{N}
$$

とする。  
すると角度 $\theta$ の回転は、角度 $\delta\theta$ の微小回転を `N` 回繰り返したものだから、

$$
U(\theta,\mathbf n)=\bigl(U(\delta\theta,\mathbf n)\bigr)^N
$$

と書ける。

ここで前節の微小回転の形

$$
U(\delta\theta,\mathbf n)
=
I-\frac{i}{\hbar}\delta\theta\,G_{\mathbf n}
+O(\delta\theta^2)
$$

を代入すると、

$$
U(\theta,\mathbf n)
=
\left(
I-\frac{i}{\hbar}\frac{\theta}{N}G_{\mathbf n}
+O\!\left(\frac{1}{N^2}\right)
\right)^N
$$

となる。

`N` を大きくしていくと、二次以上の項は消えていき、残るのは

$$
U(\theta,\mathbf n)
=
\lim_{N\to\infty}
\left(
I-\frac{i}{\hbar}\frac{\theta}{N}G_{\mathbf n}
\right)^N
$$

である。

ここで指数関数の定義

$$
e^A=\lim_{N\to\infty}\left(I+\frac{A}{N}\right)^N
$$

を使えば、

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,G_{\mathbf n}
\right)
$$

が出る。

したがって、回転演算子が指数関数になる理由は、

- 微小回転を一次まで書けること
- 有限回転がその積で作れること

の二つだけである。

---

したがって、問題は完全に

**「回転の生成子 `G_{\mathbf n}` は何か」**

に絞られる。

---

## 3. 古典回転を正しく作る量は何か

ここで古典力学を思い出す。

位置ベクトル

$$
\mathbf r=(x,y,z)
$$

を `z` 軸まわりに微小角 `\delta\phi` だけ回すと、

$$
\delta x=-y\,\delta\phi,\qquad
\delta y=x\,\delta\phi,\qquad
\delta z=0
$$

であった。

一方、古典角運動量

$$
\mathbf L=\mathbf r\times \mathbf p
$$

の `z` 成分は

$$
L_z=xp_y-yp_x
$$

である。

このとき古典力学では、微小変換はポアソン括弧で

$$
\delta f=\delta\phi\,\{f,L_z\}
$$

と書ける。  
実際、

$$
\{x,L_z\}=-y,\qquad
\{y,L_z\}=x,\qquad
\{z,L_z\}=0
$$

なので、

$$
\delta x=\delta\phi\,\{x,L_z\}=-y\,\delta\phi,\qquad
\delta y=\delta\phi\,\{y,L_z\}=x\,\delta\phi
$$

となり、回転そのものが再現される。

この意味で、古典角運動量は回転の生成子である。

同様に

- `L_x` は `x` 軸まわりの回転の生成子
- `L_y` は `y` 軸まわりの回転の生成子

である。

---

## 4. 量子力学では角運動量が生成子を引き継ぐ

量子力学では、古典のポアソン括弧の役割を交換子が引き継ぐ。

したがって、古典で回転の生成子だった角運動量は、量子でも回転の生成子として現れる。  
これを一般に

$$
\mathbf J=(J_x,J_y,J_z)
$$

と書く。

軌道角運動量もスピン角運動量も、回転の生成子という意味では同じ役割を果たす。  
したがって、方向 `\mathbf n` の回転生成子は

$$
J_{\mathbf n}=\mathbf n\cdot\mathbf J
$$

である。

ここで `\mathbf n=(n_x,n_y,n_z)` は単位ベクトルなので、

$$
J_{\mathbf n}=n_xJ_x+n_yJ_y+n_zJ_z
$$

は「その方向の角運動量成分」を意味する。

したがって、微小回転の生成子は

$$
G_{\mathbf n}=J_{\mathbf n}
$$

であり、有限回転は

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
$$

となる。

これが導きたかった式である。

---

## 5. なぜ `\mathbf n\cdot\mathbf J` なのか

この式が少し唐突に見える読者もいるので、言葉で確認しておく。

回転には

- 回転軸
- 回転角

の二つがある。  
角運動量も各軸方向に成分を持つ。

回転軸が `\mathbf n` のとき、その回転に効くのは角運動量ベクトル全部ではなく、**その軸方向の成分だけ** である。  
だから生成子は

$$
\mathbf n\cdot\mathbf J
$$

になる。

これは古典でも量子でも同じ考え方である。

---

## 6. スピン `1/2` ではどうなるか

スピン `1/2` では、角運動量演算子は

$$
J_i=S_i=\frac{\hbar}{2}\sigma_i
\qquad (i=x,y,z)
$$

である。

したがって

$$
J_{\mathbf n}
=
\mathbf n\cdot\mathbf J
=
\frac{\hbar}{2}\,\mathbf n\cdot\boldsymbol{\sigma}
$$

なので、

$$
U(\theta,\mathbf n)
=
\exp\!\left(
-\frac{i}{\hbar}\theta\,J_{\mathbf n}
\right)
=
\exp\!\left(
-i\frac{\theta}{2}\,\mathbf n\cdot\boldsymbol{\sigma}
\right)
$$

となる。

ここで初めて、`PHYSICS6.md` のスピン回転行列の式が自然に理解できる。

---

## 最後に一行で言うと

回転演算子が

$$
U(\theta,\mathbf n)=\exp\!\left(-\frac{i}{\hbar}\theta\,\mathbf n\cdot\mathbf J\right)
$$

となるのは、微小回転を積み重ねると指数関数になり、その微小回転の生成子が古典でも量子でも角運動量だからである。
