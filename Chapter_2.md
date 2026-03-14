# Chapter 2: The Rules of the Sphere

## Scene 1: 名前を固定する

次の日、三人は黒い球を机の上に置き、ノートを開いた。  
もう「変な声の出るおもちゃ」では終わらせない。  
法則として書き下せるかどうか、それを試す日だった。

Bobが言う。  
「まずは結果を名前で固定しよう。毎回“あの明るい声”とか言ってたら進まない」

Charlieがうなずき、Aliceがノートに大きく書いた。

- 声1: **Yay!**
- 声2: **Oops!**

その夜、三人は叩く場所を少しずつ変えながら、ひたすら記録を取った。  
Aliceが適当な場所を叩き、その方向を実験上の基準方向 $n$ とする。  
次に、$n$ から角度 $\theta$ だけずれた方向を叩く。  
これを何百回も繰り返した。

朝方、Charlieが集計表を見せる。  
「完全一致じゃないけど、回数を増やすほど同じ曲線に寄る」

## Physics Note 1: 観測則と状態ラベル

この章では、物語パートと解説パートを分離して進める。まず観測則を固定する。

- 測定結果は常に2値: `Yay` または `Oops`
- 一回目叩いた点から、 $\theta$ だけズレた点で2回目を叩く。その測定では、経験的に次が成り立つ:


状態記号として

$$
|Yay\rangle,\quad |Oops\rangle
$$

を導入する。
この $|\,\cdot\,\rangle$ の形をケット（ket）、対応する $\langle\,\cdot\,|$ の形をブラ（bra）と呼ぶ。

本書では、特に断らない限り基準軸として $z$ 軸を暗黙に採用する。  
したがって

$$
|Yay\rangle\equiv|Yay_z\rangle,\qquad |Oops\rangle\equiv|Oops_z\rangle
$$

とする。一般方向 $n$ の固有状態は

$$
|Yay_n\rangle,\quad |Oops_n\rangle
$$

と書く。

ここで $|Yay\rangle, |Oops\rangle$ は、状態を表す一種のベクトルだと考える。  
内積 $\langle\cdot|\cdot\rangle$ は、2つの状態の「関連具合（重なり具合）」を表す量である。  
- $\langle Yay|Yay\rangle=1$ は、ブラもケットも同じ Yay状態だから、関連性はMAX、すなわち１になる。  
- $\langle Yay|Oops\rangle=0$ は、Yay状態とOops状態が無関係（重なりなし）であることを表す。  
この「長さ1（規格化）かつ互いに重なり0（直交）」をまとめて、直交規格化条件と呼ぶ。

直交規格化条件:

$$
\langle Yay|Yay\rangle=\langle Oops|Oops\rangle=1,\qquad
\langle Yay|Oops\rangle=0
$$

ここで次の疑問が出る。  
「球の状態は、いつも $|Yay\rangle$ か $|Oops\rangle$ のどちらかだけなのか？」  
実験では、中間角で確率的な結果が出るため、2つの基底状態の“混ざり具合”を表す記述が必要になる。  
そこで一般状態を

$$
|\phi\rangle=\alpha|Yay\rangle+\beta|Oops\rangle,\qquad
\alpha^2+\beta^2=1
$$

と置く（この段階では $\alpha,\beta$ は実数）。  
$\alpha,\beta$ はそれぞれの成分の重みである。  
ここで「なぜ $\alpha^2,\beta^2$ が確率なのか？」という疑問が出るが、  
この対応は量子論では **ボルン則** と呼ばれ、この段階では基本仮定として採用する。  
仮定といっても恣意的に決めるのではなく、実験事実（角度依存の統計）を最も簡潔に再現する規則になっている。  
もし一次（$\alpha,\beta$）で確率を置くと、確率が負になる・全確率1が保てないなどの問題が起きる。  
そのため「確率は振幅の絶対値二乗で与える」という形が必要になる。  
したがって全確率が1になる条件

$$
\Pr(Yay)+\Pr(Oops)=\alpha^2+\beta^2=1
$$

を満たす必要がある。これが規格化条件である。  
要するに、$|\phi\rangle$ は「Yay/Oops のどちらか」ではなく、「Yay成分とOops成分を同時に持つ状態」を表すための最小の書き方になっている。

## Scene 2: 「叩く」は読むだけではない

Aliceは前日の実験を思い出していた。  
「同じ場所を二回叩くと、二回目は必ず一回目と同じ。これ、偶然じゃないよね」

Charlieが答える。  
「読むだけじゃない。最初の測定で、球の中身が“次に同じ答えを返す状態”に変わってる」

Bobが続ける。  
「測定装置じゃなくて、状態更新の装置でもあるってことか」

