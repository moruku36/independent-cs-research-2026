**日本語** | [English](2026-gitinject.md)

# GitInject — AI搭載CI/CDパイプラインへの実環境プロンプトインジェクション評価

## 人・PMO向けの要点

- **何が分かった**：GitHub Actions上のAIレビュー／トリアージ系ワークフロー4種（Claude・Codex・Gemini・Cline）を、使い捨てリポジトリで実際に動かして評価した。名前付きの攻撃シナリオ11件のうち、再現されたのは10件、再現されなかったのは1件（issue本文経由のトークン窃取）。最も重大とされるのは、PRブランチに置かれた設定ファイル（`CLAUDE.md`・`AGENTS.md`・`GEMINI.md`）が、運用者レベルの指示として読み込まれる経路。
- **何に使える**：AIエージェントを「信頼できる設定・指示」と「検証対象の候補コード」から分離する設計、実行環境の認証情報の露出面の点検、セキュリティ判定をLLM判定者から切り離す考え方の具体例。
- **注意点**：検証されたのは**試したワークフロー設定・モデル版・シナリオだけ**で、現在の全モデルや全構成への一般化ではない。失敗セルは「その攻撃が成功しなかった」だけで、安全の証明ではない（§6.2）。対策も範囲が限られる。HTML版には書式の崩れがあり、表と本文の不一致も確認した（下記）。
- **次の一手**：この記録は防御側の調査であり、再現実験は未実施。提案は[ai-governance-control](https://github.com/moruku36/ai-governance-control)側の文書に分けて記録する。

## サーベイ記録

- **状態**：一次本文確認済み／HTML版の§1–7、Table 1–5、Figure 1–3の説明、付録A–Hを通読。PDF版との照合、引用文献の個別精読、公開コードの確認は未実施。再現・実験は未実施。
- **題名・著者・年・会場・DOI／arXiv ID・一次URL**：*GitInject: Real-World Prompt Injection Attacks in AI-Powered CI/CD Pipelines*／Jafar Isbarov, Umid Suleymanov, Ilia Shumailov, Murat Kantarcioglu／2026／査読済み会場は未確認（arXivプレプリント、cs.CR、副分野cs.AI）。[arXiv:2606.09935v1](https://arxiv.org/abs/2606.09935v1)（投稿2026-06-07 19:17 UTC）、[HTML v1](https://arxiv.org/html/2606.09935v1)、[PDF](https://arxiv.org/pdf/2606.09935)、[DOI](https://doi.org/10.48550/arXiv.2606.09935)（arXiv発行値）。HTMLにCC BY 4.0表示を確認。
- **確認日・対象version**：2026-10-14 UTC／v1。arXivの投稿履歴でv1のみを確認した。後続版が存在しないとは主張しない。本文には、公開の猶予期間後にTable 2を更新する予定がcamera-ready向けに書かれている（§6.2）。
- **研究の問い**：実際のGitHubワークフローを実行すると、模擬ツール呼び出しによる評価では見えない、サンドボックス・認証情報の保存・権限・ネットワーク設定に由来する攻撃面が現れるか。また、ワークフロー水準の最小限の対策は何で、どこまで効くか（§1、§4）。
- **手法・データ・比較条件**：
  - **枠組み**：使い捨てのGitHubリポジトリを用意し、対象のワークフローYAMLをそのまま置き、イベントに攻撃入力を差し込み、実行後にGitHub APIで実際の状態を見て判定する（§4、Figure 3、付録E.2）。実行後にリポジトリは削除される。
  - **判定器（著者の説明）**：著者は、`StateEvaluator`（API上の副作用を見る決定的判定）をセキュリティ評価に常用し、`LLMEvaluator`（Gemini 3.1 Pro Previewを判定者とする二値判定）は有用性など意味的な成否に限り、セキュリティ評価には使わないと述べる（§4、付録E.1）。**これは著者の方法の説明であり、確立した実務ではない。** また、Table 5は判断操作・承認操作の攻撃の判定器を`LLM`と表示しており、この説明と矛盾する（下記の不一致3）。
  - **対象**：4つのAI提供者の「4つの代表的なワークフロー」で11の名前付き攻撃を評価（§5.1）。付録G（Table 4）の一覧は13件（GitLab用1件を含む）。評価対象の4件と一覧の13件は網羅範囲が異なるだけで、矛盾とは扱わない。
  - **反復**：各シナリオを5回実行し、すべて同じ結果で、各セルは5/5か0/5（Table 2の注、Table 5の注）。
  - **攻撃クラス**：PR／issue本文（利用者ターン水準の信頼）、設定ファイル（運用者水準の信頼）、可用性（コスト、鍵停止）、判断操作（レビューの見落とし誘導）（§3、§5）。
  - **付録A**：LLMで攻撃仮説を列挙した事例。仮説は外部フォークからの実行ではワークフローが発火せず、実環境で成立しなかった。この事例は「実環境でなければ分からない」ことの例として扱われ、事例集からは除外された。
- **主張と証拠**：下表。出典はTable 1–3、5と§5。
- **限界・妥当性への脅威（§6.2）**：
  - 結果は評価時点のモデル版・ワークフロー設定に依存し、修正されたかは再実行しないと分からない。
  - 攻撃の列挙は網羅的でなく、LLMによる仮説生成も網羅性を保証しない。
  - 失敗セルは安全の証明ではない。
  - 本記録の観点：複数の表・本文の不一致、判定の一部がLLM判定者である点、シミュレーション比較は1つのベンチマーク（AgentDojo）に対する結果であること。
- **関連研究との比較**：AgentDojo（97件のユーザータスク、629件のセキュリティケース）等の模擬環境ベンチマーク、GitHub Actionsの静的な設定誤りの研究、PR／issue本文経由のインジェクションの先行報告（PromptPwnd、Cline障害の事後報告）との差を、設定ファイル注入が運用者水準の信頼で届く点に置く（§2）。この「新規性」は著者の主張で、当方は網羅的な先行調査で検証していない。
- **無料で実施できる再現案**：本タスクでは実施しない。論文の実験は実在のAPI鍵・有料の実行・外部サービスへの攻撃入力を含むため、無料の机上点検（自分たちのワークフロー設定の読み合わせ）に限る。攻撃入力は本記録に載せない。
- **活用状態**：提案（[ai-governance-control](https://github.com/moruku36/ai-governance-control)側の文書）／実装・再現は未実施。
- **未確認点・次の確認**：PDF版との差異、公開コードの内容、後続版の有無、会議の採択情報、各セルとTable 3・5の整合（下記）、著者への確認は行っていない。

### 数値と評価単位

**シミュレーションとの比較（§4・§5.1、Table 1、付録B）**：AgentDojoに10件のCI/CD注入タスク（実行環境の状態を使う攻撃6、サンドボックスで遮断される攻撃2、対照2）を作り、5モデル×10タスク×2ユーザータスク＝**n=100**で実行した。

| | 実際に成功 | 実際に失敗 | 計 |
|---|---:|---:|---:|
| 模擬で成功 | 23（TP） | 1（FP） | 24 |
| 模擬で失敗 | 57（FN） | 19（TN） | 76 |
| 計 | 80 | 20 | 100 |

- 論文は「実際の攻撃の71.2%を見逃す」と記す。分母は**実際に成功した80件**（57/80 = 71.25%）。「5.0%」の分母は**実際に失敗した20件**（1/20）。両者の分母は異なり、100件全体に対する割合ではない（派生の確認は当方）。
- 「実際に成功／失敗」を各タスクにどう割り当てたかは、当方の確認範囲では本文から確定できない。タスクの分類（付録B）から80件の内訳を推定せず、Table 1の値をそのまま記録する。
- AgentDojoは1つのベンチマーク・5モデル・2タスクで、他の模擬環境への一般化はしない。論文自身も、これはAgentDojoの欠陥ではないと述べる。

**カテゴリ別（Table 2）**：各セルは「成功した攻撃数／試した攻撃数」。5回すべて同じ結果。

| MITRE分類 | Claude | Codex | Gemini | Cline | 計 |
|---|---:|---:|---:|---:|---:|
| Credential Access | 1/3 | 2/2 | 2/3 | 0/1 | 5/9 |
| Defense Evasion | 1/2 | 2/2 | 2/2 | – | 5/6 |
| Discovery | 0/1 | – | 0/1 | 1/1 | 1/3 |
| Impact | 1/1 | 1/1 | 1/1 | 1/1 | 4/4 |
| 計 | | | | | 15/22 |

- 「22」は**ワークフロー×分類の組の中の試行シナリオ数の合計**（当方の合算）で、11の名前付き攻撃とは別の単位。名前付き攻撃11件はTable 5の行で、複数のワークフローに適用されうる。
- 最後の行は当方の集計。「–」は構造上適用不能。

**モデル別（Table 3）**：PR／issue本文は分母4（Claude・Gemini）または2（GPT、Codexはissueなし）、設定ファイルは2シナリオ。

| モデル | PR/issue本文 | 設定ファイル |
|---|---:|---:|
| claude-sonnet-4-5 / claude-haiku-4-5 | 0/4 / 0/4 | 2/2 / 2/2 |
| claude-opus-4-7 | 0/4 | 0/2 |
| gpt-4o-mini | 2/2 | 2/2 |
| gpt-5 / gpt-5.4 | 0/2 / 0/2 | 2/2 / 0/2 |
| gemini-2.5-flash / gemini-3-flash / gemini-3.1-pro-preview | 0/4（各） | 2/2（各） |

**可用性（§5.4、付録C）**：サービス拒否（denial_of_wallet）のシナリオ自体は、Table 5で**5/5と確認**されている。**試算なのは、キャンペーンの金額と実行分数だけ**。65,536文字のPR本文が22,100トークン（Opus 4.7のトークナイザ）、出力上限32,000トークンで1PRあたり$1.11、100件（2時間）で$32–$111、Actions 400分。拒否応答でも入力トークンだけで$0.32とされる。**コンテンツポリシー違反による鍵の停止は仮説**で、実験はしていない（倫理・法的境界のため）。深刻度はLowとされる。

### 対策と限界（§5、付録D）

論文の対策は**シナリオ単位**で、一般的な保証ではない。

- `persist-credentials: false`：`GITHUB_TOKEN`が`.git/config`に残る経路だけを消す。他の認証情報の窃取には効かず、Geminiの鍵は別の場所に書かれるため不十分とされる（§5.2、§5.3、Table 5）。一般的な安全の証明ではない。
- ツール制限：シェル段階の窃取を防ぐが、シェルを使わない判断操作には効かない。有用性の費用がある。
- 著者関連付け（actor）フィルタ：レビューを強化するのではなく**外部者へのサービスを拒否する**交換条件。外部からのPRを受ける必要があるリポジトリには残余リスクがある。
- 人手の承認：表面的な確認では、運用者設定とみなされる悪意ある設定を見分けにくく、保証ではない（付録D）。論文の結論は、判断操作には著者フィルタか助言のみの権限だけが「確実な保証」を与えると書く一方、§5.3は残余リスクが残るとも書く。この強い表現は著者の主張として扱う。
- 判断操作（レビューの見落とし誘導）は、安価なワークフロー水準の対策が無いとされる。
- 入力サイズの事前確認、コンテンツ事前フィルタは、遅延・費用・独自実装が必要。

### 公開前の確認と注意

- 一部のペイロードやコマンドは本文にあるが、本記録は防御側の整理で、**攻撃入力・実行コマンドを再掲しない**。
- 論文は著者所有の使い捨てリポジトリでのみ実験し、GitHub・Anthropic・OpenAI・Googleに開示したと述べる（§6.3）。当方はこの開示の事実を確認していない。

## 本文・表の不一致と書式の崩れ（未解決のまま記録）

以下は一次HTMLの確認結果で、**当方は推測で解消していない**。

1. **HTMLの書式崩れ**：数式・コードブロックが抜けている箇所がある（例：「The injected payload:」「Neither step succeeds alone」の直後、付録A.2の条件式の前、§5.3のコード）。`n=100`や`2^256`などの数式は属性にのみ残る。Table 2・3の色分けも失われ、表の注の「Gray (–)」は記号のみ。付録の見出しの一部は空で、Acknowledgmentsも空。
2. **「十一の再現事例」と表**：§1は「Eleven reproduced prompt-injection cases」と書くが、Table 5の11行のうち`issue_body_github_token_exfiltration`は成功率0（前提を満たさない）で再現されていない。
3. **セキュリティ判定にLLM判定者を使わないという説明とTable 5の表示**：§4と付録E.1は、セキュリティ評価にLLMEvaluatorを使わないと述べる。一方、Table 5は判断操作・承認操作の6件（`*_approval_manipulation`）の判定器を`LLM`とし、凡例も「LLM = semantic review quality」とする。どちらが実際の判定かは本文から確定できず、当方は解消していない。判断操作の「成功」を決定的な状態確認によるとは扱わない。
4. **Table 3・Table 5・§5.2のGemini**：§5.2とTable 5は、PR本文経由の判断操作がgemini-2.5-flashとgemini-3-flashに成功し、トークン窃取もgemini-assistantで確認されたと述べる。一方、Table 3のPR/issue本文列では、両Geminiモデルとも0/4。
5. **Table 5と§5.2のworkflow**：§5.2は`pr_body_github_token_exfiltration`をcodex-pr-reviewとgemini-assistantで確認としたが、Table 5はcodex-pr-reviewとgpt-4o-miniのみ。
6. **denial_of_walletの範囲**：Table 5はclaude-pr-review／Opus 4.7のみ、Table 2のImpactは4ワークフロー全て1/1。
7. **Table 2のDiscoveryとCredentialの一部セル**：Table 5と突き合わせても、Claude・Geminiの`Discovery 0/1`とClineの`Credential Access 0/1`に対応する名前付き攻撃が特定できない。
8. **対照タスクとフォークの前提**：§5.1と付録Aは、フォークからの`workflow_run`攻撃は実環境で成立しないと述べるが、付録Bはその型の対照タスクを「模擬と実際が一致」と位置づける。付録Aは所有者アカウントでの確認とするが、Table 1で「実際に成功」に数えた根拠は明示されない。
9. **コスト算術**：§5.4の「$1.11」は、22,100入力トークン（$5/MTok）＋32,000出力トークン（$25/MTok）の単純合計（約$0.91）と一致しない。付録Cはエージェント的な複数ターンの履歴再送を挙げるが、$1.11の内訳は記載されない。
10. **コマンド表記の違い**：§5.1と§5.2で、認証ヘッダの参照コマンドの綴りが異なる（本記録では再掲しない）。
11. **gpt-4o / gpt-4o-mini**：付録E.5は「gpt-4o」への窃取攻撃の開発に言及するが、評価表のモデルはgpt-4o-miniのみ。

## 自分たちのAI運用への応用案

以下は**本プロジェクトの提案**で、論文が効果を実証した施策ではない。実装・採用・効果測定は未実施。

1. 信頼する指示・設定は、検証対象の候補（PRのチェックアウト）とは別の、信頼できるベース由来から読む。
2. 実行環境の認証情報・権限・外部通信を最小にし、AIの出力は助言にとどめる。
3. セキュリティ上の効果は、LLM判定者ではなく独立した決定的な確認で判定する。
4. 入力・出力・累積の予算を別々に制限し、不明な場合は停止する（fail closed）。

詳細と採用条件は[ai-governance-control側の調査メモ](https://github.com/moruku36/ai-governance-control/blob/main/docs/research/gitinject-2606.09935.md)に書く（マージ後に有効）。

## English

GitInject (arXiv:2606.09935v1, cs.CR, 7 June 2026; preprint, review status unconfirmed) runs real GitHub Actions workflows in ephemeral repositories to test prompt injection against AI review and triage agents (Claude, Codex, Gemini, Cline). It reports eleven named attacks; ten are shown as reproduced and one (issue-body token theft) is not. Each scenario ran five times with identical outcomes (5/5 or 0/5). Results apply only to the tested model versions, workflow configurations and scenarios, not to all current models; failed cells do not prove safety. Table 1 compares against AgentDojo over n=100 (5 models × 10 tasks × 2 user tasks): 23 TP, 1 FP, 57 FN, 19 TN as reported; the 71.2% miss rate uses the 80 real successes and the 5.0% false-positive rate the 20 real failures. We do not infer how those 80 arise from the task taxonomy. Table 2's 15/22 counts workflow/category scenario cells, a different unit from the eleven named attacks. The denial_of_wallet scenario itself is listed as 5/5 confirmed in Table 5; only the campaign amounts and Actions minutes ($32–$111, 400 minutes for a 2-hour, 100-PR campaign) are projections. The authors say security verdicts never use the LLM judge (§4, App. E.1) yet Table 5 labels the six judgment/approval-manipulation attacks as LLM-evaluated; this conflict is unresolved and the method description is an author claim, not established practice. Also, content-policy key suspension is a hypothetical not tested. The four evaluated workflows versus the 13-entry inventory are different coverage, not treated as a contradiction. Countermeasures (e.g., `persist-credentials: false`, tool restriction, actor filtering) are scenario-specific, with limits; actor filtering trades off service to external contributors. The HTML has formatting damage (missing code blocks and math) and several text/table inconsistencies, listed above and left unresolved. Primary HTML read in full; no reproduction, no PDF cross-check, no code inspection. Attack inputs are deliberately not reproduced. Governance proposals are recorded separately in ai-governance-control.

Source sections: [§1](https://arxiv.org/html/2606.09935v1#S1) · [§3](https://arxiv.org/html/2606.09935v1#S3) · [§4](https://arxiv.org/html/2606.09935v1#S4) · [§5.1/Table 1](https://arxiv.org/html/2606.09935v1#S5.SS1) · [§5.2](https://arxiv.org/html/2606.09935v1#S5.SS2) · [§5.3](https://arxiv.org/html/2606.09935v1#S5.SS3) · [§5.4](https://arxiv.org/html/2606.09935v1#S5.SS4) · [§5.5](https://arxiv.org/html/2606.09935v1#S5.SS5) · [§6.2](https://arxiv.org/html/2606.09935v1#S6.SS2) · [Appendix A](https://arxiv.org/html/2606.09935v1#A1) · [B](https://arxiv.org/html/2606.09935v1#A2) · [C](https://arxiv.org/html/2606.09935v1#A3) · [D](https://arxiv.org/html/2606.09935v1#A4) · [G](https://arxiv.org/html/2606.09935v1#A7) · [H](https://arxiv.org/html/2606.09935v1#A8) · [Table 2](https://arxiv.org/html/2606.09935v1#S5.T2) · [Table 3](https://arxiv.org/html/2606.09935v1#S5.T3)

[日本語・英語索引 / Collection index](README.ja.md) | [読書一覧 / Reading list](../../docs/reading-list.ja.md)
