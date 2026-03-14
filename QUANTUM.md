# QUANTUM notes

## 目的
- 射影測定（projective measurement）とボルン則（Born rule）を、物語本文とは独立に整理する。
- 「何が定義で、何が仮定で、何が実験で支えられているか」を明確にする。

## 1. 最小設定（2準位）

基底状態を

$$
|Yay\rangle,\quad |Oops\rangle
$$

とする。一般状態は

$$
|\psi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
$$

で表す（一般には $\alpha,\beta\in\mathbb{C}$）。

## 2. 射影測定とは何か

方向 $n$ の2値測定を考える。対応する射影演算子を

$$
P_n^{Yay}=|Yay_n\rangle\langle Yay_n|,\qquad
P_n^{Oops}=|Oops_n\rangle\langle Oops_n|
$$

とおく。

要請:

$$
P_n^{Yay}+P_n^{Oops}=I,\qquad
P_n^{Yay}P_n^{Oops}=0
$$

意味:
- 完備性: 結果は Yay/Oops のどちらかで尽くされる。
- 直交性: 同時に両方の結果は起きない。

具体的に、状態を $n$ 基底で

$$
|\phi\rangle=a|Yay_n\rangle+b|Oops_n\rangle
$$

と書くと、射影は

$$
P_n^{Yay}|\phi\rangle
=|Yay_n\rangle\langle Yay_n|
\left(a|Yay_n\rangle+b|Oops_n\rangle\right)
=a|Yay_n\rangle
$$

となり、Yay成分だけを取り出す。同様に

$$
P_n^{Oops}|\phi\rangle=b|Oops_n\rangle
$$

である。

したがって

$$
(P_n^{Yay}+P_n^{Oops})|\phi\rangle
=a|Yay_n\rangle+b|Oops_n\rangle
=|\phi\rangle
$$

が任意の $|\phi\rangle$ で成り立つため、

$$
P_n^{Yay}+P_n^{Oops}=I
$$

となる。

## 3. ボルン則（この段階では基本仮定）

状態 $|\psi\rangle$ で測定したときの確率を

$$
\Pr(Yay|n)=\langle\psi|P_n^{Yay}|\psi\rangle,\qquad
\Pr(Oops|n)=\langle\psi|P_n^{Oops}|\psi\rangle
$$

で与える。これがボルン則。

この規則を採用すると

$$
\Pr(Yay|n)+\Pr(Oops|n)=1
$$

が自動的に成り立つ（完備性より）。

## 4. なぜ「二乗」なのか

2準位の単純化で

$$
|\psi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
$$

なら、$z$ 基底で

$$
\Pr(Yay)=|\alpha|^2,\qquad \Pr(Oops)=|\beta|^2
$$

となる。

ポイント:
- これは「確率 = 振幅の絶対値二乗」というルール。
- 本書の導入段階では仮定として置く。
- ただし仮定は恣意的ではなく、実験統計（角度依存、干渉、再現性）を整合的に記述する最小規則として採用する。

## 5. 測定後状態（射影更新）

測定で Yay が出たなら

$$
|\psi\rangle\to\frac{P_n^{Yay}|\psi\rangle}
{\sqrt{\langle\psi|P_n^{Yay}|\psi\rangle}}
=|Yay_n\rangle
$$

Oops なら同様に $|Oops_n\rangle$ へ更新する。

意味:
- 測定は「値を読む操作」だけではない。
- 測定は状態を更新する（同じ軸で再測定すると同じ結果が出る理由）。

## 6. 本文での説明方針メモ

- まず実験事実を置く（同軸で再現、反対軸で反転、角度依存）。
- 次に射影演算子を導入する（記述の器）。
- 最後にボルン則を明示し、「ここは仮定だが実験で支持される」と書く。
- 初学者には「振幅」と「確率」を混同させない。

## 7. 差し込み用の短文

- 「この章では、確率が振幅の二乗で与えられるという規則（ボルン則）を基本仮定として採用する。」
- 「仮定とはいえ任意ではない。観測統計を最小の形で再現するために必要な規則である。」

## 8. 本文展開の推奨順序（測定公理まで）

### Step 1: 重ね合わせと規格化

まず状態を

$$
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
$$

と書く。基底の内積は

$$
\langle Yay|Oops\rangle=0,\qquad
\langle Yay|Yay\rangle=\langle Oops|Oops\rangle=1
$$

で、状態の規格化は

$$
\langle\phi|\phi\rangle=1
$$

とする。

### Step 2: 観測量を演算子で表す

物理量（観測量）を演算子 $A$ で表す。  
測定値が実数になるよう、$A$ はエルミート演算子（$A=A^\dagger$）を要請する。

### Step 3: 固有値と固有状態

$$
A|a_i\rangle=a_i|a_i\rangle
$$

を満たす $a_i$ が測定で得る値、$|a_i\rangle$ が対応する状態。  
エルミート性により $a_i$ は実数になる。

### Step 4: ボルン則

状態 $|\phi\rangle$ で $A$ を測るとき、結果 $a_i$ の確率は

$$
p_i=|\langle a_i|\phi\rangle|^2
$$

で与える（基本要請）。

### Step 5: 射影測定と状態更新

射影演算子

$$
P_i=|a_i\rangle\langle a_i|
$$

を用いると

$$
p_i=\langle\phi|P_i|\phi\rangle
$$

で、結果 $a_i$ が出た直後の状態は

$$
|\phi\rangle\to\frac{P_i|\phi\rangle}{\sqrt{p_i}}
$$

となる。

### Step 6: 可換性と同時測定可能性

2つの観測量 $A,B$ について

$$
[A,B]=AB-BA
$$

を考える。

- $[A,B]=0$: 共通固有基底を持ち、同時に確定させられる。
- $[A,B]\neq0$: 測定順序で結果統計が変わりうる（量子らしさの中核）。

## 9. 章に入れると効果的な一文

- 「状態ベクトルは“何が起きるか”の一覧ではなく、“各測定にどう応答するか”を圧縮した記述である。」
- 「エルミート演算子は、測定値が実数であることを保証するための数学的器である。」
- 「ボルン則はこの段階では要請だが、以後の実験事実を通じてその妥当性が検証される。」
