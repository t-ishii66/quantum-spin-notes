# 実験事実からパウリ行列を導く

> **シリーズ構成**: 本文書（PHYSICS_NOTE.md）→ [回転演算子](PHYSICS_NOTE2.md) → [ブロッホ球](PHYSICS_NOTE3.md) → [θ/2 の由来](PHYSICS_NOTE4.md) → [ベルの不等式](PHYSICS_NOTE5.md)

## この文書の方針

この文書は、パウリ行列 $\sigma_x, \sigma_y, \sigma_z$ を「便利な道具」として天下りに置くのではなく、実験事実から一歩ずつ導く。

出発点となる前提を整理しておこう。

1. ある種の粒子に磁場をかけると、進路が**ちょうど2本**に分かれる（シュテルン・ゲルラッハ実験）
2. 量子力学では、状態はベクトル、物理量はエルミート演算子で表される
3. 測定で値 $a$ が確定的に出る状態は、その演算子の固有値 $a$ に属する固有ベクトルである

途中でこの三つだけでは足りない場面が出てくる。たとえば「半々」を確率に翻訳するにはBorn則が要るし、状態空間として複素ベクトル空間を選ぶことも仮定の一つである。そうした追加の仮定は、使う場面でその都度はっきり示す。

---

## 全体の筋

流れは5段階ある。

1. **シュテルン・ゲルラッハ実験** → スピンの二値性を知る
2. **$z$ 方向の測定が二値** → 2次元空間と $\sigma_z$ が決まる
3. **$x$ 方向の測定が半々** → $\sigma_x$ の固有状態が決まる（位相の自由度が残る）→ 位相規約を選んで $\sigma_x$ が確定する
4. **$y$ 方向が必要** → 複素数が避けられず、 $\sigma_y$ が確定する
5. **交換関係の検証** → 3つの行列がスピン演算子であることが分かる

---

## 第1段階：シュテルン・ゲルラッハ実験

### 実験の概要

1922年、Otto Stern と Walther Gerlach は銀原子のビームを不均一磁場に通す実験を行った。この実験がスピンの発見につながる。

装置はこうなっている。

1. **原子源**：オーブンで銀を加熱し、蒸発した銀原子のビームを作る
2. **磁場領域**：ビームは、上下方向（ $z$ 方向）に強さが変わる磁場の中を通る
3. **スクリーン**：磁場を通過した原子がスクリーンに当たる

なぜ**不均一**磁場なのか。均一な磁場（どこでも同じ強さ）に小さな磁石を入れると、N極側とS極側に同じ大きさで逆向きの力がかかり、差し引きゼロになる。磁石はその場で回るだけで、動かない。つまりビームの進路は曲がらない。

実際の装置では、磁石の上側の極を尖ったくさび形、下側を平らな形にしてある。すると磁力線は上側で密に集中し、下側では疎に広がる。ビームが通る経路のあたりで見ると、少し上に行くほど磁場が強く、少し下に行くほど弱い。この密と疎の勾配があるために、小さな磁石のN極側とS極側で受ける力が釣り合わず、正味の力が残る。磁気モーメントの $z$ 成分が正なら磁力線が密な上側へ引かれ、負なら疎な下側へ押し出される。力の大きさは $z$ 成分の値に比例する。こうして原子の軌道を曲げ、スクリーン上の到達位置から内部状態を読み取る。

### 古典的な予想

銀原子が磁場中で力を受けるということは、内部に磁気モーメント——つまりその源となる角運動量——を持っているはずである。古典力学では、この角運動量の向きは空間の任意の方向を向きうる。したがって $z$ 成分は連続的な値を取り、スクリーン上には**縦に広がった連続的な帯**が現れるはずである。

### 実際の結果

ところが、スクリーンに現れたのは帯ではなく、はっきりと分離した**2つのスポット**だった。上側と下側の2点だけである。

これは次のことを意味する。

- 銀原子の内部角運動量の $z$ 成分は、連続的な値ではなく、**ちょうど2つの値**しか取らない
- 各原子は上か下かのどちらかに必ず振り分けられる。中間はない

この二値性は古典力学では説明できない。後に、これは銀原子の最外殻電子が持つ**スピン角運動量**（空間的な運動とは関係のない内部自由度に宿る角運動量）の性質だと理解された。

