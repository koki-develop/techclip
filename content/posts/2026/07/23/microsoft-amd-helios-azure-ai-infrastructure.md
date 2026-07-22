---
date: "2026-07-23T02:32:22+09:00"
title: "MicrosoftとAMDが提携拡大、次世代AIインフラ「Helios」をAzureに大規模導入へ"
description: "MicrosoftはAMDとの長期戦略提携を拡大し、Instinct MI455X GPUや6th Gen EPYC「Venice」CPUを搭載する次世代ラックスケールAIインフラ「Helios」をAzureに導入すると発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://www.globenewswire.com/news-release/2026/07/20/3329775/0/en/Microsoft-to-Deploy-Next-Gen-AMD-Instinct-and-AMD-EPYC-Processors-as-the-Companies-Expand-Their-Long-Term-Strategic-Partnership.html"
  - "https://blogs.microsoft.com/blog/2026/07/20/microsoft-expands-azure-ai-and-hpc-infrastructure-with-amd/"
  - "https://www.tomshardware.com/tech-industry/artificial-intelligence/microsoft-will-deploy-amds-helios-rack-scale-ai-accelerator-at-scale-on-azure-radeon-instinct-mi455x-and-epyc-venice-power-will-be-available-through-redmonds-cloud-infrastructure"
---

## 概要

Microsoftは7月20日、AMDとの長期戦略提携をさらに拡大し、AMDの次世代ラックスケールAIインフラ「Helios」をAzureに導入すると発表した。HeliosはAMD Instinct MI455X GPU、6th Gen AMD EPYC「Venice」CPU、Pensandoネットワーキング、ROCmソフトウェアスタックを統合したフルスタックのオープンプラットフォームで、フロンティアAIモデルの学習・推論をはじめ、データ準備や強化学習、エージェント連携など幅広いワークロードに対応する。出荷開始は2026年後半を予定している。AMDのリサ・スーCEOは「AMDとMicrosoftはこれまで数年間にわたり高性能インフラを共に構築してきた」と述べ、Microsoftのサティア・ナデラCEOも「顧客は学習・推論・データ準備・検索・強化学習に最適化されたAIインフラを必要としている」とコメントし、両社の関係の深化を強調した。

## 新VMファミリーと技術仕様

今回の提携拡大に伴い、MicrosoftはAMDの最新技術を搭載した3種類の新しいAzure仮想マシンを展開する。AIの推論ワークロード向けには「ND MI455X v7」、データ処理やAIシステム向けの「Azure HDv2」、半導体設計(EDA)や技術計算向けの「Azure HXv2」がラインナップされる。HDv2はおよそ500物理コアの6th Gen AMD EPYC CPU、4テラバイトのRAM、32テラバイトのローカルNVMeストレージ、400Gbの Azure Boostネットワーキングを備える。一方HXv2は176コアの6th Gen EPYC CPUを搭載し、クロック周波数は5GHzを超え、コアあたりのアドレス可能キャッシュも50%増加、AMDの3D V-Cache技術を採用する。RAMは2〜4テラバイトの構成が選べるほか、800GbのInfiniBand接続にも対応し、大規模なEDAワークロードや科学シミュレーションの高速化を狙う。

## 背景と今後の展望

生成AIの急速な普及により、クラウド事業者各社はフロンティアモデルの学習・推論需要増大に対応するインフラ拡張を迫られている。今回の発表は、MicrosoftがNVIDIA一辺倒だったAIインフラ戦略においてAMDとの協業を一段と深め、顧客に選択肢と柔軟性を提供する狙いがあるとみられる。AMDのマーク・ペーパーマスターCTOはHXv2について「複雑なEDAワークロードのスケーリングにおいて重要であり、性能とスケーラビリティの向上に期待している」とコメント。EDA大手SynopsysのShankar Krishnamoorthy氏も、この提携が「次世代AIシステムを精度とスケールをもって顧客に届けるという共通のビジョンを示すものだ」と評価している。Helios搭載インフラは2026年後半から段階的に提供が始まる見込みで、Azure上でのAIワークロード処理能力の底上げが期待される。