## Physics Note 2: 射影測定

方向 $n$ の測定を

$$
\mathrm{Measure}(n)
$$

と書く。この測定には2つの射影演算子が対応する:

$$
P_n^{Yay}=|Yay_n\rangle\langle Yay_n|,\qquad
P_n^{Oops}=|Oops_n\rangle\langle Oops_n|
$$

完備性:

$$
P_n^{Yay}+P_n^{Oops}=I
$$

確率（Born則）:

$$
\Pr(Yay|n)=\langle\psi|P_n^{Yay}|\psi\rangle,\qquad
\Pr(Oops|n)=\langle\psi|P_n^{Oops}|\psi\rangle
$$

測定後状態:

$$
|\psi\rangle\to
\frac{P_n^{Yay}|\psi\rangle}{\sqrt{\langle\psi|P_n^{Yay}|\psi\rangle}}
=|Yay_n\rangle
$$

Oops結果なら同様に $|Oops_n\rangle$ へ更新される。

補足（なぜ和が $I$ か）: 任意状態を

$$
|\psi\rangle=a|Yay_n\rangle+b|Oops_n\rangle
$$

と分解すると

$$
(P_n^{Yay}+P_n^{Oops})|\psi\rangle
=a|Yay_n\rangle+b|Oops_n\rangle
=|\psi\rangle
$$

となるためである。

## Scene 3: 反対側と中間側

Bobは球の一点を叩き、次にその真反対を叩いた。  
「やっぱり必ず反転する」

Aliceはその中間あたりを叩く。  
今度は同じになったり逆になったりする。  
「中間はブレる。でもデタラメじゃない」

Charlieがうなずく。  
「角度で連続的に変わってる」

## Physics Note 3: 反転則と角度依存

反対方向の固有状態は入れ替わる:

$$
|Yay_{-n}\rangle=|Oops_n\rangle,\qquad
|Oops_{-n}\rangle=|Yay_n\rangle
$$

したがって、同じ内部状態でも測定軸を反転すると結果ラベルが反転する。

また、状態が $|Yay_n\rangle$ のとき、方向 $m$（$n$ との角度差を $\theta$）での結果確率は

$$
\Pr(Yay|m,|Yay_n\rangle)=\cos^2\frac{\theta}{2},\qquad
\Pr(Oops|m,|Yay_n\rangle)=\sin^2\frac{\theta}{2}
$$

である。よって

- $\theta=0$ で必ず同じ結果
- $\theta=\pi$ で必ず反対結果
- その間は確率的混合

が同時に満たされる。

## Scene 4: 磁石事件

その日の夕方、Aliceは台所で球に磁石を近づけた。  
磁石側を叩くと **Yay!**。  
向きを確認して叩いても **Yay!**。  
球を回して磁石側を合わせて叩いても **Yay!**。

Aliceは走って二人を呼んだ。  
三人で追試しても、同じ傾向が続く。

Bobが目を輝かせる。  
「測るだけじゃない。状態を作れる」

Charlieは慎重に言う。  
「原因が磁石そのものかは未確定。でも“外から状態をそろえられる”のは確かだ」

## Physics Note 4: 準備操作

この操作を

$$
\mathrm{Prep}(r)
$$

と呼ぶ（$r$ は磁石を向けた方向）。理想化すれば

$$
\mathrm{Prep}(r):\quad |\psi\rangle\to|Yay_r\rangle
$$

と表せる。

実験的には、まず「高い確率で $|Yay_r\rangle$ にそろう」と理解するのが安全である。

重要な区別:

- 測定 `Measure(n)`: 結果を読み出し、同時に状態を更新する
- 準備 `Prep(r)`: 望む方向へ状態をそろえる

この2つは別操作であり、混同しない。

## この章の要点

1. 声は2値であり、状態は $|Yay\rangle,|Oops\rangle$ を基底として記述できる。  
2. 方向 $n$ の測定は射影演算子 $P_n^{Yay},P_n^{Oops}$ で表せる。  
3. 測定は確率を与えるだけでなく、状態を測定固有状態へ更新する。  
4. 反対方向では結果ラベルが反転し、一般角度では $\cos^2(\theta/2),\sin^2(\theta/2)$ に従う。  
5. 外部操作 `Prep(r)` により、状態準備という概念が必要になる。

ノートを閉じるとき、Bobが言った。  
「ルールはそろった。次は、これを一つの図形として見たい」

Charlieが答える。  
「状態空間を、球として描く段階だね」

Aliceは黒い球を机の中央に戻した。  
この物体は、ただの不思議な道具ではない。  
“状態”という言葉で世界を見る入口だった。
