# Chapter 2: The Rules of the Sphere

前章では、球を同じ軸で叩けば結果が再現することを確認した。しかし、まだ最も重要な問いが残っている。**異なる軸**で叩いたら、何が起きるのか。

---

## 異なる軸の測定

三人は翌日、分度器を持ち出して実験を始めた。

手順はこうだ。まず $z$ 軸（上下）を挟んで叩き、球の状態を確定させる。たとえば **Yay!**（$+1$）が出たとする。前章の再現性により、この直後に球は $\vert +z \rangle$ にある。

次に、 $z$ 軸から角度 $\theta$ だけ傾いた別の軸 $n$ を選び、その軸の対蹠2点を挟んで叩く。

結果は驚くべきものだった。同じ軸なら必ず同じ声が返ってくるはずなのに、別の軸では **Yay!** のときも **Oops!** のときもある。しかも、何回やっても同じ結果にはならず、ばらつく。

「壊れたんじゃないの？」と Bob が言ったが、Alice は首を振った。何十回、何百回と繰り返すうちに、ばらつきの中に規則が見えてきたからだ。

---

## 角度と確率

Alice が記録した統計を表にまとめると、次のようになった。

$z$ 軸で $+1$ が出た直後に、角度 $\theta$ だけ傾いた軸 $n$ で測定する。

<table border="1" cellspacing="0" cellpadding="6">
  <thead>
    <tr>
      <th>角度 θ</th>
      <th>n 軸で +1 が出る割合</th>
      <th>n 軸で −1 が出る割合</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>0</td><td>1.00</td><td>0.00</td></tr>
    <tr><td>π/4</td><td>0.85</td><td>0.15</td></tr>
    <tr><td>π/2</td><td>0.50</td><td>0.50</td></tr>
    <tr><td>3π/4</td><td>0.15</td><td>0.85</td></tr>
    <tr><td>π</td><td>0.00</td><td>1.00</td></tr>
  </tbody>
</table>

角度 $\theta = 0$ は同じ軸だから、前章の再現性どおり確率 $1$ で同じ声になる。$\theta = \pi$ は反対向きだから、これも前章の反転規則どおりである。問題はその中間で、確率が角度に応じて連続的に変化している。

Charlie がこの表に三角関数を当てはめた。

```math
P(+1) = \cos^2\frac{\theta}{2}, \qquad P(-1) = \sin^2\frac{\theta}{2}
```

検算してみよう。 $\theta = 0$ なら $\cos^2 0 = 1$ 、$\theta = \pi$ なら $\cos^2(\pi/2) = 0$ 。中間の $\theta = \pi/2$ なら $\cos^2(\pi/4) = 1/2$ 。すべて表と一致する。さらに

```math
\cos^2\frac{\theta}{2} + \sin^2\frac{\theta}{2} = 1
```

だから、確率の合計も常に $1$ になる。

これが球の**角度則**である。

---

## なぜ θ/2 なのか

ここで自然な疑問が生じる。2つの軸のなす角は $\theta$ なのに、なぜ確率には $\theta/2$ が現れるのか。

この問いへの完全な答えは、ブロッホ球の幾何学を導入する第4章で得られる。球の状態を球面上の点として表すと、球面上の「幾何学的な角度」と確率に現れる「状態空間の角度」の間にちょうど2倍の関係があることが見える。今の段階では、$\theta/2$ は実験事実が要求する形として受け入れておく。

---

## 状態の重ね合わせ

角度則は、球の内部状態について重要なことを教えている。

$z$ 軸で $+1$ が確定した状態 $\vert +z \rangle$ の球を、別の軸 $n$ で測ると、$+1$ も $-1$ も出る。つまり $\vert +z \rangle$ は $n$ 軸の測定に対しては結果が確定していない。それでいて、確率はきちんと角度で決まっている。

この状況を記述するために、**重ね合わせ**（superposition）を導入する。 $\vert +z \rangle$ を、$n$ 軸の固有状態 $\vert +n \rangle, \vert -n \rangle$ を使って

```math
\vert +z \rangle = \alpha \vert +n \rangle + \beta \vert -n \rangle
```

と展開する。ここで $\alpha, \beta$ は係数である。

この式の意味は、「$\vert +z \rangle$ は $\vert +n \rangle$ でも $\vert -n \rangle$ でもないが、両方の"成分"を持っている」ということだ。

---

## 係数の決定

係数 $\alpha, \beta$ の値は、角度則から決まる。

測定で $+1$ が出る確率が $\vert \alpha \vert^2$ 、$-1$ が出る確率が $\vert \beta \vert^2$ であると仮定する（この仮定は**ボルン則**と呼ばれ、次章で体系的に扱う）。すると角度則との比較から

```math
\vert \alpha \vert^2 = \cos^2\frac{\theta}{2}, \qquad \vert \beta \vert^2 = \sin^2\frac{\theta}{2}
```

が要求される。最も単純な解は

```math
\alpha = \cos\frac{\theta}{2}, \qquad \beta = \sin\frac{\theta}{2}
```

である。つまり

