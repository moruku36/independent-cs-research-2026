**日本語** | [English](README.md)

# Independent CS Research 2026

個人・企業勤務者がコンピュータサイエンスの研究を進め、論文・学会発表につなげるための公開ノートです。公開情報に基づく発表経路、研究候補、AI論文の読書記録と活用案を今後蓄積します。

**現状（2026-10-26 JST）：研究計画は初期段階。各論文ノートに、実際に確認した範囲（一次本文・部分読了・要旨のみ）を明記しています。再現実験・独自研究の検証は未実施です。発表資格・採択例・経歴・所属は未確定です。**

## テーマ別の論文ノート

まずテーマを選んでください。各フォルダのREADMEに、論文の一覧と確認状態があります。[全テーマと運用ルール](surveys/README.ja.md)。

- [AIエージェントの安全性・逸脱行動](surveys/agent-safety/README.ja.md)（論文4本＋研究記事1本）: AIエージェントが権限外の行動をとるか、実際のワークフローがどう攻撃されうるか。 [自己複製AI](surveys/agent-safety/2026-anthropic-self-replicating-ai.ja.md)・[報酬ハッキング](surveys/agent-safety/2025-reward-hacking-emergent-misalignment.ja.md)。 [Agentic Overconfidence：AIエージェントの自信は成功率と一致するか](surveys/agent-safety/2026-agentic-overconfidence.ja.md)。
- [おとり・欺瞞とLLMシステム防御](surveys/deception-defense/README.ja.md)（2本）: 偽の証拠やおとりモデルで、悪意あるエージェントや要求を誘導・隔離する研究。
- [コーディングエージェント・コードレビュー・開発現場](surveys/coding-agents/README.ja.md)（論文7本＋研究記事1本＋技術記事4本）: AIコーディング支援・自動修復・自動レビューのベンチマークと企業での実証研究。 [形式検証](surveys/coding-agents/2026-anthropic-formal-verification.ja.md)・[NFV](surveys/coding-agents/2026-neuro-formal-verification.ja.md)・[サブエージェント統合](surveys/coding-agents/2026-fold-subagents-main-loop.ja.md)。 [Anthropicのソース管理再設計：Scion](surveys/coding-agents/2026-anthropic-scion-source-control.ja.md) (技術記事・報告)。 [Claude Codeのコードレビュー](surveys/coding-agents/2026-claude-code-review.ja.md)。
- [職場での人とAIの協働](surveys/human-ai-collaboration/README.ja.md)（5本）: AIの同僚への期待、待ち時間・注意の扱い、AI利用による業務活動と学習機会の変化。 [職場の生成AI導入](surveys/human-ai-collaboration/2026-genai-workplace-productivity-communication.ja.md)・[日常対話の非公式学習](surveys/human-ai-collaboration/2026-informal-learning-human-llm.ja.md)。 [人とAIの協働で、目標を独立した共有情報として扱う](surveys/human-ai-collaboration/2026-goals-first-class-abstractions.ja.md)。
- [セキュリティ・ガバナンス（プライバシー・組織ポリシー・暗号アジリティ・クラウド統制）](surveys/security-governance/README.ja.md)（論文4本＋記事3本）: GenAI利用・暗号移行・マルチクラウド統制の一貫性をめぐる、組織面のセキュリティの問い。 [マルチクラウド設計のサーベイ](surveys/security-governance/2026-multi-cloud-security-architecture.ja.md)。 [Agentic Inequality：AIエージェントを使える力の格差](surveys/security-governance/2025-agentic-inequality.ja.md)。 [シャドーAI・個人情報の解説記事レビュー](surveys/security-governance/2026-shadow-ai-ban-pii-governance.ja.md).
- [LLM推論基盤と費用対効果](surveys/llm-infrastructure/README.ja.md)（3本）: LLM推論のハードウェア選択、スケジューリング、KVキャッシュ制御、長期記憶検索。 [Raw-RAGのサーベイ](surveys/llm-infrastructure/2026-raw-rag-agentic-memory.ja.md)。
- [クラウドの耐障害性・SRE](surveys/cloud-resilience/README.ja.md)（2本）: AWS複数アカウントの障害実験と復旧判定。実測・再現は未確認。 [SequenceFI：タイミングを指定するマイクロサービス障害注入](surveys/cloud-resilience/2026-sequencefi.ja.md)。 [Cloud Computing & DevOps：2025–2026年の研究動向](surveys/cloud-resilience/2026-cloud-devops-research-insights.ja.md) (技術記事・報告).
- [イベント・技術記事・仕事／労働研究](surveys/articles/README.ja.md)（記事・報告書5本＋学術論文1本）: 仕事・労働のCHI論文を記事と区別して収録。 [再帰的自己改善（RSI）：証拠の読み分け](surveys/articles/2026-rsi-evidence-review.ja.md)。

## 経済・企業開示（論文とは別枠）

- [経済・企業開示の索引](economics/README.ja.md)
- [Anthropic Form S-1](economics/2026-anthropic-s1.ja.md) — 2026-10-26提出。索引・表紙の読書ノート／財務本文未確認。

## 計画・ガイド

- [個人によるCS研究の発表と論文投稿](docs/publication-pathways-2026.ja.md)：2026-10-11 JST更新。国内の発表経路、採録例、公開研究意図を一次資料で確認。本人の投稿先・所属表記・参加予算は未決定。
- [研究候補（未検証）](docs/research-agenda.ja.md)
- [AI論文の読書・活用一覧](docs/reading-list.ja.md)
- [再現性・倫理・公開前の確認票](docs/reproducibility-ethics-checklist.ja.md)
- [サーベイ記録のテンプレート](surveys/template.ja.md)
- [参考文献候補（一次本文確認）](docs/reference-candidates/2024-dwave-annealing-rsa.ja.md)：D-Wave Advantageによる量子アニーリングとRSA整数分解（2026-10-14 追加）。論文ノートの件数には含めない。

## このリポジトリについて

公開内容は本人の公開CS経歴・OSS実績・研究計画と公開論文情報に限定します。会社内部情報、私信、秘密、非公開の個人情報は掲載しません。公開前の誤認防止のため、本プロジェクトの構成・主張・図表・調査結果の他媒体への転載・再利用・引用・要約はお控えください。

英語が主言語で、すべてのページに日本語版（`*.ja.md`）があります。各ページ先頭の切替リンクから移動できます。
