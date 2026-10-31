**日本語** | [English](reading-history.md)

# 読書履歴

新しい日付順。過去分は既存の読書一覧に記された追加日を使用し、本人の読了日を保証するものではありません。日付が特定できない資料は省いています。

## 2026-10-31

### [エージェントの構造的テスト](../surveys/agent-safety/2026-agent-workflow-structural-testing.ja.md)

- **課題・方法**：タスクの成功だけでは、許可されたツールやエージェント間の委任、禁止された操作を十分に試したか分からない。[論文](https://arxiv.org/html/2605.26521v1)はそれらの関係をグラフにし、自然言語のテストを生成して実行経路を観測する。
- **結果と注意**：OpenAI Agents SDK由来の10ワークフローで評価し、禁止されたツールへの呼び出しを誘発したケースも報告した。ただし、許可ツールと委任の集計値は抄録と本文の表で食い違っており、原因は未解決。対象の多くはデモ・研究規模で、ツールは模擬されている。
- **実務への応用案**：AIチームの担当、ツール権限、引き継ぎ経路を一覧にし、必要な経路と禁止操作をテストする。回答の正確さや実APIとの連携は別途確認する。一次HTMLの主要部分を確認、再現未実施。

### [エージェントの監査証拠ブラックボックス](../surveys/security-governance/2026-agentic-evidence-black-box.ja.md)

- **課題・提案**：エージェントの通信、ツール操作、人の承認を事後に調査できるよう、[ワーキングペーパー](https://arxiv.org/html/2609.04017v1)は重要な記録を正規化・ハッシュ化し、その証拠を外部に固定する設計を提案する。機密の本文は別の管理された場所に保存する。
- **限界**：ハッシュは保存された記録の変更検知を助けるが、記録内容が正しいことや、収集漏れがないことを保証しない。取得前の差し替え対策、本人・権限の確認、イベントの順序付けも別途必要。実環境での性能・安全性の評価は示されていない。
- **実務への応用案**：クラウド変更の申請、ポリシー、人の承認、実際のAPI引数、変更後の状態を紐付け、エージェントから分離した監査記録に残す。一次HTMLの主要部分を確認、実装・再現未実施。

### [ECB講演：原文確認待ち](../economics/2026-ecb-ai-adoption-pending.ja.md)

- **確認状況**：[指定されたECBページ](https://www.ecb.europa.eu/press/key/date/2026/html/ecb.sp261030~08d9d540f0.en.html)は取得ツールで内部エラーとなり、一次本文は未読。正式題名、講演者、日付、主張、数値は一次資料との照合待ち。
- **参考情報**：[第三者の紹介記事](https://regulus.tv/story/947)はこのURLにリンクし、Philip LaneによるAI導入に関する講演と紹介している。ただし機械生成記事であり、編集者による個別確認はないと記されている。別の二次資料として扱い、その説明や数値をECB本文の確認結果とはしない。
- **次の確認**：一次本文を取得できた後に、調査対象、数値の分母や時点、著者の主張と実務への示唆を整理する。現時点では内容評価・再現未実施。

## 2026-10-30

- [Octoverse 2026：AIエージェントとGitHubの開発動向](../surveys/articles/2026-github-octoverse-agents.ja.md)

- [Google Sleep：継続学習と記憶の定着](../surveys/llm-infrastructure/2026-google-sleep-continual-learning.ja.md)

- [QERS：IoT通信の耐量子暗号評価](../surveys/security-governance/2026-qers-pqc-iot.ja.md)
- [IDOBE：感染症流行予測](../surveys/forecasting/2026-idobe-outbreak-benchmark.ja.md)

- [INFUSE：間接プロンプトインジェクションの評価](../surveys/agent-safety/2026-arxiv-2610.20776.ja.md)
- [The Innocent Courier：Web取得機能を経由した秘密情報の流出](../surveys/agent-safety/2026-arxiv-2610.01768.ja.md)
- [MCPサーバーのファイル権限と資格情報流出](../surveys/agent-safety/2026-arxiv-2610.22301.ja.md)
- [マルチエージェントでの信頼伝播と権限制御](../surveys/agent-safety/2026-arxiv-2609.17648.ja.md)
- [承認から権限濫用へ：コーディングエージェントの権限拡大](../surveys/agent-safety/2026-arxiv-2610.22987.ja.md)
- [Loopjacking：人の承認と実際の操作のすり替え](../surveys/agent-safety/2026-arxiv-2609.21081.ja.md)
- [OverAct：AIによる不要な個人情報アクセス](../surveys/agent-safety/2026-arxiv-2610.01508.ja.md)
- [CoDeL：攻撃と防御を共進化させるプロンプト注入対策](../surveys/agent-safety/2026-arxiv-2609.34463.ja.md)

- [危険な3条件（Lethal Trifecta）](../surveys/security-governance/2025-lethal-trifecta.ja.md)
- [OWASP エージェント型アプリケーションの10大リスク](../surveys/security-governance/2025-owasp-agentic-top10.ja.md)
- [Meta：エージェントの Rule of Two](../surveys/security-governance/2025-meta-rule-of-two.ja.md)
- [Google：AIセキュリティの防御戦略](../surveys/security-governance/2025-google-ai-security-frontier.ja.md)
- [CSA：MAESTRO 脅威モデリング](../surveys/security-governance/2025-csa-maestro.ja.md)
- [NVIDIA：Open Agent Safety Platform](../surveys/security-governance/2026-nvidia-open-agent-safety.ja.md)

## 2026-10-29

- [AIエージェントは自由な研究を進められるか](../surveys/agent-safety/2026-open-ended-ai-research-shadow-evaluation.ja.md)
- [AI生成Terraformの失敗パターンと防御策](../surveys/cloud-resilience/2026-ai-generated-terraform-guardrails.ja.md)
- [AIエージェントと人による教育対話の行動ラベル付け](../surveys/human-ai-collaboration/2026-coding-agents-behavioral-labeling.ja.md)
- [Anthropicのソース管理再設計：Scion（再確認）](../surveys/coding-agents/2026-anthropic-scion-source-control.ja.md)

## 2026-10-28

- [自宅サーバー25年の変化：仮想化からAIへ](../surveys/cloud-resilience/2026-home-server-evolution.ja.md)
- [メルカリの全社エージェント活用とAIセキュリティ統制](../surveys/security-governance/2026-mercari-ai-security-governance.ja.md)
- [Scion解説：Gitの前提とエージェント規模の開発基盤](../surveys/coding-agents/2026-scion-qiita-design-review.ja.md)
- [Check PointとDaybreak：脆弱性調査から防御へ](../surveys/security-governance/2026-check-point-daybreak.ja.md)
- [ハーネス蒸留でエージェントの周辺設計はどう変わるか](../surveys/coding-agents/2026-harness-distillation-commentary.ja.md)
- [現代AI入門：モデルから思考するシステムへ](../surveys/coding-agents/2026-thinking-systems.ja.md)
- [知識労働のベンチマークは何を測るべきか](../surveys/human-ai-collaboration/2026-knowledge-work-benchmark-design.ja.md)
- [tfdrift：IaCドリフトの重要度分類と通知の削減](../surveys/cloud-resilience/2026-tfdrift-severity-taxonomy.ja.md)
- [2026年AIエージェント動向：企業導入と業務の再設計](../surveys/human-ai-collaboration/2026-state-of-ai-agents-report.ja.md)

## 2026-10-27

- [Claude Duetの安全設計](../surveys/security-governance/2026-claude-duet-safety-privacy-security.ja.md)
- [Claude Codeの記事公開時の漏えい経路](../surveys/security-governance/2026-claude-code-publication-leak-paths.ja.md)
- [AIエージェントによるコード移行と仕様駆動開発](../surveys/coding-agents/2026-microsoft-agentic-code-modernization.ja.md)
- [Claude Codeチームのコードレビュー](../surveys/coding-agents/2026-claude-code-review.ja.md)
- [Cloud Computing & DevOps：2025–2026年の研究動向](../surveys/cloud-resilience/2026-cloud-devops-research-insights.ja.md)
- [Anthropicのソース管理再設計：Scion](../surveys/coding-agents/2026-anthropic-scion-source-control.ja.md)
- [Anthropic Form S-1](../economics/2026-anthropic-s1.ja.md)

## 2026-10-26

- [AIDB記事レビュー：禁止の次の統制](../surveys/security-governance/2026-shadow-ai-ban-pii-governance.ja.md)
- [再帰的自己改善（RSI）：証拠の読み分け](../surveys/articles/2026-rsi-evidence-review.ja.md)
- [Agentic Inequality：AIエージェントを使える力の格差](../surveys/security-governance/2025-agentic-inequality.ja.md)
- [SequenceFI：タイミングを指定するマイクロサービス障害注入](../surveys/cloud-resilience/2026-sequencefi.ja.md)
- [Agentic Overconfidence：AIエージェントの自信は成功率と一致するか](../surveys/agent-safety/2026-agentic-overconfidence.ja.md)
- [人とAIの協働で、目標を独立した共有情報として扱う](../surveys/human-ai-collaboration/2026-goals-first-class-abstractions.ja.md)

## 2026-10-25

- [生成AI導入と生産性・コミュニケーション活動](../surveys/human-ai-collaboration/2026-genai-workplace-productivity-communication.ja.md)
- [日常の人・LLM対話における非公式学習](../surveys/human-ai-collaboration/2026-informal-learning-human-llm.ja.md)
- [サブエージェント統合](../surveys/coding-agents/2026-fold-subagents-main-loop.ja.md)
- [マルチクラウド・セキュリティ設計](../surveys/security-governance/2026-multi-cloud-security-architecture.ja.md)
- [Neuro-Formal Verification](../surveys/coding-agents/2026-neuro-formal-verification.ja.md)
- [報酬ハッキングとミスアラインメント](../surveys/agent-safety/2025-reward-hacking-emergent-misalignment.ja.md)
