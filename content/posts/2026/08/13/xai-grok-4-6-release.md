---
date: "2026-08-13T08:12:37+09:00"
title: "SpaceXAIが「Grok 4.6」を発表、長時間エージェントタスクと視覚処理を強化しGPT-5.6 Sol水準へ"
description: "SpaceXAIが新フラッグシップモデルGrok 4.6を発表し、GPT-5.6 SolやClaude Fable 5に匹敵する性能をベンチマークで示しつつ、価格は前モデルから据え置いた。"
tags:
  - AI
references:
  - "https://x.ai/news/grok-4-6"
  - "https://venturebeat.com/technology/spacexai-debuts-grok-4-6-overtaking-kimi-k3s-performance-and-matching-gpt-5-6-sol-for-worlds-third-best-on-artificial-analysis"
  - "https://9to5mac.com/2026/08/12/spacexai-releases-grok-4-6/"
---

## 概要

SpaceXAIは8月12日、新しいフラッグシップモデル「Grok 4.6」を発表した。長時間稼働するエージェントタスクや、より野心的な対話・視覚処理向けに設計されており、複数ステップにわたる研究、コード分析、アプリケーション開発といった用途に対応する。Artificial Analysis Intelligence Indexでは61ポイントを記録し、Kimi K3を上回るとともに、OpenAIのGPT-5.6 Sol(最大推論レベル)とほぼ並ぶ、世界3位相当の性能を主張している。同スコアはAnthropicのClaude Fable 5 Maxよりわずか1ポイント低い水準にとどまっており、トップ集団に肉薄する結果となった。

## ベンチマークと性能

SpaceXAIによると、Grok 4.6はコーディング関連のベンチマークであるDeepSWE v1.1で65.9%のスコアを獲得した。また前モデルのGrok 4.5と比較して、CursorBench、FrontierCode、APEX-Agents、Terminal-Benchのすべての評価項目でスコアが向上したという。これらのベンチマークはいずれもエージェント的なコーディングタスクや長時間の作業遂行能力を測るもので、今回のアップデートが単純な知識・対話性能だけでなく、実務的なタスク遂行能力の底上げを狙ったものであることがうかがえる。

## 技術的な改善

性能向上の要因としてSpaceXAIは、モデル生成データと高品質なエンジニアリングデータを用いた補強訓練、改善されたオプティマイザーの採用、そして「自己テストと検証」機能の強化を挙げている。9to5macの報道でも、より長い補強学習の実行、強化されたエンジニアリングデータ、コーディングおよび知識作業向けに拡張された強化学習が改善のポイントとして紹介されており、両者の説明は一致している。

## 価格と提供方法

Grok 4.6の価格は前モデルのGrok 4.5と同水準に据え置かれ、入力トークンは100万トークンあたり2ドル、出力トークンは100万トークンあたり6ドルから利用できる。高速(fast)バージョンはこの2倍の価格設定となる。提供チャネルはCursor、Grok Build、SpaceXAIのAPIに加え、OpenRouter、Vercel、Cloudflareなど複数のプラットフォームに広がっており、発表から最初の1週間は2倍のトークン使用量が無料で含まれるキャンペーンも実施される。性能を据え置き価格で引き上げたことで、GPT-5.6 SolやClaude Fable 5と競合するハイエンド市場での価格競争力をさらに強めた形だ。