### 連続測定の実験

シュテルン・ゲルラッハ装置を複数つなげると、さらに重要な事実が分かる。

**実験A：同じ方向を2回**

$z$ 方向の装置でビームを2つに分ける。下側（ $-1$ ）のビームは壁でブロックして捨て、上側（ $+1$ ）のビームだけを取り出す。これをもう一度 $z$ 方向の装置に通す。結果は、**全粒子が上側に出る**。下側には1つも来ない。

つまり、 $z$ 方向で一度測って上側と確認した粒子を、もう一度 $z$ 方向で測ると、必ず上側になる。これが**再現性**である。

**実験B：異なる方向を測る**

$z$ 方向の装置で上側のビームを取り出し、次に $x$ 方向（水平方向）の装置に通す。すると、 $x$ 方向の上側と下側が**半々**で出る。

$z$ 方向で確定した粒子なのに、 $x$ 方向の結果は確率的になる。

**実験C：状態更新の確認**

実験Bの続きとして、 $x$ 方向で上側のビームだけを取り出し、もう一度 $z$ 方向の装置に通す。すると、 $z$ 方向の結果は再び**半々**に戻る。

最初の $z$ 測定で上側を選んだはずなのに、間に $x$ 測定を挟んだだけで $z$ の情報が失われている。標準的な量子論では、これは**測定による状態の更新**（ある方向の情報が別の方向の測定で上書きされる）として記述される。

### 実験事実のまとめ

| 事実 | 内容 |
|------|------|
| 二値性 | 各方向の測定で結果は $+1$ か $-1$ の2値だけ |
| 再現性 | 同方向の再測定で結果が一致する |
| 確率性 | 異方向の測定では結果が確率的になる（ $z$ 確定後に直交する $x$ を測ると半々） |
| 状態更新 | ある方向の測定を挟むと、別方向の情報が失われる |

---

## 第2段階： $z$ 方向の測定から $\sigma_z$ へ

### 実験事実から状態空間へ

シュテルン・ゲルラッハ実験で、 $z$ 方向の測定は2値（上側と下側）しか返さない。

ここから分かることは

- この内部自由度は $z$ 方向について2値しか返さない
- したがって状態空間は（少なくとも）2次元である

最小のモデルとして、2次元の**複素**ベクトル空間を採用する。これは仮定である——実験が教えてくれるのは「2値」という事実だけで、状態空間が複素ベクトル空間の構造を持つことや、なぜ実数ではなく複素数なのかは、ここでは天下り的に受け入れる。「最小のモデル」というのは、2値を説明するには最低2次元が必要で、それ以上の次元を持ち込んでも新しい測定値が増えないからである。

### 固有状態を置く

$z$ 測定で上側に出た粒子をもう一度 $z$ 方向で測ると、必ず上側になる。下側も同様に再現される。したがって

- $z$ 測定には2つの確定状態がある
- 一方が「必ず上（ $+1$ ）」、他方が「必ず下（ $-1$ ）」を返す

この2状態を $\vert {+z}\rangle$, $\vert {-z}\rangle$ と書く。両者は完全に区別可能なので直交し、確率1の状態なので正規化されている。

```math
\langle{+z}\vert {+z}\rangle = 1, \qquad
\langle{-z}\vert {-z}\rangle = 1, \qquad
\langle{+z}\vert {-z}\rangle = 0
```

ここで使っている $\langle \cdot \vert \cdot \rangle$ は内積——2つのベクトルがどれだけ似ているかを測る操作——である。普通のベクトルで考えると、同じ向きなら内積は最大、直角に交わるベクトルなら内積はゼロになる。状態ベクトルでも同じで、自分自身との内積が1（完全に同じ）、完全に区別できる状態との内積が0（まったく似ていない）になる。

### 測定演算子を作る

いま、状態は $\vert {+z}\rangle$ または $\vert {-z}\rangle$ のどちらかである。ここで、上向きに揃えた銀 $\vert {+z}\rangle$ を $z$ 方向の装置で測定することを考えよう。量子論では、この「装置で測定する」という操作を**演算子**という数学的対象で表す。

$z$ 方向の装置を演算子 $\hat{Z}$ と書くと、上向きの銀に装置を作用させた結果は