```math
\vert +z \rangle = \cos\frac{\theta}{2}\,\vert +n \rangle + \sin\frac{\theta}{2}\,\vert -n \rangle
```

と書ける。この関係を逆に読むと、$n$ 軸の固有状態 $\vert +n \rangle$ は $z$ 軸の固有状態で展開できる。 $z$ 軸と $n$ 軸のなす角が $\theta$ のとき

```math
\vert +n \rangle = \cos\frac{\theta}{2}\,\vert +z \rangle + \sin\frac{\theta}{2}\,\vert -z \rangle
```

```math
\vert -n \rangle = -\sin\frac{\theta}{2}\,\vert +z \rangle + \cos\frac{\theta}{2}\,\vert -z \rangle
```

である。2番目の式に $-\sin$ が現れるのは、$\vert +n \rangle$ と $\vert -n \rangle$ が直交する（内積がゼロになる）ために必要な符号である。

---

## 確率の再現を検算する

導いた係数が本当に角度則を再現するか、確かめておこう。

球が $\vert +n \rangle$ にあるとする。この状態を $z$ 軸の基底で展開すると

```math
\vert +n \rangle = \cos\frac{\theta}{2}\,\vert +z \rangle + \sin\frac{\theta}{2}\,\vert -z \rangle
```

$z$ 軸で測定したとき、$+1$ が出る確率は

```math
P(+1) = \cos^2\frac{\theta}{2}
```

$-1$ が出る確率は

```math
P(-1) = \sin^2\frac{\theta}{2}
```

角度則と一致する。

逆に、球が $\vert -n \rangle$ にあるとき、$z$ 軸測定で $+1$ が出る確率は

```math
P(+1) = \sin^2\frac{\theta}{2}
```

となり、$\vert +n \rangle$ のときと入れ替わる。これも反転規則と整合している。

---

## 測定後の状態更新

もうひとつ重要な事実がある。

球が $\vert +z \rangle$ にあるとき、$n$ 軸で測定して $+1$ が出たとする。その直後にもう一度 $n$ 軸で測ると、必ず $+1$ が出る。これは前章の再現性そのものだが、重ね合わせの言葉では次のように読める。

測定前の状態は

```math
\vert +z \rangle = \cos\frac{\theta}{2}\,\vert +n \rangle + \sin\frac{\theta}{2}\,\vert -n \rangle
```

で、$\vert +n \rangle$ と $\vert -n \rangle$ の両方の成分を持っていた。しかし $n$ 軸測定で $+1$ が出た瞬間、状態は $\vert +n \rangle$ になる。$\vert -n \rangle$ の成分は消える。

```math
\cos\frac{\theta}{2}\,\vert +n \rangle + \sin\frac{\theta}{2}\,\vert -n \rangle \xrightarrow{n\text{ 軸で }+1} \vert +n \rangle
```

これが**状態更新**（state update）である。測定は状態を読み取るだけでなく、状態を変える。この事実は、次章以降の議論で繰り返し使われる。

---

## 反平行の関係

最後に、前章の反転規則を新しい記法で整理しておく。

軸 $n$ を反転した軸を $-n$ と書く。たとえば $n$ が「上」なら $-n$ は「下」である。前章で確認したように、同じ軸を反対から挟めば声が反転する。これは

```math
\vert +(-n) \rangle = \vert -n \rangle, \qquad \vert -(-n) \rangle = \vert +n \rangle
```

と書ける。つまり、$-n$ 方向で **Yay!**（$+1$）が出る状態は、$n$ 方向で **Oops!**（$-1$）が出る状態と同じである。軸の向きを反転しても新しい物理は生まれない——ラベルが入れ替わるだけである。

---

## 複素数への伏線

この章では係数 $\alpha, \beta$ を実数として扱った。実際、$z$ 軸と $n$ 軸が同一平面内にある限り、実数の係数で角度則を完全に再現できる。

しかし球は三次元空間に存在する。測定軸は一つの平面に限られない。三次元のすべての軸方向を記述しようとすると、実数だけでは自由度が足りなくなる。この問題は第4章（ブロッホ球）で正面から扱う。そこで係数は複素数 $\alpha, \beta \in \mathbb{C}$ へ拡張されることになる。

---

## この章で手に入れたもの

1. 異なる軸で測ると、結果は確率的になる。確率は2つの軸のなす角 $\theta$ で決まる。
2. 角度則: $P(+1) = \cos^2(\theta/2)$, $P(-1) = \sin^2(\theta/2)$ 。
3. 状態の重ね合わせ $\vert +n \rangle = \cos(\theta/2)\,\vert +z \rangle + \sin(\theta/2)\,\vert -z \rangle$ を導入した。
4. 係数の二乗が確率を与える（ボルン則の原型）。
5. 測定は状態を更新する。重ね合わせから一方の固有状態へ変化する。
6. 反平行の関係: $\vert +(-n) \rangle = \vert -n \rangle$ 。
7. 係数は現段階では実数だが、三次元を記述するには複素数が必要になる。

次章では、測定を演算子として扱い、期待値・内積・射影の言語を整える。
