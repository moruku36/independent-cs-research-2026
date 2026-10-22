**日本語** | [English](2025-heterogeneous-gpu-llm-serving.md)

# Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs — 異種GPUでのLLM推論の費用対効果

## 人・PMO向けの要点

- **何が分かった**：リクエストごとに負荷のかかる資源が違うため、LLM推論は1種類のGPUより、複数種類のGPUを混ぜたほうが費用対効果が高くなりうる。著者らは6種類のGPUを計測し、価格予算とリアルタイムのGPU空き状況のもとで、どのGPUを借りるか、モデルのレプリカをどう配置するか、リクエストをどう振り分けるかを決めるスケジューラ（混合整数線形計画法、MILP）を作った。同じ価格予算で、ベースライン比、スループットが最大41%（平均20%）向上、またはレイテンシが最大54%（平均20%）低下したと報告している。
- **何に使える**：負荷の形（計算が重いプロンプト、メモリが重い長い出力）でGPUを選ぶ考え方と、「一番大きいGPUを買う」ではなく最適化問題として扱う見方。
- **注意点**：読めたのは論文の前半（要旨から§4.2の途中まで）のみ。計測は6種類のGPU・2つのLlama3モデル・9種類の負荷に限られ、計測時点のクラウド価格と空き状況に依存する。著者自身の結論と限界は確認できていない。
- **次の一手**：未実施。再現・コード確認・価格の再確認は行っていない。

## サーベイ記録

- **状態**：**部分読了**。一次HTMLを要約型の取得ツール経由で確認したが、抽出は§4.2の途中で終わっており、手法の残り、評価の全体、議論、結論、付録（プロファイリング、議論）は**見ていない**。PDFとの照合・引用文献の精読・再現は未実施。以下の数値は当該抽出の報告どおりで、PDFで再確認が必要。
- **題名・著者・年・会場・DOI／arXiv ID・一次URL**：*Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs*／Youhe Jiang, Fangcheng Fu, Xiaozhe Yao, Guoliang He, Xupeng Miao, Ana Klimovic, Bin Cui, Binhang Yuan, Eiko Yoneki／年はarXiv IDから2025年と推定（v2。提出日・改訂日は表示されず）／キーワードに「Machine Learning, ICML」とあるが、**採択・会場は未確認**。[arXiv:2502.00722v2](https://arxiv.org/abs/2502.00722v2)、[HTML](https://arxiv.org/html/2502.00722v2)。
- **確認日・対象version**：2026-10-22／v2。
- **研究の問い**（論文の記載）：
  1. 異種のGPU資源でLLMを提供すると、同種のGPU資源より費用対効果を高められるか。
  2. 高められるなら、どうすればさらに高められるか。
- **手法・データ・比較条件**（読めた範囲）：
  - **ベンチマーク**：GPU 6種類（A6000、A40、L40、A100、H100、4090）、モデル2種類（Llama3-8B、Llama3-70B）、ShareGPT・WildGPT・Azure-Traceから作った9種類の負荷。負荷は、計算集約型（入力が長く出力が短い）とメモリ集約型（入力が短く出力が長い）に分類される。ここから、費用対効果の3つの要因（GPUの構成、配置設定、負荷の割り当て）を特定している。
  - **問題設定**：価格予算と空き状況の制約のもとでGPU構成を選び、GPUを並列化戦略付きの提供グループにまとめ、負荷をレプリカに割り当てて、入ってくる全負荷の完了時間（makespan）を最小化する。
  - **スケジューラ**：MILP。ヒューリスティクスと二分探索で高速化し、複数モデルの提供にも拡張。1回限りのプロファイリング手順は付録に記載（未確認）。ベースラインは同種・異種の代替手法だが、正確な定義は未確認。
- **主張と証拠**（報告どおり）：
  - データセンター向けGPU（H100、A100）は、Llama3-70Bの計算集約型の負荷に向く。
  - ワークステーション向けGPU（A40、A6000、L40）はメモリ集約型の負荷に向き、価格あたりのメモリ帯域は平均1.2倍、メモリ容量は1.8倍（データセンター向けGPU比）。
  - 消費者向け4090はLlama3-8Bで良好で、価格あたりのメモリ帯域はA100/H100の約1.9倍。
  - 適切なGPU種類の選択で費用対効果が最大2.27倍、最適な配置設定でシステム性能が最大2.61倍向上。
  - 同じ価格予算でのエンドツーエンド：さまざまな負荷トレース、GPU空き状況の変化、複数モデル提供でも、ベースライン比、スループット最大41%（平均20%）向上、またはレイテンシ最大54%（平均20%）低下。
- **限界・妥当性への脅威**：著者の限界の記述は**未確認**。以下は論文の記述ではなく当方の所見：評価は6種類のGPU・2つのモデル規模・9種類の負荷に限られる。結果は計測時点のクラウド価格と空き状況に依存する。「価格あたり」の比較は価格が変わるたびに動く。大規模でのMILPの計算コストは確認できていない。
- **関連研究との比較**：未確認（関連研究の節を見ていない）。上の数値を、他の推論システムに対する順位として読まない。
- **無料で実施できる再現案**：ベンチマークはGPUのレンタルが必要で、無料では再現できない。無料の代替として、最適化問題を小さなMILPとして書く（オープンソースのソルバーなどを使う）。価格・スループット・空き状況は**架空の値**を使い、予算や負荷の構成を変えたときに選ばれるGPUの組み合わせがどう変わるかを見る。定式化の発想を試すだけで、論文の数値の検証にはならない。未実施。
- **活用状態**：案として提案（下記）／試行なし。
- **未確認点・次の確認**：公開日と会場、§4〜§6の全体と付録（プロファイリング、議論）、著者の結論と限界、ベースラインの定義、コードの公開有無、全数値のPDF照合。

## 試す価値のある発想（論文が実証したものではない）

社内のLLMサービスでGPU容量を見積もるとき、まず負荷をプロンプト重視と出力重視に分け、1つのGPU種類で全部をまかなうのではなく、GPUクラスごとに「価格あたりの性能」を比べる。上の比率に頼る前に、最新の価格と空き状況を確認する。

## English

The paper asks whether LLM serving over heterogeneous cloud GPUs is more cost-efficient than over homogeneous GPUs, and how to improve it further. It benchmarks six GPU types, two Llama3 models, and nine workloads, finds that GPU type and deployment configuration each shift cost-efficiency by up to 2.27x and 2.61x, and proposes a MILP scheduler that chooses GPU composition, deployment, and workload assignment under a price budget. Reported gains at equal budget: up to 41% (average 20%) throughput or up to 54% (average 20%) latency. Only part of the paper was read, the authors' conclusion and limitations were not seen, venue is unconfirmed, and nothing was reproduced.

[日本語・英語索引 / Collection index](README.ja.md) | [読書一覧 / Reading list](../../docs/reading-list.ja.md)
