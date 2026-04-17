# Physics Notes on Spin 1/2

![](images/top.png)

A self-contained note series that starts from the experimental facts of the Stern–Gerlach experiment and derives the Pauli matrices, rotation operators, the Bloch sphere, and Bell's inequality.

All derivations are presented without skipping intermediate steps, and every new concept is explained before it is used. Clarity is prioritized over rigor.

## Notes (English)

| # | Title | Contents |
|---|-------|----------|
| 1 | [Deriving the Pauli Matrices from Experimental Facts](en/NOTE1.md) | From the two-valued Stern–Gerlach measurement through eigenstates, projectors, and spectral decomposition to construct the Pauli matrices $\sigma_x, \sigma_y, \sigma_z$ |
| 2 | [Derivation of the Rotation Operator](en/NOTE2.md) | Derive the rotation operator $U(\theta,\mathbf{n}) = \exp(-i\theta \mathbf{n}\cdot\mathbf{J}/\hbar)$ from probability conservation and unitarity |
| 3 | [The Bloch Sphere](en/NOTE3.md) | Represent spin states as points on a sphere and read measurement probabilities geometrically |
| 4 | [Why θ/2 Appears](en/NOTE4.md) | Explain why the half-angle appears in the spin-1/2 rotation operator, from angular momentum commutation relations |
| 5 | [Bell's Inequality](en/NOTE5.md) | Derive the CHSH inequality from entangled two-particle states and show that quantum mechanics exceeds the classical local-realist bound |
| Supplement | [Mini Introduction to Group Theory: SU(2) and SO(3)](en/NOTE6.md) | A concise introduction to the groups SU(2) and SO(3) that appear in spin rotations, from group definitions through double covers and representations |

## Prerequisites

- High-school level trigonometry and basic matrix operations
- Complex numbers (Euler's formula $e^{i\phi} = \cos\phi + i\sin\phi$)
- A basic familiarity with linear algebra and quantum theory

---

# スピン1/2の物理ノート

シュテルン・ゲルラッハの実験事実から出発し、パウリ行列、回転演算子、ブロッホ球、ベルの不等式までを導く自己完結的なノートシリーズです。

他の教科書を参照しなくても読み進められるよう、式の導出は途中計算を省略せず、新しい概念は使う前に必ず説明しています。厳密さよりわかりやすさを優先しています。

## ノート一覧（日本語）

| # | タイトル | 内容 |
|---|---------|------|
| 1 | [実験事実からパウリ行列を導く](ja/NOTE1.md) | シュテルン・ゲルラッハ実験の二値測定から固有状態・射影子・スペクトル分解を経てパウリ行列 $\sigma_x, \sigma_y, \sigma_z$ を構成する |
| 2 | [回転演算子の導出](ja/NOTE2.md) | 確率保存とユニタリ性から回転演算子 $U(\theta,\mathbf{n}) = \exp(-i\theta \mathbf{n}\cdot\mathbf{J}/\hbar)$ を導く |
| 3 | [ブロッホ球](ja/NOTE3.md) | スピン状態を球面上の1点として表し、測定確率を幾何学的に読む方法を示す |
| 4 | [なぜ θ/2 が現れるのか](ja/NOTE4.md) | スピン1/2の回転演算子に半角が現れる理由を、角運動量の交換関係から説明する |
| 5 | [ベルの不等式](ja/NOTE5.md) | 2粒子のもつれ状態からCHSH不等式を導き、量子力学が古典的な局所実在論の限界を超えることを示す |
| 補講 | [群論ミニ入門：SU(2) と SO(3)](ja/NOTE6.md) | スピンの回転で登場する群 SU(2) と SO(3) の関係を、群の定義から二重被覆・表現まで簡潔に導入する |

## 前提知識

- 高校レベルの三角関数と行列の基本操作
- 複素数（オイラーの公式 $e^{i\phi} = \cos\phi + i\sin\phi$）
- さわり程度の線形代数、量子論の知識

---

## Credits

- Project: t-ishii66 (studied physics at university; systems engineer)
- Authors: Claude Opus 4.6, t-ishii66
- Review: t-ishii66, GPT5.4 Codex
- English translation: Claude Opus 4.6
- Illustrations: ChatGPT5.4
- Published: 2026/4/17
- Version: 1.0.0

---

**Keywords**: quantum mechanics tutorial / spin 1/2 / Pauli matrices derivation / Stern-Gerlach experiment / Bloch sphere / rotation operator derivation / Bell inequality proof / CHSH inequality / quantum entanglement / Born rule / eigenvalue equation / spectral decomposition / projective measurement / hidden variables / local realism / 量子力学 入門 / スピン1/2 / パウリ行列 導出 / シュテルン・ゲルラッハ実験 / ブロッホ球 解説 / 回転演算子 導出 / ベルの不等式 証明 / CHSH不等式 / 量子もつれ エンタングルメント
