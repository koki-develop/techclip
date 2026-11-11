---
date: "2026-11-11T18:09:40+09:00"
title: "Google、AMDと共同開発の機密コンピューティング対応TPU「8tx」と帯域幅2倍の「8i Max」を発表"
description: "GoogleがAMD EPYC Turinと組み合わせた機密コンピューティング向けTPU「8tx」と、メモリ帯域幅・SRAMを倍増させた長文コンテキスト推論向けTPU「8i Max」を発表し、他社製チップへの依存低減とAIハードウェア戦略の拡充を図る。"
tags:
  - AI
  - Other
references:
  - "https://techcrunch.com/2026/11/10/google-broadens-its-ai-hardware-portfolio-with-two-new-specialized-chips/"
  - "https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/tpu-8i-max-and-8tx/"
  - "https://www.servethehome.com/google-tpu-8tx-8i-max-amd-epyc-turin/"
---

## 概要

Googleは11月9日から10日にかけて、第8世代TPU(Tensor Processing Unit)ポートフォリオを拡張する新型チップ「TPU 8tx」と「TPU 8i Max」を発表した。これにより、Googleは単一年度で4種類のTPUシステムを投入する初めてのケースとなった。TPU 8txは機密コンピューティングに対応したAIトレーニング・推論向けチップ、TPU 8i Maxは長文コンテキスト推論向けにメモリ帯域幅を倍増させたチップで、いずれも他社製チップへの依存を減らしながら独自のAIチップ戦略を加速させる狙いがある。背景には、Microsoft、Amazon、OpenAI、Anthropicなど競合各社がそれぞれ独自のカスタムAIチップ開発を進めているという業界全体の動きがある。

## TPU 8tx：機密コンピューティングとAMDとの協業

TPU 8txは、既存のTPU 8tと同一のシリコン基盤を用いながら、ホストCPUにAMDの第5世代EPYC(Turin)を採用した点が最大の特徴だ。従来、データは保存時やネットワーク転送時には暗号化されるものの、処理中はメモリ上で平文として展開されるという課題があったが、TPU 8txはこれをハードウェアレイヤーで解決し、機密データやモデルウェイトを処理中も保護する。構成としてはデュアルソケットのTurinが128本のGen5レーンを提供し、PCIe Gen5 x16インターフェースで4基のTPUと高速NICを接続、オーバーサブスクリプションを避けるBoardflyネットワークトポロジー(最大ホップ数7)を採用している。性能面ではTPU 8t比で最大2倍のレイテンシ低減を実現しつつ、性能ペナルティはほぼゼロに抑えられているという。カスタム推論ネットワークによりトレーニング中の推論実行も可能になり、企業は自社データを外部に移動させずにモデル蒸留を行える。AMDにとっても、非AMDアクセラレータ系システムでEPYCを採用させた大型案件であり、機密コンピューティング分野における競争力を示す成果となった。

## TPU 8i Max：帯域幅とSRAMを倍増し長文コンテキストに対応

TPU 8i Maxは、低レイテンシ推論向けのTPU 8iを2基、1つのマルチチップパッケージに統合したチップだ。これにより演算能力、HBM帯域幅、SRAM容量をいずれも倍増させている。具体的には384GBの高帯域幅メモリ(従来のTPU 8i比で約1.3倍)を搭載し、HBM帯域幅は17.2TB/s、オンチップSRAMは768MBと、こちらは従来のTPU 8i比で2倍の値になった。既存ラック内に2倍のシリコンを搭載できるため、平方フィート当たりの計算性能も大幅に向上する。この設計は、百万トークン規模のコンテキストウィンドウを処理するエージェント型ワークロードに最適化されている。

## ソフトウェアスタックの強化とビジネスへの影響

Googleはハードウェアの拡充と並行して、ソフトウェア面での利便性向上も進めている。PyTorchコードの書き換えを不要にする「TorchTPU」をオープンソース化し、vLLMやSGLangなどの推論エンジンにも対応した。また、Claude Code、Cursor、Google Antigravityと統合する「TPUエージェントスイート」による自動化、KV転送レイテンシと初トークン出力時間(TTFT)を90%超削減する「TPU Sync」のオープンソース化、ジョブ起動時間を最大5倍・障害復旧を最大4.5倍高速化するGKEの動的スライシング機能、Google DeepMindランタイム「Cloud Pathways」の全顧客への提供開始など、一連の最適化を打ち出した。InferenceXおよびAgentXベンチマークでは最先端の価格対性能を達成したとしている。Googleは現在、frontier labs、トレーディング企業、小売業者、大学など、ほぼ100社の顧客を抱えており、今回の新チップ投入はAI基盤の多様化が進む中でNvidia一社依存からの脱却を図る動きの一環として注目される。
