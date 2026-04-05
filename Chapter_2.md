# Chapter 2: The Rules of the Sphere

## Scene 2-1: 角度で整理する

次の日、三人は黒い球を机の上に置き、ノートを開いた。  
Chapter 1 で見えた規則を、今度は「角度」で整理するためだ。

Bobが言う。  
「同じ場所か反対側か、だけじゃ足りない。中間をちゃんと測ろう」

Charlieが分度器を取り出す。  
「1回目に叩いた点を基準方向 $n$ として、2回目を角度 $\theta$ だけずらして叩く」

Aliceは記録係になった。  
角度を変え、何十回も、何百回も叩く。

夜遅く、表の形が見えてきた。

- 同じ声が出る割合は、$\theta=0$ で最大
- 反対の声が出る割合は、$\theta=\pi$ で最大
- 途中の角度では連続的に変化

Aliceが言う。  
「これ、気分じゃない。角度で決まってる」

## Physics Note 2-1: 角度依存の観測則

この章で固定する実験則は次の2式。

```math
\Pr(\text{同じ声})=\cos^2\frac{\theta}{2},\qquad
\Pr(\text{異なる声})=\sin^2\frac{\theta}{2}
```
ここで $\theta$ は「1回目と2回目の叩く方向の角度差」。

---

## Scene 2-2: 2つだけでは足りない

Aliceは表を眺めながら首をかしげた。  
「でも、状態が本当に `|Yay⟩` か `|Oops⟩` の2つだけなら、中間角で半端な確率が出るのは変じゃない？」

Bobがうなずく。  
「だから“混ざり具合”を持つ状態が必要なんだと思う」

Charlieは式を書いた。

```math
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
```
「これを一般状態として仮定して、観測確率を再現できるか試す」

Aliceが笑う。  
「つまり、まずモデルを作って、実験と突き合わせるんだね」

## Physics Note 2-2: 重ね合わせの導入

この段階では、状態を次の形で書けると仮定する。

```math
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
```
ここでのポイントは、状態が `Yay` と `Oops` のどちらか一方だけでなく、  
2つの基底状態の重ね合わせとして表せる、ということ。  
この章ではまず $\alpha,\beta$ を実数として扱う。  
例えば

```math
\alpha=1,\ \beta=0 \Rightarrow |\phi\rangle=|Yay\rangle,\qquad
\alpha=0,\ \beta=1 \Rightarrow |\phi\rangle=|Oops\rangle
```
となるので、2つの極端な状態を含む一般形として使える。  
ただし「$\alpha,\beta$ は実数で十分」というのは現段階の仮定にすぎない。  
実験事実と辻褄が合わなければ、後で複素数へ拡張する。

---

## Scene 2-3: 係数を実験で決める

Bobは言った。  
「じゃあ次は、実際の統計を使ってこの係数の意味を確かめよう」

Charlieが手順を確認する。  
「1回目で状態をそろえて、2回目を角度 $\theta$ だけずらして叩く。  
そのとき“同じ声 / 異なる声”の割合を取る」

Aliceはうなずいた。  
「つまり、この表が係数の当てはまりを決める材料になるんだね」

Charlie達は条件を固定して測定した。  
「一回目で状態をそろえ、二回目を角度 $\theta$ だけずらして叩く」  
その結果、次の表が得られた。