```math
\hat{Z}\vert {+z}\rangle = (+1)\vert {+z}\rangle
```

と表せる。左辺は「装置 $\hat{Z}$ を、上向きに揃った銀 $\vert {+z}\rangle$ に作用させる」こと。右辺は「測定値 $(+1)$ が得られ、測定後の状態は変わらず $\vert {+z}\rangle$ のまま」ということを意味する。下向きの場合も同様で

```math
\hat{Z}\vert {-z}\rangle = (-1)\vert {-z}\rangle
```

となる。このように、ある状態に演算子を作用させたとき、定数倍（測定値）×元の状態に戻る関係を**固有値方程式**と呼び、 $(+1)$, $(-1)$ を**固有値**、 $\vert {+z}\rangle$, $\vert {-z}\rangle$ を**固有状態**と呼ぶ。

この2つの固有状態と固有値を使うと、測定演算子を組み立てることができる。発想はこうである。まず $\vert {+z}\rangle\langle{+z}\vert$ は「状態の $\vert {+z}\rangle$ 成分だけを取り出す」射影子であった。これに固有値 $(+1)$ を重みとして掛ける。 $\vert {-z}\rangle$ 成分についても同様にして、両者を足し合わせると

```math
\hat{Z} = (+1)\vert {+z}\rangle\langle{+z}\vert + (-1)\vert {-z}\rangle\langle{-z}\vert
```

が得られる。これを**スペクトル分解**と呼ぶ。本当にこれが正しい演算子になっているか、固有状態に作用させて確かめよう。 $\vert {+z}\rangle$ に作用させると

```math
\hat{Z}\vert {+z}\rangle
= (+1)\vert {+z}\rangle\underbrace{\langle{+z}\vert {+z}\rangle}_{=1}
 + (-1)\vert {-z}\rangle\underbrace{\langle{-z}\vert {+z}\rangle}_{=0}
= (+1)\vert {+z}\rangle \quad\checkmark
```

同様に $\vert {-z}\rangle$ に作用させると

```math
\hat{Z}\vert {-z}\rangle
= (+1)\vert {+z}\rangle\underbrace{\langle{+z}\vert {-z}\rangle}_{=0}
 + (-1)\vert {-z}\rangle\underbrace{\langle{-z}\vert {-z}\rangle}_{=1}
= (-1)\vert {-z}\rangle \quad\checkmark
```

確かに132行目・138行目の固有値方程式が再現された。ここで内積の直交性（ $\langle{+z}\vert {-z}\rangle = 0$ ）が本質的に効いている。

### 行列表示

この2状態を計算基底に選ぶ。

```math
\vert {+z}\rangle = \begin{pmatrix}1\\0\end{pmatrix}, \qquad
\vert {-z}\rangle = \begin{pmatrix}0\\1\end{pmatrix}
```

すると $\hat{Z}$ の行列表示は

```math
\sigma_z =
\begin{pmatrix}
1 & 0 \\
0 & -1
\end{pmatrix}
```

である。これが最初のパウリ行列 $\sigma_z$ であり、「 $z$ 方向の測定で2値が出る」という事実をそのまま行列にしたものにすぎない。

### 任意の状態

ここで視点を切り替える。これまで見てきたシュテルン・ゲルラッハの実験では、多数の銀原子をビームとして流し、スクリーン上の統計的な分布から結果を読み取った。しかし量子論の核心は、**たった1つの銀原子**についても $\vert {+z}\rangle$, $\vert {-z}\rangle$ という状態ベクトルが意味を持つということである。統計量ではなく、個々の粒子が状態を持つ。

実験Bを思い出そう。 $z$ 方向で上側と確認した1つの銀原子を $x$ 方向で測ると、結果は $+1$ か $-1$ のどちらかになり、どちらが出るかは測定するまで分からなかった。この銀原子は $\vert {+x}\rangle$ でも $\vert {-x}\rangle$ でもない。かといって「本当はどちらかだが我々が知らないだけ」とも考えにくい——実験Cが示したように、 $x$ 方向の測定が $z$ 方向の情報を壊すからである（この「事前に決まっていたのではないか」という問いに最終的な決着をつけるのがベルの不等式であり、[PHYSICS_NOTE5.md](PHYSICS_NOTE5.md) で扱う）。量子論では、この状況を2つの基底状態の**重ね合わせ**として表現する。

