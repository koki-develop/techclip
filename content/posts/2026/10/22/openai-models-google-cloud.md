---
date: "2026-10-22T18:14:12+09:00"
title: "OpenAIの最新モデル群がGoogle Cloudに登場、Googleが三大クローズドLLM全てに対応する唯一のクラウドに"
description: "OpenAIがGPT-6 Astraなど最新モデル群をGoogle CloudのModel Garden経由で提供開始し、GoogleはGPT-6 Astra、Claude Fable 5.1、Gemini 4 Argonの三大クローズドソースLLM全てにアクセス可能な唯一のハイパースケーラーとなった。"
tags:
  - AI
  - Cloud
references:
  - "https://openai.com/index/openai-models-google-cloud/"
  - "https://siliconangle.com/2026/10/21/openai-to-make-its-most-advanced-ai-models-available-in-google-cloud/"
  - "https://www.techzine.eu/news/applications/145174/openais-models-are-finally-fully-supported-on-google-cloud/"
---

## 概要

OpenAIは10月21日、GPT-6 Astra、GPT-6.1 Sol、GPT-6 Lunaの各モデルをGoogle CloudのModel Gardenを通じて企業向けに提供開始すると発表した。マイクロソフトに続く主要クラウドパートナーとしてGoogleとの提携関係を一段深めるもので、これによりGoogleはGPT-6 Astra、Claude Fable 5.1、Gemini 4 Argonという三大クローズドソースLLM全てにアクセス可能な、唯一のハイパースケーラーとなった。現代のエンタープライズAI活用では用途ごとに最適なモデルを選びたいというニーズが強まっており、今回の提携はその選択の幅をGoogle Cloud上でそのまま確保する動きと言える。

## 提供されるモデルと価格

提供される3モデルはいずれも用途に応じた性能・価格のバランスで差別化されている。フラッグシップのGPT-6 Astraはコーディングやコンピュータ操作、科学研究といった高度なタスク向けで、サイバーセキュリティの脆弱性検出ベンチマークであるExploitBenchで満点を記録し、OpenAIが公表した最近のAI主導の数学的発見にも使われたモデルだという。安全性の観点でも「競合のフロンティアモデルより不整合な出力が少ない」とされ、ユーザーが定めたタスク制限を尊重するよう設計されている。GPT-6.1 SolはAstraに近い性能をより低コストで実現するモデルで価格はAstraの5分の1、GPT-6 Lunaは日常的な大規模業務向けの高速・低コスト型でAstraの100分の1という価格設定になっている。各モデルはGoogle Cloud Marketplaceを通じて販売され、利用料は単一の請求書に統合されるほか、既存のクラウド利用コミットメントや柔軟節約プランの対象にもなるため、企業は新たにAI専用の予算を確保する必要がない。

## データ管理と提供形態

データガバナンスについてもGoogle Cloudは明確な保証を示している。プロンプトやコンテキスト、出力は顧客のデータ境界内に留まり、モデルの学習には使用されないとしており、クエリは隔離されたゲートウェイを経由する。Zero Data RetentionとConfidential Compute(信頼実行環境技術でワークロード固有のメモリを暗号化する仕組み)は今後追加される予定だ。提供経路はModel Gardenに加え、AIコーディングツールのAntigravityや、クラウドアプリケーション間の業務を自動化するGemini Agentも含まれる。現時点ではプライベートプレビューの段階にあり、まずは開発者向けのCodex CLI統合から始まり、Model GardenでのAstra/Sol/Lunaの提供は数週間以内に、Google Antigravityへの対応はその後に続く計画だ。

## 背景と今後の見通し

今回の提携は、2025年夏にOpenAIとGoogleの間で締結されたクラウド容量契約の延長線上にある動きだ。OpenAIはこれまでマイクロソフトのAzureを独占的な提供基盤としてきたが、その後AWS、そして今回のGoogle Cloudへと提供範囲を広げてきた。Google Cloud CEOのThomas Kurianは、この提携が「顧客に幅広いモデルの選択肢」を与え、品質とコストの両面で最適な組み合わせを可能にすると述べている。また、Google Cloud製品管理部門の副社長Michael Gerstenhaberも、現代的なエンタープライズAIでは各ワークロードを適切なモデルに合わせる必要があると指摘しており、今回の提携はGoogleのAI基盤を競合クラウドベンダーに対して強化する一手となりそうだ。
