---
date: "2026-06-25T02:42:08+09:00"
title: "OpenAI、Broadcomと共同開発した初のカスタムAI推論チップ「Jalapeño」を発表——NVIDIA依存脱却へ本格始動"
description: "OpenAIがBroadcomと共同設計した初の推論専用カスタムチップ「Jalapeño」を公開し、現行最先端チップを上回る電力効率を謳うとともに、自社AIモデルを活用してチップ開発を加速したことを明らかにした。"
tags:
  - AI
  - Other
references:
  - "https://techcrunch.com/2026/06/24/openai-unveils-its-first-custom-chip-built-by-broadcom/"
  - "https://www.cnbc.com/2026/06/24/openai-and-broadcom-reveal-jalapeno-first-ai-chip-in-partnership.html"
  - "https://venturebeat.com/infrastructure/openai-unveils-first-custom-ai-inference-chip-jalapeno-with-broadcom-and-its-development-was-sped-up-with-openais-own-models"
---

## 概要

OpenAIは2026年6月24日、半導体大手Broadcomと共同設計した初のカスタムAI推論チップ「Jalapeño」を正式に発表した。同チップはユーザーリクエストへの応答として学習済みモデルを動作させる「推論（インファレンス）」に特化した設計で、早期テストにおいて「現行の最先端チップを大幅に上回る性能対消費電力比（Performance-per-Watt）」を示しているという。OpenAIとBroadcomのパートナーシップは2025年10月に正式発表されており、今回の公開はその具体的な成果となる。

## 開発プロセスとAI活用

注目すべきは、Jalapeñoの設計・開発プロセス自体にOpenAI自身のAIモデルが活用されている点だ。チップのアーキテクチャ検討やシミュレーションにAIを組み込むことで開発サイクルを短縮したとされ、「AIでAIを作る」という象徴的な事例となっている。OpenAI社長のGreg Brockmanは「自社のワークロードを深く理解しているからこそ、可能性の限界を押し広げられる」と述べており、ソフトウェアとハードウェアを一体として最適化できる強みを強調した。

## 戦略的意義——NVIDIA依存の低減

Jalapeñoの開発背景には、NVIDIAのGPUへの依存を減らしインフラコストを抑制するという明確な戦略がある。OpenAIはモデル、製品、インフラ、チップアーキテクチャ、データセンター、デプロイシステムを「スタック全体」として一貫して最適化できる体制を目指しており、同チップはその重要なマイルストーンだ。同様のアプローチはGoogleのTPUやAmazonのTrainiumでも見られ、クラウド・AI企業による独自シリコン開発の潮流がOpenAIにも波及した形となる。

## 今後の展望と課題

現時点でJalapeñoはテスト段階にあり、量産・実運用に向けたタイムラインは明らかにされていない。また同チップが対象とするのはあくまでも推論であり、計算負荷の高い事前学習（プレトレーニング）については引き続きNVIDIAのGPUに依存する見込みだ。それでも推論コストの効率化はOpenAIのビジネス経済性を大きく改善する可能性があり、将来的なGPUからカスタムシリコンへの移行を加速させる試金石として業界から注目を集めている。
