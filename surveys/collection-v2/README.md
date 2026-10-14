# サーベイ論文集 v2

2026年のコンピュータサイエンス／AIセキュリティ論文の読書記録。各ファイルは[サーベイ記録テンプレート](../template.md)の項目に沿い、**一次資料確認／本文精読／再現**を区別して記録する。

## AIエージェントの安全性・逸脱行動

- [Evaluating Whether GPT-6 Astra Performs Unsanctioned Supply-Chain Attacks](2026-unsanctioned-supply-chain-attacks.md)（2026-09-29）— 権限外のOSSサプライチェーン攻撃をAIが試みるか評価。一次本文確認済み／実験未実施。

## おとり・欺瞞とLLMシステム防御

- [AgentLSD](2026-agentlsd.md)（2026-09）— 偽の証拠でエージェントの探索や推論予算がどう変化するか。要旨確認／追試なし。
- [HoneyRoute](2026-honeyroute.md)（2026-09）— 不正リクエストをおとりLLMに分岐し、本番の負荷を隔離。要旨確認／追試なし。
- [2論文の横断比較（旧テーマ別メモ）](../2026-ai-agent-honeypot-deception.md)

## コーディング支援と人・AI協働

- [SWE-Journey](2026-swe-journey.md)（2026-10-08）— 長期開発と模擬利用者の対話を評価。一次本文確認済み／部分読了／実験未実施。
- [FlowAgent](2026-flowagent.md)（2026-10-05）— Googleの提出前テスト失敗を低遅延で自動修復。一次PDF確認済み／再現未実施（非公開データによる制約）／運用方針採用・効果未検証。

## 研究メモの原則

- 実験を行っていない場合は「再現済み」と記載しない。
- 論文のシミュレーション結果を、実運用の攻撃成功と混同しない。
- 引用文献の一次URLと確認状態を必ず残す。
- 既存の個別メモは外部リンク保護のため維持し、このディレクトリを**今後の正規の索引先**にする。

[リポジトリREADME](../../README.md) | [全読書一覧](../../docs/reading-list.md)

## English index

- [SWE-Journey: long-horizon coding collaboration](2026-swe-journey.md) — primary text checked, partial reading; no reproduction.
- [FlowAgent: low-latency pre-submit test repair at Google](2026-flowagent.md) — primary PDF checked; proprietary data, no reproduction.
- [Unsanctioned supply-chain attacks](2026-unsanctioned-supply-chain-attacks.md) — primary text checked; no experiments.
- [AgentLSD](2026-agentlsd.md) and [HoneyRoute](2026-honeyroute.md) — abstract-based records.
- [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
