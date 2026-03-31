---
date: "2026-03-31"
title: "CoreWeave、NVIDIA Rubinプラットフォームをクラウドへ統合——推論コスト10分の1、MoE学習GPU数4分の1を実現"
description: "CoreWeaveはNVIDIA Rubinテクノロジーをクラウドプラットフォームへ統合すると発表し、2026年下半期にRubinを最初に展開するクラウドプロバイダーの一つとなる予定。"
tags:
  - Cloud
references:
  - "https://www.coreweave.com/news/coreweave-extends-its-cloud-platform-with-nvidia-rubin-platform"
  - "https://www.hpcwire.com/off-the-wire/coreweave-extends-its-cloud-platform-with-nvidia-rubin-platform/"
  - "https://nvidianews.nvidia.com/news/rubin-platform-ai-supercomputer"
---

## 概要

CoreWeave（Nasdaq: CRWV）は2026年1月、NVIDIA Rubinテクノロジーをクラウドプラットフォームへ統合すると発表した。同社は2026年下半期にNVIDIA Rubinプラットフォームを最初に展開するクラウドプロバイダーの一つとなる予定で、エージェント型AI・大規模推論・大規模インファレンスワークロードの構築・デプロイを支援する。CoreWeaveのCEO Michael Intrator氏は「エンタープライズ顧客は本物の選択肢と、複雑なワークロードを本番スケールで確実に実行できる能力を求めてCoreWeaveを選ぶ」とコメントしており、NVIDIA Rubinプラットフォームはその戦略をさらに強化するものと位置付けている。NVIDIA CEOのJensen Huang氏も「CoreWeaveのスピード、スケール、そして独創性はこの新時代のコンピューティングにおいて不可欠なパートナーだ」と述べている。

## NVIDIA Rubinプラットフォームの技術仕様

NVIDIA Rubinプラットフォームは6種類のチップを極限まで協調設計（コデザイン）することで、AIシステムの構築・デプロイ・セキュリティ確保の新たな基準を打ち立てる。構成要素は以下の通りだ。

- **NVIDIA Vera CPU**：88個のカスタムOlympusコア（Armv9.2互換）を搭載
- **NVIDIA Rubin GPU**：第3世代Transformer Engineを搭載し、NVFP4で50ペタフロップスの計算性能を発揮
- **NVIDIA NVLink 6 Switch**：GPU1基あたり3.6TB/sの帯域幅を実現するGPU間通信スイッチ
- **NVIDIA ConnectX-9 SuperNIC**：高速ネットワークインターフェース
- **NVIDIA BlueField-4 DPU**：AIネイティブなストレージ処理
- **NVIDIA Spectrum-6 Ethernet Switch**：大規模クラスタ向けイーサネットスイッチング

旗艦ラック構成「Vera Rubin NVL72」にはRubin GPUを72基、Vera CPUを36基搭載し、合計260TB/sのトータル帯域幅を誇る。前世代のBlackwellプラットフォームと比較して、推論トークンコストを最大10分の1に削減し、混合専門家（MoE）モデルの学習に必要なGPU数を4分の1に抑えることができるとされている。

## CoreWeaveの独自技術と展開戦略

CoreWeaveは単にNVIDIA Rubinを採用するだけでなく、自社開発の技術でその運用基盤を強化している。同社が構築した**Rack Lifecycle Controller**は、NVIDIA Vera Rubin NVL72ラック全体を単一のプログラマブルエンティティとして扱うKubernetesネイティブのオーケストレーターだ。電力供給、液体冷却、ネットワーク統合の緊密な要件を調整し、顧客のワークロードを投入する前にハードウェアの本番稼働準備を確実にする。

また、Rubinベースのシステムは業界初のAIワークロード向けオペレーティング標準である**CoreWeave Mission Control**と連携して展開される。これはトレーニング・インファレンス・エージェント型AIワークロードをセキュリティ、オペレーション、可観測性を統合して管理するものだ。CoreWeaveは既にGB200 NVL72やGrace Blackwell Ultra NVL72の一般提供を最初に実現した実績を持ち、SemiAnalysisのClusterMAX™ プラチナ評価を2度獲得している。

## 業界全体での展開動向と今後の展望

NVIDIA Rubinプラットフォームへの対応は、CoreWeaveだけにとどまらない。AWS、Google Cloud、Microsoft、OCIといった主要クラウドプロバイダーに加え、NVIDIA Cloud Partnersであるλambda、Nebius、Nscaleも2026年下半期にVera Rubinベースのインスタンスをいつしかのパートナーとともに提供予定だ。AI研究機関側でも、Anthropic、Meta、OpenAI、Mistral AI、xAIなど多数の企業がRubinプラットフォームへの期待を表明している。

CoreWeaveはNasdaq上場（2025年3月）後も、NVIDIAの最新プラットフォームへの早期アクセスを競争上の差別化要因として活用し続けている。薬物探索・ゲノム研究・気候シミュレーション・核融合エネルギーモデリングといった高負荷科学計算からエンタープライズAIまで幅広いユースケースをカバーするNVIDIA Rubinの採用を通じて、同社は専業AIクラウドとしての地位をさらに強固にしようとしている。