2次元空間の基底が決まったので、1つの銀原子の任意の状態は

```math
\vert \psi\rangle = \alpha\vert {+z}\rangle + \beta\vert {-z}\rangle
= \begin{pmatrix}\alpha\\\beta\end{pmatrix}
```

と書ける。ここで $\alpha, \beta$ は複素数である。繰り返すが、これは「上側に行く銀と下側に行く銀が集団として混ざっている」のではない。**1つの銀原子**が、測定されるまで $\vert {+z}\rangle$ と $\vert {-z}\rangle$ の両方の性質を重ね合わせて持っている——それが量子力学的な状態の意味である。

ところで、基底ベクトル自身は正規化されていた（ $\langle{+z}\vert {+z}\rangle = 1$ 等）。一般の状態ベクトルについても同じ正規化条件

```math
\langle\psi\vert \psi\rangle = \vert \alpha\vert ^2 + \vert \beta\vert ^2 = 1
```

を課す。現時点ではこれは**規約**である。「なぜ1でなければならないのか」は、次の段階で測定結果の確率を読み取る方法（Born則）を導入したとき明らかになる—— $\vert \alpha\vert ^2$ と $\vert \beta\vert ^2$ がそれぞれの結果を得る確率になり、確率の総和は1だからである。

---

## 第3段階： $x$ 方向の測定から固有状態の形へ

### 実験事実

$z$ 方向で上側を選んだ粒子を、今度は $x$ 方向の装置に入れる。すると

- $x$ 方向の上と下が**半々**で出る

さらに

- $x$ で上を選んでもう一度 $x$ を測ると、必ず上になる
- しかしその後 $z$ を測ると、 $z$ の結果は半々に戻る

つまり $z$ と $x$ は同時には確定せず、 $x$ にも独自の2つの確定状態がある。

### $x$ の固有状態を $z$ 基底で表す

$x$ 方向にも2つの固有状態 $\vert {+x}\rangle$, $\vert {-x}\rangle$ がある。これらは同じ2次元空間の中に住んでいるので、 $z$ 基底で書けるはずである。

```math
\vert {+x}\rangle = a\vert {+z}\rangle + b\vert {-z}\rangle
```

実験Bの結果「 $\vert {+z}\rangle$ の銀原子を $x$ 方向の装置に通すと、 $+1$ と $-1$ が半々で出る」を数式にしたい。Born則によれば、ある状態が別の固有状態に見出される確率は、両者の内積の絶対値の2乗で与えられる。したがって「半々」という条件は

```math
\vert \langle{+x}\vert {+z}\rangle\vert ^2 = \frac{1}{2}
```

となる。 $\langle{+x}\vert {+z}\rangle = a^*$ なので $\vert a\vert ^2 = 1/2$ 。正規化 $\vert a\vert ^2 + \vert b\vert ^2 = 1$ から $\vert b\vert ^2 = 1/2$ も得られる。

