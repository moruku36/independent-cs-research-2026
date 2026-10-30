**日本語** | [English](2026-qers-pqc-iot.md)

# QERS：IoT通信における耐量子暗号の評価

## 3行概要

- ESP32-C6とRaspberry Pi CM4を用い、MQTT・HTTP・HTTPSのPQC負荷とセキュリティを比較する実験的プレプリント。
- 遅延、CPU、電力などを重み付きスコアに集約し、効率と安全性の優先度によって評価が変わる。
- 結果は実験条件とスコア設計に依存し、本文に結果記述の不一致がある。

## 出典と確認範囲

- 著者：Jonatan Rassekhnia、2026-01-19。
- 指定された[ResearchGate](https://www.researchgate.net/publication/399931145_Quantum_Encryption_Resilience_Score_QERS_for_MQTT_HTTP_and_HTTPS_under_Post-Quantum_Cryptography_in_Computer_IoT_and_IIoT_Systems)はアクセス制限。DOI 10.48550/arXiv.2601.13423 により[arXiv v1](https://arxiv.org/html/2601.13423v1)を同一研究と照合し、抄録・方法・結果を部分確認した。HTMLの題名はResearchGateの表記と異なる。
- 論文著者の報告。実験・コード・測定データ・査読状況の独立検証は未実施。

## 内容と結果

Basic、Tuned、Fusionの3種類の複合指標を提案。著者の表IIIではMQTTがBasic/Tunedで高く、HTTPSが安全性を重視するFusionで高い。スコアは指標の選択や重みに左右され、暗号強度や安全性を単独で証明するものではない。MQTTはTLS上でも動くため、MQTTとHTTPSを一般的なセキュリティの優劣として直接比較しない。

## 注意点

本文IV-BはHTTPSのFusionスコアが低下すると説明する一方、IV-Aと表IIIではHTTPSが最高。V節は距離に伴う全プロトコルのFusion低下と書くが、表IIIではMQTTは同値、HTTPとHTTPSはわずかに増加している。矛盾は未解決であり、原データと実装を確認する必要がある。PQC接続構成と証明書の詳細も導入前に追検証する。

## 実務への活用

PQC移行のPoCで、対象機器ごとにTLSハンドシェイク、遅延、CPU、メモリ、電力を従来方式と比較する。暗号方式・認証・接続再利用を揃えたうえで評価し、総合スコアだけでなく元の測定値も残す。

[セキュリティ・ガバナンス索引](README.ja.md)
