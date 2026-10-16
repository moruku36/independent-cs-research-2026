**日本語** | [English](README.md)

# サーベイ論文集 v2

2026年のコンピュータサイエンス／AIセキュリティ論文の読書記録。各ファイルは[サーベイ記録テンプレート](../template.ja.md)の項目に沿い、**一次資料確認／本文精読／再現**を区別して記録する。

## AIエージェントの安全性・逸脱行動

- [Evaluating Whether GPT-6 Astra Performs Unsanctioned Supply-Chain Attacks](2026-unsanctioned-supply-chain-attacks.ja.md)（2026-09-29）— 権限外のOSSサプライチェーン攻撃をAIが試みるか評価。一次本文確認済み／実験未実施。
- [GitInject](2026-gitinject.ja.md)（2026-06-07）— AI搭載CI/CDワークフローへの実環境プロンプトインジェクションを評価。一次HTML通読／再現・PDF照合・コード確認は未実施。表と本文の不一致は未解決のまま記録。

## おとり・欺瞞とLLMシステム防御

- [AgentLSD](2026-agentlsd.ja.md)（2026-09）— 偽の証拠でエージェントの探索や推論予算がどう変化するか。要旨確認／追試なし。
- [HoneyRoute](2026-honeyroute.ja.md)（2026-09）— 不正リクエストをおとりLLMに分岐し、本番の負荷を隔離。要旨確認／追試なし。
- [2論文の横断比較（旧テーマ別メモ）](../2026-ai-agent-honeypot-deception.ja.md)

## コーディング支援と人・AI協働

- [SWE-Journey](2026-swe-journey.ja.md)（2026-10-08）— 長期開発と模擬利用者の対話を評価。一次本文確認済み／部分読了／実験未実施。
- [FlowAgent](2026-flowagent.ja.md)（2026-10-05）— Googleの提出前テスト失敗を低遅延で自動修復。一次PDF確認済み／再現未実施（非公開データによる制約）／運用方針採用・効果未検証。

- [人中心からエージェント型コードレビューへ](2026-agentic-code-review-eras.ja.md)（v1、2026-07-14）— 207のGitHubプロジェクト・約102万PRを、pre-LLM／LLM期／エージェント期で比較。一次HTML通読／PDF照合・再現パッケージ確認・再現は未実施／回帰結果は説明的で因果ではない。

## GenAI利用のプライバシーと組織ポリシー

- [Chat First, Worry Later](2026-chat-first-worry-later.ja.md)（v1、2026-08-21）— 職場でChatGPTを使う欧州の224人への質問票調査。ポリシー・プライバシー懸念・知識の関係。一次HTML通読・PDF図の照合済み／再現未実施／本文と表の不一致は未解決のまま記録。

## 暗号アジリティ・PQC移行の評価

- [CAMMの実用評価](2026-camm-practical-evaluation.ja.md)（v1、2026-04-14）— 一次PDF本文確認済み／再現未実施。評価条件・限界と、PQCラボ向けの未実施の演習案を記録。

## 関連する参考文献候補（サーベイ件数の対象外）

- [2024年のD-Wave量子アニーリング・RSA整数分解報道](../../docs/reference-candidates/2024-dwave-annealing-rsa.ja.md) — 記事から公式PDFへの導線を記録。一次本文未読・書誌未確定・追試未実施。

## 研究メモの原則

- 実験を行っていない場合は「再現済み」と記載しない。
- 論文のシミュレーション結果を、実運用の攻撃成功と混同しない。
- 引用文献の一次URLと確認状態を必ず残す。
- 既存の個別メモは外部リンク保護のため維持し、このディレクトリを**今後の正規の索引先**にする。

[リポジトリREADME](../../README.ja.md) | [全読書一覧](../../docs/reading-list.ja.md)

## English index

- [CAMM: practical evaluation of crypto-agility maturity](2026-camm-practical-evaluation.ja.md) — primary PDF reviewed; no reproduction; evidence-review exercise proposed.
- [SWE-Journey: long-horizon coding collaboration](2026-swe-journey.ja.md) — primary text checked, partial reading; no reproduction.
- [FlowAgent: low-latency pre-submit test repair at Google](2026-flowagent.ja.md) — primary PDF checked; proprietary data, no reproduction.
- [GitInject: prompt injection in AI-powered CI/CD](2026-gitinject.ja.md) — primary HTML read in full; no reproduction; text/table inconsistencies recorded unresolved.
- [Unsanctioned supply-chain attacks](2026-unsanctioned-supply-chain-attacks.ja.md) — primary text checked; no experiments.
- [AgentLSD](2026-agentlsd.ja.md) and [HoneyRoute](2026-honeyroute.ja.md) — abstract-based records.
- [Reading list](../../docs/reading-list.ja.md) | [Repository README](../../README.ja.md)