<table border="1" cellspacing="0" cellpadding="6">
  <thead>
    <tr>
      <th>一回目と二回目の声</th>
      <th>角度 θ</th>
      <th>Alice達の観測確率（例）</th>
      <th>経験則</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>同じ声</td><td>0</td><td>0.98</td><td>cos²(θ/2)=1.00</td></tr>
    <tr><td>同じ声</td><td>π/4</td><td>0.86</td><td>cos²(θ/2)≈0.85</td></tr>
    <tr><td>同じ声</td><td>π/2</td><td>0.53</td><td>cos²(θ/2)=0.50</td></tr>
    <tr><td>同じ声</td><td>3π/4</td><td>0.17</td><td>cos²(θ/2)≈0.15</td></tr>
    <tr><td>同じ声</td><td>π</td><td>0.02</td><td>cos²(θ/2)=0.00</td></tr>
    <tr><td>異なる声</td><td>0</td><td>0.02</td><td>sin²(θ/2)=0.00</td></tr>
    <tr><td>異なる声</td><td>π/4</td><td>0.14</td><td>sin²(θ/2)≈0.15</td></tr>
    <tr><td>異なる声</td><td>π/2</td><td>0.47</td><td>sin²(θ/2)=0.50</td></tr>
    <tr><td>異なる声</td><td>3π/4</td><td>0.83</td><td>sin²(θ/2)≈0.85</td></tr>
    <tr><td>異なる声</td><td>π</td><td>0.98</td><td>sin²(θ/2)=1.00</td></tr>
  </tbody>
</table>

Bobは表を見て言った。  
「ここで素朴な候補は2つある。  
`確率そのものを係数にする` なら
```math
\alpha=\cos^2\frac{\theta}{2},\quad \beta=\sin^2\frac{\theta}{2}
```
だし、  
`確率は係数の二乗で読む` なら
```math
\alpha=\cos\frac{\theta}{2},\quad \beta=\sin\frac{\theta}{2}
```
になる」

Aliceが言う。  
「私なら前者にしちゃいそう。表の数値と見た目が同じだから」

Charlieはうなずきつつ、付け足した。  
「その直感は自然。  
ただ、どっちを採るかは“この先の式と全部つながるか”で決めるべきだ」

Bobがまとめる。  
「ここでは候補として両方ノートに残そう。  
後で期待値や再測定の計算と突き合わせて、辻褄の合う方を採用する」

Charlieが暫定メモを書いた。  
「現時点では、角度依存に対して次の形が有力」

```math
\alpha(\theta)\approx\cos\frac{\theta}{2},\qquad
\beta(\theta)\approx\sin\frac{\theta}{2}
```
Aliceは笑った。  
「つまり、ここではまだ“仮説勝負”ってことだね」

## Physics Note 2-3: この段階での係数の扱い

この章では、次の立場にとどめる。

- 状態は重ね合わせで書く: $|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle$
- 係数 $\alpha,\beta$ の候補は、実験表と今後の計算整合性で比較する
- 候補A: $\alpha=\cos^2(\theta/2),\ \beta=\sin^2(\theta/2)$
- 候補B: $\alpha=\cos(\theta/2),\ \beta=\sin(\theta/2)$

ここでは「係数をどう定義すると実験を再現し、かつ後の式と矛盾しないか」をこれから検証する段階に置く。  
確率解釈の体系化（Born則の厳密な位置づけ）は次章以降で行う。

---

## Physics Note 2-4: この章で固定したルール

Chapter 2 で固定できたのは次の3点。

1. **角度則**  
角度差 $\theta$ に対して、同じ声/異なる声の割合が `cos²(θ/2), sin²(θ/2)` に従う。

2. **重ね合わせ表現**  
状態は
```math
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle
```
の形で書くのが有効である。

3. **係数候補の比較方針**  
`α,β` の取り方は実験表と整合する条件で決める。  
候補A（`cos²,sin²`）と候補B（`cos,sin`）のどちらが一貫するかは、次章の演算子計算で判定する。

## この章で手に入れたもの

1. 球の観測統計は角度差 $\theta$ で決まる。  
2. 中間角の確率を記述するには、2状態の重ね合わせが必要になる。  
3. 係数 $\alpha,\beta$ は実験データと整合するように決める必要がある。  
4. `\alpha=\cos^2(\theta/2),\beta=\sin^2(\theta/2)` と `\alpha=\cos(\theta/2),\beta=\sin(\theta/2)` の2候補を立てた。  
5. 次章では測定を演算子言語で書き、どの係数解釈が矛盾なくつながるかを検証する。