したがって

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(e^{i\alpha}\vert {+z}\rangle + e^{i\beta}\vert {-z}\rangle\bigr)
```

の形になる。ここで $e^{i\alpha}$, $e^{i\beta}$ は何かというと、自乗して確率を求めたときに $\vert e^{i\alpha}\vert ^2 = 1$ となって消える係数——つまり確率に影響しない「飾り」にすぎない。こうした係数を位相因子と呼ぶ。

### 位相の自由度を数える

量子力学では、状態ベクトル全体に共通の位相 $e^{i\gamma}$ を掛けても物理は変わらない。この自由度を使って $e^{i\alpha} = 1$ と選ぶことができる。すると

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

のように、**相対位相** $e^{i\phi}$ だけが残る。

つまり「 $z$ から見て半々」という条件を満たす状態は無限に存在し、それらは相対位相 $\phi$ で区別される。

---

### 位相規約を選んで $\sigma_x$ を確定する

### $\phi$ の選択は物理的に何を意味するか

相対位相 $\phi$ が異なる状態は、 $z$ 測定では区別できない（どれも半々になる）。しかし別方向の測定をすれば区別できる。たとえば $\phi = 0$ の状態が $\vert {+x}\rangle$、 $\phi = \pi$ の状態が $\vert {-x}\rangle$ に対応する——どちらも $z$ 測定では半々だが、 $x$ 測定をすれば一方は必ず $+1$、他方は必ず $-1$ を返す。したがって $\phi$ は物理的に意味のある量である。

ここで $x$ 軸方向を定義するにあたって、位相規約を選ぶ。**$z$ 基底で書いたとき実数係数になる方向を $x$ と呼ぶ** ことにする。すなわち

```math
\phi = 0
```

を選ぶ。241行目の式に $\phi = 0$ を代入すると $e^{i \cdot 0} = 1$ なので

```math
\vert {+x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + \vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
```

となる。次に $\vert {-x}\rangle$ を求める。254行目で述べたように $\vert {-x}\rangle$ は $\phi = \pi$ に対応するので、同じ式に $\phi = \pi$ を代入すると $e^{i\pi} = -1$ から

```math
\vert {-x}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle - \vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
```

が得られる。直交条件 $\langle{-x}\vert {+x}\rangle = \frac{1}{2}(1 \cdot 1 + (-1) \cdot 1) = 0$ も確かに満たされている。

### なぜこれが「規約」なのか

「 $\phi = 0$ を選ぶ」とは、3次元空間の中で $z$ 軸に対して垂直な一方向を、 $x$ 軸と名付けるということである。 $z$ 軸だけでは水平面内の向きは決まらないので、どこを $x$ と呼ぶかは規約として選ばなければならない。 $\phi = 0$ はその選択であり、物理法則ではない。

### $\sigma_x$ を書き下す

$\vert {+x}\rangle$ が固有値 $+1$ 、 $\vert {-x}\rangle$ が固有値 $-1$ を持つ演算子を作る。

```math
\hat{X} = (+1)\vert {+x}\rangle\langle{+x}\vert + (-1)\vert {-x}\rangle\langle{-x}\vert 
```

これを $z$ 基底で行列にする。

```math
\vert {+x}\rangle\langle{+x}\vert 
= \frac{1}{2}\begin{pmatrix}1\\1\end{pmatrix}(1\;1)
= \frac{1}{2}\begin{pmatrix}1&1\\1&1\end{pmatrix}
```

```math
\vert {-x}\rangle\langle{-x}\vert 
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
\sigma_x\,\vert {+x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= +1 \cdot \vert {+x}\rangle \quad\checkmark
```

```math
\sigma_x\,\vert {-x}\rangle
= \begin{pmatrix}0&1\\1&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-1\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\1\end{pmatrix}
= -1 \cdot \vert {-x}\rangle \quad\checkmark
```

---

## 第4段階： $y$ 方向には複素数が必要

### なぜ $y$ は $x$ と同じではないのか

3次元空間には $z$ に垂直な方向が2つ（ $x$ と $y$ ）ある。 $z$ から見れば $x$ も $y$ も対等で、どちらも

- $\vert {+z}\rangle$ を測ると半々

を与える。ならば $x$ と $y$ は同じものではないか？

答えは否である。 $x$ と $y$ は**異なる方向**の測定なので、**異なる固有状態**を持たなければならない。しかし「 $z$ から見て半々」という条件だけでは $\vert a\vert ^2 = \vert b\vert ^2 = 1/2$ しか言えず、差は相対位相にしかない。

$x$ はすでに $\phi = 0$ を使った。 $y$ が $x$ と異なるなら、 $\phi \neq 0$ でなければならない。

### $y$ を $\phi = \pi/2$ に対応させる

$x$ 軸から 90 度回転した方向が $y$ 軸である。ここで、状態ベクトルの相対位相 $\phi$ が実空間の方位角にそのまま対応すると仮定する。この対応は自然に見えるが、実は回転演算子と $\mathrm{SU}(2)$ 表現を使って初めてきちんと正当化される（[PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で導く）。いまはこの対応を認めて先に進もう。

$x$ を $\phi = 0$ に取ったので、 $y$ は

```math
\phi = \frac{\pi}{2}
```

に対応する。241行目の式に $\phi = \pi/2$ を代入する。 $e^{i\pi/2} = i$ なので

```math
\vert {+y}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + i\vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
```

同様に $\vert {-y}\rangle$ は $\phi = \pi/2 + \pi = 3\pi/2$ に対応する。 $e^{i \cdot 3\pi/2} = -i$ なので

```math
\vert {-y}\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle - i\vert {-z}\rangle\bigr)
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
```

となる。直交条件も確かめておく。 $\langle{-y}\vert {+y}\rangle = \frac{1}{2}(1 \cdot 1 + i \cdot i) = \frac{1}{2}(1 - 1) = 0$ 。

### なぜ $i$ が出るのか

$i$ は突然の思いつきではない。一般の「 $z$ から見て半々」の状態は

```math
\vert \psi(\phi)\rangle = \frac{1}{\sqrt{2}}\bigl(\vert {+z}\rangle + e^{i\phi}\vert {-z}\rangle\bigr)
```

であり、 $\phi$ は赤道上の方位角だった。 $x$ が $\phi = 0$ なら、そこから 90 度回った $y$ は $\phi = \pi/2$ であり

```math
e^{i\pi/2} = i
```

になるだけである。

### 実数では足りない理由

もし係数を実数に限ると、相対位相は $+1$ か $-1$ しかない。 $+1$ はすでに $x$ が使っている。 $-1$ を使うと $\vert {-x}\rangle$ と同じ状態になってしまう。

つまり実数だけでは、 $z$ に垂直な独立方向を1つしか表せない。もう少し正確に言えば、実数の $2 \times 2$ 行列で作れる traceless エルミート行列は $\sigma_z$ と $\sigma_x$ の実数係数の組み合わせに限られ、第三の独立な成分 $\sigma_y$ を持てない。3方向の測定を2次元で表すには、複素数——つまり $i$ ——がどうしても必要になる。

### 測定統計の検算

この $\vert {+y}\rangle$, $\vert {-y}\rangle$ が実験事実と矛盾しないかを確かめる。

$\vert {+x}\rangle$ を $y$ で測る：

```math
\langle{+y}\vert {+x}\rangle
= \frac{1}{\sqrt{2}}(1,\,-i) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\1\end{pmatrix}
= \frac{1}{2}(1 - i)
```

```math
\vert \langle{+y}\vert {+x}\rangle\vert ^2
= \left\vert \frac{1-i}{2}\right\vert ^2
= \frac{1+1}{4}
= \frac{1}{2} \quad\checkmark
```

$\vert {+y}\rangle$ を $x$ で測る：

```math
\langle{+x}\vert {+y}\rangle
= \frac{1}{\sqrt{2}}(1,\,1) \cdot \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{2}(1 + i)
```

```math
\vert \langle{+x}\vert {+y}\rangle\vert ^2
= \left\vert \frac{1+i}{2}\right\vert ^2
= \frac{1}{2} \quad\checkmark
```

$\vert {+y}\rangle$ を $z$ で測る：

```math
\vert \langle{+z}\vert {+y}\rangle\vert ^2
= \left\vert \frac{1}{\sqrt{2}}\right\vert ^2
= \frac{1}{2} \quad\checkmark
```

$x$, $y$, $z$ のどの2方向を選んでも、一方の固有状態を他方で測れば半々になる。この対称性は、 $y$ を $\phi = \pi/2$ に取る選択が実験と整合することを示している。

### $\sigma_y$ を書き下す

$\vert {+y}\rangle$ が固有値 $+1$ 、 $\vert {-y}\rangle$ が固有値 $-1$ を持つ演算子を作る。

```math
\hat{Y} = (+1)\vert {+y}\rangle\langle{+y}\vert + (-1)\vert {-y}\rangle\langle{-y}\vert 
```

$z$ 基底で各項を計算する。

```math
\vert {+y}\rangle\langle{+y}\vert 
= \frac{1}{2}\begin{pmatrix}1\\i\end{pmatrix}(1\;{-i})
= \frac{1}{2}\begin{pmatrix}1&-i\\i&1\end{pmatrix}
```

```math
\vert {-y}\rangle\langle{-y}\vert 
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
\sigma_y\,\vert {+y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-i^2\\i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}1\\i\end{pmatrix}
= +1 \cdot \vert {+y}\rangle \quad\checkmark
```

```math
\sigma_y\,\vert {-y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}-(-i)(-i)\\i\cdot 1 + 0\end{pmatrix}
```

もう少し丁寧にやる。

```math
\sigma_y\,\vert {-y}\rangle
= \begin{pmatrix}0&-i\\i&0\end{pmatrix}\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}0\cdot 1 + (-i)(-i)\\i\cdot 1 + 0\cdot(-i)\end{pmatrix}
= \frac{1}{\sqrt{2}}\begin{pmatrix}i^2\\i\end{pmatrix}
```

ここで $(-i)(-i) = i^2 = -1$ なので

```math
= \frac{1}{\sqrt{2}}\begin{pmatrix}-1\\i\end{pmatrix}
= -\frac{1}{\sqrt{2}}\begin{pmatrix}1\\-i\end{pmatrix}
= -1\cdot\vert {-y}\rangle \quad\checkmark
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

