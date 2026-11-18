---
date: "2026-11-18T18:09:22+09:00"
title: "OpenAI、専門業務向け「GPT-6.2 Astra」と日常業務向け「GPT-6.2 Sol」を投入、API価格引き下げとベンチマーク向上を両立"
description: "OpenAIが新モデルGPT-6.2 AstraとSolを発表し、API価格の引き下げとベンチマーク性能の向上を同時に実現した。"
tags:
  - AI
references:
  - "https://openai.com/index/introducing-gpt-6-2-astra-sol/"
  - "https://the-decoder.com/openai-launches-gpt-6-2-astra-and-sol-with-lower-api-prices-and-some-benchmark-gains/"
  - "https://9to5mac.com/2026/11/17/openai-upgrades-chatgpt-and-codex-with-new-gpt-6-2-astra-and-sol-models/"
---

## 概要

OpenAIは11月17日、新モデル「GPT-6.2 Astra」と「GPT-6.2 Sol」を発表した。Astraは科学・法務・金融といった専門業務向けの高性能モデル、Solは日常的なコーディングや執筆向けのコスト効率型モデルという位置付けで、両モデルともChatGPT Work、Codex、APIを通じて即日利用可能になった。ChatGPT側はPlus、Pro、Enterprise、Eduの各プランが対象となる。注目すべきは、性能向上とAPI価格引き下げを同時に実現した点で、Astraの入出力トークン価格は前世代より最大20%引き下げられた一方、Solの価格帯は従来のまま据え置かれている。

## ベンチマークと実務性能

Artificial Analysis Intelligence Indexの評価では、Astraは62点を獲得し、Claude Fable 5.2(65点)に次ぐ2位につけた。Solは57点で前世代(55点)から2ポイント向上したが、コストパフォーマンスの面で「最高の価値を提供する」モデルと評価されている。分野別では、Astraは科学関連タスクで優位性を示す一方、法務分野では改善の余地が残るとの指摘もある。Cognitionが提供するコーディング特化ベンチマーク「FrontierCode 2.0」では、Solが最大推論努力の設定でAstraとわずか0.5ポイント差まで迫る結果を出し、その際のコストはAstraの約5分の1に抑えられたという。Astraについては、画面のスクリーンショットをテンプレートとして読み込み、レイアウトや配色、フォントサイズを再現できる機能も強化され、より整理されたコード生成と的を絞ったテスト作成が可能になったと紹介されている。

## 価格体系とUltrafastモード

Pro プラン(月額200ドル)ではSol向けに生成速度を標準比で最大4.5倍に高速化する「Ultrafast」モードが新たに導入された。さらに月額500ドルのプランでは、AstraとSolの両モデルでUltrafastモードを利用できる。速度向上と引き換えに利用量の消費ペースは速くなるため、用途に応じた選択が求められる。API側では、Astraの標準入出力価格が20%引き下げられたことで、高性能モデルをより低コストで組み込める環境が整った。

## AI自己改善能力と安全性への論点

OpenAIは、Astraが外部公開モデルとして初めてAI自己改善能力の「High」閾値に達したと説明しており、AI研究そのものを加速させうる能力を持つとしている。これに対し同社は、内部の監視体制「Control Room」を通じて対応する方針を示した。一方でEpoch AIの分析によると、Astraは可視的な思考過程(チェーン・オブ・ソート)を示さずに複雑な推論を実行できるとされ、外部から安全性を監視することがこれまでより難しくなる可能性が指摘されている。性能向上と価格引き下げという利用者にとって歓迎すべき進化の裏側で、モデルの能力拡大に監視体制がどこまで追随できるかが、今後の課題として注目される。
