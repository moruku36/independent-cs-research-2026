**日本語** | [English](2026-camm-practical-evaluation.md)

# CAMM — 暗号アジリティ成熟度モデルの実用評価

- **状態**：一次PDF本文確認済み（§1–6、Table 1–3）／再現未実施。
- **題名・著者・年・会場・DOI／arXiv ID・一次URL**：*Practical Evaluation of the Crypto-Agility Maturity Model*／Leonie Wolf, Samson Umezulike, Gurur Öndarö, Sebastian Schinzel, Fabian Ising／2026／arXivの会場記載はFPS 2025／[arXiv:2604.12428v1](https://arxiv.org/abs/2604.12428v1)／[PDF](https://arxiv.org/pdf/2604.12428v1)／[DOI](https://doi.org/10.48550/arXiv.2604.12428)。
- **確認日・対象version**：2026-10-15 UTC／v1、2026-04-14提出。引用先のCAMM原論文・Webサイトは別途精読していない。
- **研究の問い**：CAMMの設計原則への適合、実用上の適用可能性、改善点（RQ1–3）。
- **手法・データ・比較条件**：成熟度モデルの設計原則による分析と、インターネットから隔離した社内HTTPSサービスへの適用。指定ブラウザーとOSは定期更新を仮定。研究者4人が独立に要件を分類し、議論で合意した（§3–4）。
- **主張と証拠**：範囲・対象者、測定可能な受入基準、依存関係に問題を指摘（Table 1・3）。**Table 2の✓は組織の判断で要件を満たせるという意味**で、実装・移行成功の証明ではない。Piは初期判断と最終合意の一致割合で、参考値。範囲の明確化、検証可能な基準、依存関係の整理、対象者別の手引きを提案する（§5）。
- **限界・妥当性への脅威**：4人・単一の簡略シナリオで一般化に限界がある。改良版CAMMは提示していない（§1）。PQC性能、安全性、実システムの成熟度を実証した論文として扱わない。
- **関連研究との比較**：CAMM原論文を評価する研究であり、CAMMの代替実装ではない。ラボの[独自採点](https://github.com/moruku36/pqc-crypto-inventory-lab/blob/main/docs/scoring.md)とは対象も判定方法も異なる。既存の[AI論文の記録](README.ja.md)と同様、申告・観測・検証結果の区別を重視する。

## 無料で実施できる再現案（本リポジトリの提案、未実施）

厳密な追試には、論文が評価したCAMM原論文・Web要件の版を確保する必要がある。現在のWebサイトをそのまま使う場合は、v1論文の追試ではなく後続版の評価と明記する。

まずラボの公開合成サンプルだけを使い、評価対象のファイル、除外範囲、根拠、責任範囲を固定する。評価票に「要件ID／判定基準／適用性と理由／証拠／評価者／日付／判断」を分けて記入する。情報不足と対象外を混同しない。2人以上で独立判断を保存してから合議し、不一致件数と解釈変更を記録する。この小規模演習は、4人による原評価の再現や統計的な妥当性の確認にはならない。

- **活用状態**：提案。[PQC側の改善計画](https://github.com/moruku36/pqc-crypto-inventory-lab/blob/main/docs/camm-practical-evaluation.ja.md)に接続する文書追加のみ。CAMM採点・新スキーマ・新機能・実験は実装していない。
- **未確認点・次の確認**：原評価時のCAMM要件版と個別判断データの入手可能性を確認し、演習の事前基準を決める。測定を行うまで一致率や改善効果は報告しない。

## English

Primary PDF reviewed; no reproduction. Proposed work is an offline evidence-review exercise, not a CAMM implementation or maturity certification.

[論文集索引](README.ja.md) | [全読書一覧](../../docs/reading-list.ja.md)
