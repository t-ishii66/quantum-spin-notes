# Chapter 4: The Bloch Sphere

## Scene 4-1: まだ変数が足りない

夜の机に、黒い球がひとつ。  
Aliceが指先で球を回しながら言った。  
「ねえ、なんか変。私たち、同じことしか聞いてない気がする」

Bobが顔を上げる。  
「同じこと？」

「うん。まず叩いて、Yay/Oops を数える。  
でも最初の1回で状態を作り替えちゃうなら、“それ以前の向き”が見えてないんじゃない？」

Charlieがペンを止める。  
「それだ。Chapter 3 までで使った変数だけだと、説明しきれない差が残るはずだ」

Bobがノートに書く。  
「不足してる自由度を探す。次は、測る向きを変える」

---

## Physics Note 4-1: なぜ φ が必要か

`z` 基底で

$$
|\psi\rangle=\cos\frac{\theta}{2}|Yay\rangle+e^{i\phi}\sin\frac{\theta}{2}|Oops\rangle
$$

と書くと、`z` 方向の確率は

$$
P(Oops|z)=\sin^2\frac{\theta}{2}
$$

で、相対位相 $\phi$ は現れない。  
つまり、`z` 方向だけの測定では $\theta$ は見えても $\phi$ は見えない。

したがって位相を知るには、`z` 以外の向き（例: `x`,`y`）で統計を取る必要がある。

---

## Scene 4-2: 三つの山

三人は実験手順を作り直した。

1. 同じ準備操作 `Prep(r)` で、できるだけ同じ状態を大量に作る。  
2. サンプルを3つの山に分ける。  
3. 山Aは `z`、山Bは `x`、山Cは `y` 方向で、**最初の1回だけ**叩く。  
4. 各山の Yay/Oops 比率を集計する。

Aliceが念を押す。  
「二回目はなし。二回目はもう別状態の実験だから」

Charlieがうなずく。  
「最初の1回だけが“元の状態”の情報を持つ」

翌朝、表ができた。  
`z` の比率は同じなのに、`x` と `y` が準備条件で系統的にずれている。

Bobが笑う。  
「きた。これは角度 $\theta$ だけじゃ説明できない」

---

## Physics Note 4-2: x, y で位相を読む

純粋状態を

$$
|\psi\rangle=\cos\frac{\theta}{2}|Yay\rangle+e^{i\phi}\sin\frac{\theta}{2}|Oops\rangle
$$

とすると、期待値は

$$
\langle\sigma_z\rangle=\cos\theta,
\quad
\langle\sigma_x\rangle=\sin\theta\cos\phi,
\quad
\langle\sigma_y\rangle=\sin\theta\sin\phi
$$

である。測定確率との関係は

$$
P(Yay|n)=\frac{1+\langle\sigma_n\rangle}{2}
$$

だから、`x,y,z` の統計から

$$
\theta=\arccos(\langle\sigma_z\rangle),
\qquad
\phi=\mathrm{atan2}(\langle\sigma_y\rangle,\langle\sigma_x\rangle)
$$

を再構成できる。

補足: $\theta=0,\pi$（北極・南極）では $\phi$ は物理的に未定義になる。

---

## Scene 4-3: 球として見る

Aliceはノートの真ん中に円を描いた。  
上を `Yay`、下を `Oops`。  
赤道に `x` と `y` の目盛りを置く。

「これ、状態が球面上の点ってこと？」

Charlieが答える。  
「そう。縦の傾きが $\theta$、赤道方向の方位が $\phi$。  
Chapter 2 の角度則と Chapter 3 の演算子計算を、同じ図で見られる」

Bobが言う。  
「つまり、状態は“値”じゃなくて“向き”なんだ」

Aliceが笑う。  
「しかもその向きは、質問の向きを変えないと全部は見えない」

---

## Physics Note 4-3: ブロッホ球の最小まとめ

2準位純粋状態は、全体位相を除けば 2つの実パラメータで決まる。  
その自然な座標が $(\theta,\phi)$ で、ブロッホ球では

- 北極: $|Yay\rangle$  
- 南極: $|Oops\rangle$  
- 赤道: 等重み重ね合わせ（位相差のみ違う）

として表される。

この章の役割は「状態を球で可視化すること」。  
次章では、単一球ではなく**2球の相関**へ進む。

## この章で手に入れたもの

1. `z` 方向だけでは位相 $\phi$ は見えない。  
2. `x,y,z` の3方向測定で $(\theta,\phi)$ を再構成できる。  
3. 2準位純粋状態はブロッホ球上の1点として表せる。  
4. 状態は「結果の箱」ではなく「測定方向への応答を持つ向き」として理解できる。  
5. 次章では2球分裂と相関（もつれ）を扱う。
