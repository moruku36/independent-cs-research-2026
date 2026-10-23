**日本語** | [English](2024-dwave-annealing-rsa.md)

# 参考文献候補：D-Wave Advantageによる量子アニーリングとRSA整数分解

## 概要

- **何についてのものか**: D-Wave Advantageによる量子アニーリングでのRSA素因数分解に関する中国の研究報告を、GIGAZINEの記事だけを通して扱った参考候補（本格的なサーベイではない）。
- **何を述べているか**: 記事によれば、D-Wave Advantageで22ビットの整数を、古典計算と組み合わせて50ビットの整数を素因数分解したという。
- **留意点**: 一次論文は未読で、数値は記事の記述にすぎない。RSA-2048が破れることも量子優位も示していない。

**状態：記事経由の限定紹介。一次論文本文未読・書誌未確定・追試未実施。確認日：2026-10-15 UTC。**

これは全文確認済みサーベイではなく、今後のPQC調査用の参考文献候補である。既存のサーベイ7件の読書状態や件数に加算しない。

## 出典と確認範囲

| 項目 | 今回確認できたこと |
|---|---|
| 紹介元 | [GIGAZINE「中国の研究者が量子コンピューターでRSA暗号の解読手法を構築」](https://gigazine.net/news/20241015-rsa-encryption-quantum-computer/)（2024-10-15）を確認 |
| 記事が示す論文題名 | 基于 D-Wave Advantage 的量子退火公钥密码攻击算法研究。原誌本文での表記照合は未実施 |
| 一次論文への導線 | 記事が直接リンクする[学術誌サイトの公式PDF](http://cjc.ict.ac.cn/online/onlinepaper/wc-202458160402.pdf)。今回取得失敗のため本文未読 |
| 著者・掲載先 | 記事は上海大学のワン・チャオ氏ら、Chinese Journal of Computersと紹介。正式な著者一覧・刊行年・巻号・ページは一次資料で未確定 |
| DOI・版 | 一次確認できていないため確定書誌として採録しない |

## 記事から分かる報告範囲

記事は、D-Wave Advantageによる量子アニーリングで22ビット、古典計算との組合せで50ビットの整数分解を報告していると紹介する。この数値は**記事の記述**であり、本ノートによる論文本文の検証や再現結果ではない。

実用RSA-2048の解読実証、実用規模へ拡張できる証明、古典最良手法に対する量子優位の実証としては扱わない。量子アニーリングによる最適化・ハイブリッド手法と、ゲート型量子計算のShor法を混同しない。

## 今後の確認と活用（提案のみ）

[サーベイテンプレート](../../surveys/template.ja.md)に従う精読へ進む前に、公式本文で題名・著者・年・巻号・ページ・DOI・版を照合する。その後、対象整数の選び方、前処理の仮定、古典計算の役割、全処理時間、成功率、比較条件、量子資源を確認する。小規模な整数の実験から、RSA-2048の攻撃費用や実現時期を外挿しない。

用途は暗号解析の報道を評価する際の参考文献探索であり、新しい攻撃コードやPQC機能の採用ではない。無料でできる次の作業は、公開本文の書誌照合と条件表作成。D-Wave実機へのアクセスや実験は開始していない。

## English

Reference candidate identified through a news article; the linked primary PDF could not be retrieved. Full text, complete bibliography and DOI remain unverified; no reproduction. Reported small-instance factoring is not treated as practical RSA-2048 decryption or proof of quantum advantage.

[読書・活用一覧](../reading-list.ja.md) | [論文集索引](../../surveys/README.ja.md) | [README](../../README.ja.md)
