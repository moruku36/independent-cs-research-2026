**日本語** | [English](README.md)

# サーベイノート

コンピュータサイエンス／AIセキュリティの論文・研究記事の読書記録。各ファイルは[サーベイ記録テンプレート](template.ja.md)の項目に沿い、**一次資料確認／本文精読／再現**を区別して記録する。テーマを選んでください。

- [AIエージェントの安全性・逸脱行動](agent-safety/README.ja.md)（論文4本＋研究記事1本）: AIエージェントが権限外の行動をとるか、実際のワークフローがどう攻撃されうるか。 [Agentic Overconfidence：AIエージェントの自信は成功率と一致するか](agent-safety/2026-agentic-overconfidence.ja.md)。
- [おとり・欺瞞とLLMシステム防御](deception-defense/README.ja.md)（2本）: 偽の証拠やおとりモデルで、悪意あるエージェントや要求を誘導・隔離する研究。
- [コーディングエージェント・コードレビュー・開発現場](coding-agents/README.ja.md)（論文7本＋研究記事1本＋技術記事4本）: AIコーディング支援・自動修復・自動レビューのベンチマークと企業での実証研究。 [Anthropicのソース管理再設計：Scion](coding-agents/2026-anthropic-scion-source-control.ja.md) (技術記事・報告).
- [職場での人とAIの協働](human-ai-collaboration/README.ja.md)（5本）: AIの同僚への期待、待ち時間・注意の扱い、AI利用による業務活動と学習機会の変化。 [人とAIの協働で、目標を独立した共有情報として扱う](human-ai-collaboration/2026-goals-first-class-abstractions.ja.md)。
- [セキュリティ・ガバナンス（プライバシー・組織ポリシー・暗号アジリティ・クラウド統制）](security-governance/README.ja.md)（論文4本＋記事レビュー1本）: GenAI利用・暗号移行・マルチクラウド統制の一貫性をめぐる、組織面のセキュリティの問い。 [Agentic Inequality：AIエージェントを使える力の格差](security-governance/2025-agentic-inequality.ja.md)。 [シャドーAI・個人情報の解説記事レビュー](security-governance/2026-shadow-ai-ban-pii-governance.ja.md).
- [LLM推論基盤と費用対効果](llm-infrastructure/README.ja.md)（3本）: LLM推論のハードウェア選択、スケジューリング、KVキャッシュ制御、長期記憶検索。
- [クラウドの耐障害性・SRE](cloud-resilience/README.ja.md)（2本）: AWS複数アカウントの障害実験と復旧判定。実測・再現は未確認。 [SequenceFI：タイミングを指定するマイクロサービス障害注入](cloud-resilience/2026-sequencefi.ja.md)。 [Cloud Computing & DevOps：2025–2026年の研究動向](cloud-resilience/2026-cloud-devops-research-insights.ja.md) (技術記事・報告).
- [イベント・技術記事・仕事／労働研究](articles/README.ja.md)（記事・報告書5本＋学術論文1本）: 仕事・労働のCHI論文を記事と区別して収録。 [再帰的自己改善（RSI）：証拠の読み分け](articles/2026-rsi-evidence-review.ja.md)。

研究記事も同じ記録項目で整理するが、査読論文・プレプリントとは区別して件数を示す。

## 研究メモの原則

- 実験を行っていない場合は「再現済み」と記載しない。
- 論文のシミュレーション結果を、実運用の攻撃成功と混同しない。
- 引用文献の一次URLと確認状態を必ず残す。
- すべてのノートに日本語版（`*.ja.md`）を用意する。
- すべてのノートの冒頭（タイトル直後）に、3行の**概要**（何についてのものか／何を述べているか／留意点）を置く。

## ファイルの置き場所

論文は `surveys/<テーマ>/<年>-<スラッグ>.md`、日本語版は `<スラッグ>.ja.md`。各テーマのフォルダに、そのテーマのノート一覧のREADMEがある。計画・確認票・全読書一覧は [docs/](../docs/reading-list.ja.md) にある。

[リポジトリREADME](../README.ja.md) | [全読書一覧](../docs/reading-list.ja.md)
