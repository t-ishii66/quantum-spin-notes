# ARGUE notes (current)

## 対象
- [Chapter_1.md](/Users/ben/Develop/Claude/TheAlienSphere/Chapter_1.md)

## 現在の主な問題点（物理観点）

1. 章1として情報密度が高い
- `Scene 1-2` 以降で、固有状態・直交・測定演算子・重ね合わせ・Born則・期待値まで一気に入っている。
- 物理的誤りではないが、導入章としては読者負荷が大きい。
- 対応案: 期待値計算（`⟨\phi_n|\hat M_n|\phi_n⟩`）は Chapter 2/3 に移す。

2. Born則の「要請」である点をもう1段強く明示したい
- 現在も要請と書いてあるが、読者によっては式展開で導出したように見える可能性が残る。
- 対応案: 「この章では採用する。根拠と検証は後章」の1文を追加。

3. 記号の依存関係を1行で補強したい
- `P(a)=|\alpha|^2` は `|\phi_n\rangle=\alpha|Yay_n\rangle+\beta|Oops_n\rangle` という「その測定基底での展開」に依存する。
- 対応案: 「\alpha,\beta は \hat M_n の固有基底で展開した係数」と明記。

## すでに解消済み（再発防止メモ）
- `|Yay_n\rangle = -|Oops_n\rangle` の誤りは削除済み。
- `M` と `M_n` の混同は整理済み（`M ≡ M_z` を明示）。
- 固有値 `a,b` は「実数かつ `a\neq b`」を明記済み。
- `|α|^2` と `α^2` の混在は、主記法を `|α|^2` に統一済み。

## 次にやるなら
1. Chapter 1 の `Physics Note 1-3` を短縮して、詳細計算は Chapter 3 へ移設。
2. Chapter 1 の末尾に「この章ではここまで」を3行で入れる。