3つのパウリ行列の間の交換関係を直接計算してみよう。交換子（commutator）とは $[A, B] = AB - BA$ のことである。

まず $[\sigma_x, \sigma_y]$ を計算する。

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

である。ここで $\epsilon_{ijk}$ は完全反対称テンソル（レヴィ＝チヴィタ記号）で、添字の入れ替えに対する符号を表す。具体的には、 $i, j, k$ を $1, 2, 3$（それぞれ $x, y, z$）として

- $\epsilon_{123} = \epsilon_{231} = \epsilon_{312} = +1$ （巡回的な順序）
- $\epsilon_{213} = \epsilon_{132} = \epsilon_{321} = -1$ （隣接2つを入れ替えると符号が反転）
- 添字に重複がある場合はすべて $0$（例: $\epsilon_{112} = 0$ ）

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

となる。これは**角運動量の交換関係**そのものである。

なぜこの交換関係が重要なのか——つまり、これを満たすことがなぜ「角運動量である」ことの証明になるのかは、次の文書 [PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) で一般的な回転演算子を導き、[PHYSICS_NOTE4.md](PHYSICS_NOTE4.md) で詳しく論じる。

ここでは結論だけ述べておく。3つのパウリ行列は

- 実験事実（二値測定、半々の統計）から形が決まる
- その形が角運動量の交換関係を自動的に満たす
- しかも2次元では、この交換関係を満たす表現は本質的にこれだけである（ $\mathrm{SU}(2)$ の2次元既約表現の一意性）

