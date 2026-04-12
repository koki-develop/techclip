---
date: "2026-04-12T18:14:57+09:00"
title: "CoreWeave、NVIDIA Rubin統合を発表——専用オーケストレータでラック丸ごとを単一ユニットとして管理"
description: "CoreWeaveがNVIDIA Vera Rubin NVL72ラックをクラウド基盤に統合する計画を発表し、独自開発の「Rack Lifecycle Controller」でエージェンティックAIや大規模推論ワークロードに対応する。"
tags:
  - Cloud
  - AI
references:
  - "https://www.coreweave.com/news/coreweave-extends-its-cloud-platform-with-nvidia-rubin-platform"
---

## 概要

CoreWeaveは2026年1月、NVIDIA Rubinプラットフォームをクラウド基盤に統合する計画を発表した。同社は最初期にNVIDIA Rubinを展開するクラウドプロバイダーの一つとなる見込みで、2026年後半に初期デプロイを開始する予定だ。今回の統合により、大規模な推論処理、エージェンティックAI、そして薬物発見・気候シミュレーション・融合エネルギーモデリングといった複雑な科学技術ワークロードへの対応能力が大幅に強化される。

## 独自開発のRack Lifecycle Controller

今回の発表における中心的な技術要素が、CoreWeaveが独自に開発したKubernetesネイティブのオーケストレータ「Rack Lifecycle Controller」だ。このシステムはNVIDIA Vera Rubin NVL72ラック全体を単一のプログラマブルユニットとして扱い、電力供給・液体冷却・ネットワーク統合を統合的に管理することで本番環境への確実な準備を実現する。

さらに、NVIDIAの信頼性エンジン（RAS Engine）と統合された「Mission Control」により、リアルタイム診断と可視性の提供が可能になる。フリート全体・ラック・キャビネットという複数の粒度でシステムのヘルス状態を監視できる点は、大規模クラウドオペレーションにおいて重要な意味を持つ。

## 戦略的位置付けと将来展望

CoreWeaveのCEO、Michael Intrator氏は「エンタープライズ顧客がCoreWeaveを選ぶのは、真の選択肢と、複雑なワークロードを本番規模で確実に動かす能力があるからだ」と述べており、信頼性と柔軟性を競合との差別化軸に据えている。同社のプラットフォームは複数世代のテクノロジーを並行して運用できる設計となっており、顧客が進化する要件に対して迅速に適応できる環境を提供する。

NVIDIA Vera Rubin NVL72は大規模Mixture-of-Expertsモデルのサポートにも対応しており、生成AIの推論インフラとしても期待されている。AIワークロードの高度化・大規模化が続く中で、ラック単位での統合管理という CoreWeaveのアプローチは、次世代クラウドインフラの一つのモデルケースとなりうる。
