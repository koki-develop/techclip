---
date: "2026-10-28T08:08:08+09:00"
title: "OpenAIの新モデル「GPT-6.1 Terra」、画面操作エージェントを3倍高速化しAPI価格は半額に"
description: "OpenAIが業務自動化向けモデル「GPT-6.1 Terra」を発表し、エージェント処理速度3倍・API価格50%引き下げとエラー率の大幅改善を実現した。"
tags:
  - AI
references:
  - "https://9to5mac.com/2026/10/26/openai-upgrades-chatgpt-and-codex-with-new-gpt-6-1-terra-model/"
  - "https://www.bleepingcomputer.com/news/artificial-intelligence/openai-launches-gpt-61-terra-with-3x-faster-ai-agents-50-percent-lower-pricing/"
  - "https://decrypt.co/381883/openai-launches-gpt-6-1-terra-half-good-half-price"
---

## 概要

OpenAIは10月26日、画面を認識して複数のアプリケーションを横断操作できる新モデル「GPT-6.1 Terra」を発表した。前モデルのGPT-5.6 Terraからのアップグレードにあたり、ChatGPT Work・Codex・APIを通じて提供が始まっている。Terraは「コンピュータ使用（computer use）」に特化したモデルで、画面を見ながらクリックやキー入力で人間のようにアプリを操作し、提案書作成、技術図面の読み取り、フォーム入力、データ入力、動画編集といった業務タスクをこなす。研究寄りの用途を担うGPT-6 AstraやGPT-6.1 Solとは役割が異なり、Terraはオフィスワークの自動化という実務領域に軸を置いている。

## 性能とベンチマークの改善

OpenAIの内部ベンチマークによれば、エラー率は低推論努力時で53.6%から16.7%へと37ポイント改善し、最大努力時でも18ポイント低下して4.3%まで下がった。これはハイエンドモデルに迫る精度だという。エージェントのタスク遂行能力を測る「Agents' Last Exam」では、中程度の推論設定でGPT-5.6 Terraを15ポイント上回った。コーディング関連のベンチマークであるTerminal-Bench 4.0でも、コマンドライン操作タスクの解決率が50.3%となり、前モデルの21.5%から倍以上に向上している。処理速度の面では、通常タスクの実行速度がGPT-6 AstraおよびGPT-6.1 Solの3倍以上に達するとされ、エージェントによる自動化のレスポンスを大きく高速化した。

## 価格設定と提供範囲

API価格は入力100万トークンあたり1ドル、出力100万トークンあたり5ドルで、前モデルGPT-5.6 Terraから50%引き下げられた。GPT-6 Astraと比較すると同等の性能を保ちながらトークン単価は10分の1に抑えられており、コスト効率を重視する企業にとって実用的な選択肢となる。ChatGPT Work・Codex・APIでは、Plus、Pro、Enterprise、Eduの各プランユーザーが`gpt-6.1-terra`としてモデルを利用できる。

## 背景と今後の展望

Terra系列は2026年6月に限定プレビューとして導入され、7月に一般公開された経緯を持つ。OpenAIは先月（9月）、下位モデルのGPT-6 Lunaと上位モデルのGPT-6 Solを公開しており、Terraはこの更新には含まれていなかった。複雑なコーディングや高度な調査用途では、現在もGPT-6.1 SolやGPT-6 Astraが案内されている。いずれにせよ、エラー率の大幅な改善と価格の引き下げが同時に実現したことで、企業が画面操作エージェントを本格導入する際の障壁は一段と下がったと言える。今後はTerraのような実務特化モデルと、AstraやSolのような研究特化モデルの役割分担がOpenAIのプロダクト戦略の軸になっていきそうだ。
