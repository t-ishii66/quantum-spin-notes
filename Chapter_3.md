# Chapter 3: Vectors and States

## Scene 3-1: 記号を分ける

夜、三人は Chapter 2 の表を見ながら、同じところで止まっていた。  
規則は見えた。だが、式として運ぶ道具がまだ粗い。

Bobが言う。  
「`Yay!` と `Oops!` をそのまま文章で追うのは限界だ。  
ここからは、結果と状態を別の記号で管理しよう」

Aliceがノートに二列を書く。

- 結果ラベル: `Yay`, `Oops`
- 状態ベクトル: `|Yay\rangle`, `|Oops\rangle`

Charlieがうなずいた。  
「見た目は似てるけど別物。そこを混ぜると全部崩れる」

Bobが前章のページを指す。  
「前の章で、係数 $\alpha,\beta$ は実験表に合わせて当てる形が見えた。  
この章では、その係数を“いったん既知の記号”として使って計算の道具を整える」

## Physics Note 3-1: 何を何で表すか

この章で使う最小の記号は次の通り。

- `|Yay_n\rangle, |Oops_n\rangle`: 方向 $n$ 測定の固有状態
- `\hat M_n`: 方向 $n$ を叩く測定操作（演算子）
- `a,b`: その測定で得る2つの測定値（実数、$a\neq b$）

したがって固有値方程式は

$$
\hat M_n|Yay_n\rangle=a|Yay_n\rangle,\qquad
\hat M_n|Oops_n\rangle=b|Oops_n\rangle
$$

となる。

この式の意味:

1. 測定値として $a$ か $b$ が得られる。  
2. 固有状態に対して同じ測定を繰り返すと、結果は再現される。

---

## Scene 3-2: 一般状態に作用させる

Aliceが尋ねる。  
「固有状態じゃないときは？」

Bobは白紙に書いた。

$$
|\phi_n\rangle=\alpha|Yay_n\rangle+\beta|Oops_n\rangle
$$

Charlieが続ける。  
「これに $\hat M_n$ を作用させる」

$$
\hat M_n|\phi_n\rangle
=\alpha a|Yay_n\rangle+\beta b|Oops_n\rangle
$$

Aliceは少し考えてから言う。  
「つまり、測定は“混ざり方”を値つきで押し出してる感じ？」

Bobが笑う。  
「いい言い方だね」

## Physics Note 3-2: 線形性と展開

上式は線形性

$$
\hat M_n(c_1|u\rangle+c_2|v\rangle)=c_1\hat M_n|u\rangle+c_2\hat M_n|v\rangle
$$

から直接出る。  
この段階では、測定後の単発結果を言っているのではなく、演算子が状態にどう作用するかを言っている。

---

## Scene 3-3: Charlieの一手

沈黙のあと、Charlieが言った。  
「左からブラをかけてみよう。平均値が見える」

$$
\langle\phi_n|\hat M_n|\phi_n\rangle
$$

Bobが計算する。直交規格化

$$
\langle Yay_n|Yay_n\rangle=1,\quad
\langle Oops_n|Oops_n\rangle=1,\quad
\langle Yay_n|Oops_n\rangle=0
$$

を使うと

$$
\langle\phi_n|\hat M_n|\phi_n\rangle
=a|\alpha|^2+b|\beta|^2
$$

Aliceが顔を上げる。  
「これ、確率そのもの？」

Charlieが首を振る。  
「これは平均値。確率とは別に読む」

## Physics Note 3-3: 平均値と確率の切り分け

この章の読み分け:

- $\langle\phi_n|\hat M_n|\phi_n\rangle$ は測定値の平均
- 確率は Born則（要請）で与える

$$
P(a)=|\alpha|^2,\qquad P(b)=|\beta|^2,\qquad
|\alpha|^2+|\beta|^2=1
$$

このとき平均値は

$$
\langle\hat M_n\rangle=aP(a)+bP(b)
$$

となり、上の式と一致する。

---

## Scene 3-4: 何が前進したか

Aliceはノートを閉じた。  
「Chapter 2 では“規則がある”までだった。  
今日は“その規則を計算で運べる形”になった感じ」

Bobが言う。  
「うん。次はこの状態を幾何として見たい。  
角度だけじゃなく、まだ見えてない自由度も含めて」

Charlieはページの端に小さく書いた。

**Bloch Sphere: $(\theta,\phi)$**

「次章はここだ」

## この章で手に入れたもの

1. 状態ラベルと結果ラベルを明確に分離した。  
2. 測定操作を `\hat M_n` として定義し、固有値方程式で書いた。  
3. 一般状態への作用を線形性で展開した。  
4. 期待値 `\langle\phi_n|\hat M_n|\phi_n\rangle` を導出した。  
5. 期待値と確率（Born則）を切り分けて整理した。  
6. 次章の Bloch 球導入に必要な記法をそろえた。
