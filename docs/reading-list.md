# AI論文の読書・活用一覧

状態：既存の二次記事seedは一次論文の識別待ち。読書状態は論文別に記録する。Astra・SWE-Journey・FlowAgent・GitInjectは一次本文（FlowAgentは一次PDF）確認済み、SWE-Journeyは部分読了（再現・実装は未実施）。活用案を実施済みの成果と扱いません。

| 二次記事seed | 関心・活用案 | 一次論文／読了／実装 |
|---|---|---|
| https://ai-data-base.com/timeline/read/125022 | 工数予測シミュレーションへの活用案 | 識別待ち／未確認／未確認 |
| https://ai-data-base.com/timeline/read/127145 | Qwenによる独立レビュー・A100への適用案 | 識別待ち／未確認／未確認 |
| https://ai-data-base.com/timeline/read/122219 | 内容理解・解説の対象 | 識別待ち／未確認／未確認 |

## サーベイ論文集 v2

- **[サーベイ論文集 v2（7論文の索引）](../surveys/collection-v2/README.md)**
- [非承認OSSサプライチェーン攻撃評価（GPT-6 Astra）](../surveys/collection-v2/2026-unsanctioned-supply-chain-attacks.md) — arXiv:2609.38415。一次本文確認／追試未実施。

## 2026年9〜10月：AIエージェント攻撃とおとり

- [おとり・偽の証拠による探索誘導とLLM本番系の保護（詳細メモ）](../surveys/2026-ai-agent-honeypot-deception.md)
- **[AgentLSD — テンプレート準拠の個別メモ](../surveys/collection-v2/2026-agentlsd.md)**（2026-09-16）：偽の手掛かりでAIの探索ターン・推論トークンが増えるかを評価。一次要旨確認済み／再現未実施。[一次論文](https://arxiv.org/abs/2609.19140)
- **[HoneyRoute — テンプレート準拠の個別メモ](../surveys/collection-v2/2026-honeyroute.md)**（2026-09-08）：不正なLLMリクエストをおとりモデルへ分岐し本番側を保護。一次要旨確認済み／再現未実施。[一次論文](https://arxiv.org/abs/2609.08306)
- **元記事**：[AIDB 134139](https://ai-data-base.com/timeline/read/134139)

追加時には、一次URL・書誌情報・読書状態・問い・手法・限界・比較・再現案・活用状態・公開証拠を分けて記録する。

## 2026年10月：コーディング支援と協働

- [SWE-Journey — 長期・対話型コーディング支援の評価](../surveys/collection-v2/2026-swe-journey.md) — [arXiv:2610.11559v1](https://arxiv.org/abs/2610.11559v1)。一次本文確認済み／部分読了／再現・実装未実施。受入条件・検証記録への活用は提案。紹介元[AIDB 134413](https://ai-data-base.com/timeline/read/134413)は取得できず、本文を根拠に記録。
- [FlowAgent — 提出前テスト失敗の低遅延エージェント修復](../surveys/collection-v2/2026-flowagent.md) — [arXiv:2610.07289v1](https://arxiv.org/abs/2610.07289v1)。一次PDF確認済み／再現未実施（データ非公開）。作業委任の運用4点は採用済みだが効果未検証。紹介記事[AIDB 133569](https://ai-data-base.com/timeline/read/133569)は全文未読で、根拠は論文のみ。

## 2026年6月：CI/CDのAIエージェント防御

- [GitInject — AI搭載CI/CDへの実環境プロンプトインジェクション評価](../surveys/collection-v2/2026-gitinject.md) — [arXiv:2606.09935v1](https://arxiv.org/abs/2606.09935v1)。一次HTML通読／再現・PDF照合・コード確認は未実施。試した構成の結果で、全モデルへの一般化ではない。表と本文の不一致は未解決のまま記録。活用案は提案のみ。

## 2026年4月：暗号アジリティ・PQC移行の評価

- [CAMMの実用評価](../surveys/collection-v2/2026-camm-practical-evaluation.md) — [arXiv:2604.12428v1](https://arxiv.org/abs/2604.12428v1)、2026-04-14。一次PDF本文確認済み／再現未実施。PQCラボへの適用は改善提案のみ。

## English index

- [CAMM: practical evaluation of crypto-agility maturity](../surveys/collection-v2/2026-camm-practical-evaluation.md) — primary PDF reviewed; no reproduction or new implementation.
- [Survey collection](../surveys/collection-v2/README.md) — seven paper records with individual reading status.
- [FlowAgent: pre-submit test repair at Google](../surveys/collection-v2/2026-flowagent.md) — primary PDF checked; no reproduction; adopted practices unverified.
- [GitInject: prompt injection in AI-powered CI/CD](../surveys/collection-v2/2026-gitinject.md) — primary HTML read; no reproduction; kept as a defensive survey with unresolved text/table inconsistencies.
- [SWE-Journey: evaluation and proposed acceptance workflow](../surveys/collection-v2/2026-swe-journey.md) — primary text checked, partially read; no reproduction or implementation.