という三重の意味で、スピン 1/2 の演算子として確定する。

---

## まとめ：何が実験事実で、何が規約か

導出の中で使ったものを整理しておく。

### 実験事実（変えられない）

- 各方向の測定で結果が2値（ $+1$ と $-1$ ）
- 同方向の再測定で結果が再現する
- 直交する異方向の測定で確率が半々になる（一般の角度では $\cos^2(\theta/2)$ ）
- 一方の測定を挟むと他方の情報が失われる

### 規約（別の選び方もあり得る）

- $\vert {+z}\rangle = (1,0)^T$, $\vert {-z}\rangle = (0,1)^T$ という基底の取り方
- $x$ 方向の固有状態を実数係数で書く（ $\phi = 0$ ）
- 右手系の約束で $y$ は $x$ から反時計回り 90 度（ $\phi = \pi/2$ ）——相対位相と実空間の方位角の対応は [PHYSICS_NOTE2.md](PHYSICS_NOTE2.md) の回転演算子で裏付けられる

### 導出された結果

- $\sigma_z, \sigma_x, \sigma_y$ の行列形
- $S_i = \hbar\sigma_i/2$ が角運動量の交換関係を満たすこと
- 2次元既約表現の一意性により、これがスピン 1/2 の唯一の表現であること

---

## 全体の論理構造（振り返り）

```
シュテルン・ゲルラッハ実験：ビームが2本に分かれる
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

最小限の量子力学的な枠組み（複素ベクトル空間、Born則など）を受け入れると、実験事実が行列の形を絞り、規約が残りの自由度を固定し、交換関係がスピンとの同定を保証する——パウリ行列は天から降ってきたのではなく、実験に導かれて自然に決まるのである。

---

**次の文書**: [PHYSICS_NOTE2.md — 回転演算子の導出](PHYSICS_NOTE2.md) では、この交換関係がなぜ回転と結びつくのかを一般的に導く。
