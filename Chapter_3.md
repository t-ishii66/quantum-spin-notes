# Chapter 3: 声を数にする

## Scene 1: Bobの提案

机の上で黒い球が静かに転がっている。  
Aliceが同じ場所を二回叩くと、二回とも **Yay!** が出た。

Bobがノートに書く。  
「この“声”を、そのまま数式に入れたい。まずは対応する変数を作ろう」

Charlieが確認する。  
「記号の使い分けは厳密にしよう。混ぜると破綻する」

Aliceが読み上げる。  
「`Yay` は値（変数の値）。`|Yay⟩` は状態ベクトル。見た目が似てても別物、ね」

## Physics Note 1: 記号の区別

この章では、次の区別を明示する。

- `|Yay⟩`, `|Oops⟩`: 状態ベクトル（ケット）
- `Yay`, `Oops`: 測定結果ラベル
- `m`: 測定値を表す数値変数

以後、結果ラベルと数値の対応を

$$
Yay \leftrightarrow +1,\qquad Oops \leftrightarrow -1
$$

と定める。すると、声は「数」として扱える。

## Scene 2: 測定を演算子で書く

Bobは続けて書く。  
「測定そのものを演算子にして、$\hat M$ と置こう」

そして、固有状態に対して

$$
\hat M|Yay\rangle=+1\,|Yay\rangle,\qquad
\hat M|Oops\rangle=-1\,|Oops\rangle
$$

と書いた。

Aliceが首をかしげる。  
「それで、一般の状態だとどうなるの？」

## Physics Note 2: 一般状態への作用

一般状態を

$$
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
$$

（この段階では $\alpha,\beta\in\mathbb R$）とすると、線形性より

$$
\hat M|\phi\rangle
=\alpha\hat M|Yay\rangle+\beta\hat M|Oops\rangle
=\alpha|Yay\rangle-\beta|Oops\rangle
$$

となる。

ここで重要なのは、$\hat M|\phi\rangle$ 自体は「測定後の1回の結果」ではなく、  
演算子 $\hat M$ が状態 $|\phi\rangle$ にどう作用するかを表す式だという点である。

## Scene 3: Charlieの提案

沈黙のあと、Charlieが言う。  
「左から $\langle\phi|$ をかけてみよう」

$$
\langle\phi|\hat M|\phi\rangle
$$

を計算すると（実係数の場合）、

$$
\langle\phi|\hat M|\phi\rangle=\alpha^2-\beta^2
$$

になる。

Aliceがつぶやく。  
「これ、何を意味してるの？」

## Physics Note 3: 平均値と確率の読み分け

- $\langle\phi|\hat M|\phi\rangle$ は測定値の**平均値**
- 確率そのものは（この段階の仮定として）

$$
P(Yay)=\alpha^2,\qquad P(Oops)=\beta^2,\qquad \alpha^2+\beta^2=1
$$

と読む。

このとき

$$
\langle\hat M\rangle
=(+1)P(Yay)+(-1)P(Oops)
=\alpha^2-\beta^2
$$

となり、上の計算と一致する。

## この章の要点

1. `|Yay⟩` と `Yay` は別物である。前者は状態、後者は結果ラベル（または対応する値）。  
2. 測定結果を数に落とすため、`Yay↔+1`, `Oops↔-1` の対応を導入した。  
3. 測定演算子 $\hat M$ の固有値方程式で、再測定の確定性を表現できる。  
4. $\langle\phi|\hat M|\phi\rangle$ は確率ではなく平均値であり、確率は $\alpha^2,\beta^2$ で与える。

Bobがノートを閉じる。  
「声を数にしたら、実験結果が計算とつながった」

Aliceは球を見つめる。  
「記号が増えたのに、前より意味は見えやすいかも」


代表的な観測結果は次のように整理できる（観測確率は試行回数を増やすと理論値へ近づく）。

<table border="1" cellspacing="0" cellpadding="6">
  <thead>
    <tr>
      <th>一回目と二回目の声</th>
      <th>一回目と二回目の叩く点の角度 θ</th>
      <th>観測確率</th>
      <th>理論値</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>同じ声</td>
      <td>0</td>
      <td>0.98</td>
      <td>cos²(θ/2) = 1.00</td>
    </tr>
    <tr>
      <td>同じ声</td>
      <td>π/4</td>
      <td>0.86</td>
      <td>cos²(θ/2) ≈ 0.85</td>
    </tr>
    <tr>
      <td>同じ声</td>
      <td>π/2</td>
      <td>0.53</td>
      <td>cos²(θ/2) = 0.50</td>
    </tr>
    <tr>
      <td>同じ声</td>
      <td>3π/4</td>
      <td>0.17</td>
      <td>cos²(θ/2) ≈ 0.15</td>
    </tr>
    <tr>
      <td>同じ声</td>
      <td>π</td>
      <td>0.02</td>
      <td>cos²(θ/2) = 0.00</td>
    </tr>
  </tbody>
</table>


$$
\Pr(\text{二回目が同じ声})=\cos^2\frac{\theta}{2},\qquad
\Pr(\text{二回目が反対の声})=1 - \cos^2\frac{\theta}{2}= \sin^2\frac{\theta}{2}
$$
