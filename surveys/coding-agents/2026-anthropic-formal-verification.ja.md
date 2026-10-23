**日本語** | [English](2026-anthropic-formal-verification.md)

# LLMによる形式的ソフトウェア検証：批判的サーベイ

## 書誌情報・確認状態

- 一次資料 [F1]：[LLMs are making formal software verification feasible at a much larger scale](https://www.anthropic.com/research/formal-verification)、Anthropic / Theorem、2026-10-22公開。
- 掲載著者：Keane Lucas、Aengus Lynch、Luna Tong、Luke Champine、Zygi Straznickas、Dino Distefano、Harshikaa Agrawal、Evyatar Ben Asher、Ava Howell、Sami Jawhar、Chris Rohlf、Nickolai Zeldovich、Nicholas Carlini、Rajashree Agrawal、Jason Gross。
- 資料種別：研究機関の研究記事。技術付録・公開成果物を伴うが、この記事の査読会議・DOI・arXiv IDは未確認。
- 確認日：2026-10-24 JST。一次HTMLの主要節・限界を読了。[技術付録 F2](https://www-cdn.anthropic.com/files/4zrzovbb/website/6867eadf760258fa8b42a504600cd3c036d16358.pdf)の定理・インタプリタ部分、[公開証明リポジトリ F3](https://github.com/theorem-labs/oss-verify-proofs)のREADMEを確認。
- 証明の独立チェック、バイナリ再ビルド、コード監査、再現実験は未実施。対象を絞ったサーベイノートであり、独自実験・体系的文献レビューではない。

## 研究の問い・手法

AIによる変更の受入判定に、テストだけでなく機械検査可能な証拠を使えるか。F1はfuzz harnessからRISC-Vバイナリ上の仕様を構成し、Claudeが生成する証明をRocqで検査する。123ライブラリ・239入口、受理された証明約1.8億行を報告。ただし入力64 MB未満、単一スレッド・静的バイナリ、モデル化された実行環境という条件がある。数値は著者報告であり追試結果ではない。[F1「Turning tests into proofs」]

## 証拠と読み方

| 出典 | 確認した事項 | 評価上の意味 |
|---|---|---|
| F2「What our OSS-Fuzz proofs prove」 | 通常版と計装版の非クラッシュ性、モデル上の観測可能な振る舞いの一致 | 「検証済み」の前に定理と前提を読む |
| F3 README | 公開版は25ライブラリ・60入口。agreementを証明し、停止性は保証しない | F1のプロジェクト全体の件数と公開範囲を区別する |
| F3「What a proof does not say」 | 特定のコンパイル済み成果物と到達可能なharnessの範囲が対象 | ソース更新や実行環境変更後の適用可否は別途評価する |

F2のインタプリタ実験も、形式意味論に対する証明とCPythonとの経験的な一致を区別している。高いテスト一致率から意味論の完全一致は導けない。[F2「Building a Python interpreter in Rust」]

## 限界・妥当性への脅威

F1の結果は、任意のx86/ARM配備やライブラリ全入口の安全性を確立しない。[F1「Limitations」]

本サーベイの考察：受入判定は「ソース版・バイナリ・harness・定理・実行モデル・検査器」の組に結び付けるべきだと考える。いずれかが変われば、証明の再利用可否を再評価する。証明行数だけでは利用者に必要な性質を保証したか判断できない。生成の費用対効果も、成功した証明だけでなく失敗試行、所要時間、資源消費を含めて評価する必要がある。

研究全体と公開成果物の件数差は、まず範囲の違いとして追跡する。現行の公開定理を「必ず正常終了する」と一括して説明することも避ける。[F3]

## 関連研究との比較

以下は概念上の比較であり、同条件の性能比較ではない。

| 既存ノート | 本サーベイでの比較軸 |
|---|---|
| [FlowAgent](2026-flowagent.ja.md) | テスト合格と明示的な定理の成立の違い。どちらも修正が意図を保つかの確認が必要 |
| [SlopCodeBench](2026-slopcodebench.ja.md) | 性質の証明とは別に、構造・保守性を評価する |
| [自己複製AI](../agent-safety/2026-anthropic-self-replicating-ai.ja.md) | 個別ソフトウェアの保証と、環境全体のエージェント封じ込めは別の問い |

## 無料で実施する再現・確認計画

未実施の提案：F3の公開対象を1件選び、コミット・バイナリハッシュを固定し、前提を確認して公開ツールチェーンで既存証明を再検査する。検査器版、仮定、時間、最大メモリ、結果、未確認事項を記録する。有料推論APIは不要だが、AIによる証明生成そのものの再現ではない。F3は大きなメモリ需要を示しているため、実行前に対象1件の必要資源を見積もる。

次段階では同一harnessに対して予算を固定したfuzzingと証明検査を比較し、失敗も残す。資源不足による失敗を定理の反証とは扱わない。

## 活用状態・未確認事項

**提案のみ。試行・採用・効果測定は未実施。** 依存ライブラリのレビューに、定理の対象範囲と成果物の同一性を添える用途が候補。

次に確認すること：F3の公開コミット固定、F1/F2と選定対象の照合、[実行意味論](https://github.com/theorem-labs/rocq-linux-process-semantics)の確認、修正前後の意図保持、生成費用と検査費用の分離。

## 参考文献

- F1：[Anthropic研究記事](https://www.anthropic.com/research/formal-verification)。
- F2：[技術付録](https://www-cdn.anthropic.com/files/4zrzovbb/website/6867eadf760258fa8b42a504600cd3c036d16358.pdf)。
- F3：[Theorem OSS Verify証明・検査資料](https://github.com/theorem-labs/oss-verify-proofs)。更新されうるREADMEを2026-10-24に確認。実行未実施。

[テーマ索引](README.ja.md) | [サーベイ索引](../README.ja.md) | [読書一覧](../../docs/reading-list.ja.md) | [リポジトリREADME](../../README.ja.md)
