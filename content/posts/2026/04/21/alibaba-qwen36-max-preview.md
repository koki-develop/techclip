---
date: "2026-04-21T18:30:42+09:00"
title: "AlibabaのQwen3.6-Max-Preview、プログラミングベンチマーク6冠達成—クローズドモデルへ方針転換"
description: "Alibabaが新フラッグシップAIモデル「Qwen3.6-Max-Preview」を公開し、SWE-benchProなど6つのプログラミングベンチマークでトップスコアを獲得した。"
tags:
  - AI
references:
  - "https://cntechpost.com/2026/04/20/alibaba-releases-qwen3-6-max-preview-stronger-instruction-following-capabilities/"
  - "https://decrypt.co/364948/alibaba-qwen-3-6-max-preview-most-powerful-model"
  - "https://www.aibase.com/news/27277"
---

## 概要

Alibabaは2026年4月20日、フラッグシップAIモデルシリーズの最新版「Qwen3.6-Max-Preview」を早期アクセス版として公開した。同モデルはQwenStudioおよびAlibaba Cloud BaiLian APIを通じて利用可能で、現在も活発に開発中のワークインプログレス版として位置づけられている。Qwen3.6-Plus比でプログラミング能力・知識・指示追従の3つの主要領域で大幅な改善を達成したとされ、Alibabaのフラッグシップモデルとして現時点で最も高性能な水準に達していると発表された。

## プログラミングベンチマークでの最高性能

プログラミング能力においては、SWE-benchPro、Terminal-Bench2.0、SkillsBenchを含む6つの主要ベンチマークで首位スコアを獲得した。前世代のQwen3.6-Plusとの比較では、SkillsBenchで9.9ポイント、SciCodeで10.8ポイントの向上を達成しており、エージェント型コーディングへの対応能力が特に強化されている。指示追従能力においてはClaudeなどの競合モデルを上回ると報告されており、ToolcallFormatIFBenchでは2.8ポイントの改善を記録した。

## 技術仕様と知識向上

技術仕様面では、256,000トークンのコンテキストウィンドウをサポートし、OpenAIおよびAnthropicのAPI仕様と互換性を持つ。マルチターン会話での推論過程を保持するpreserve_thinking機能も備えており、複雑なエージェント型タスクへの対応を強化している。ただし、現時点ではテキスト入力のみに対応しており、マルチモーダル機能は含まれていない。知識面では世界知識の理解において顕著な改善が見られ、SuperGPQAで2.3ポイント、中国語性能を測るQwenChineseBenchで5.3ポイントの向上を達成した。

## 戦略的転換：オープンソースからクローズドモデルへ

今回のリリースで注目されるのは、Alibabaの配布戦略の大きな転換だ。同社はこれまで強力なモデルを無料のオープンソースとして公開してきたが、Qwen3.6-Max-Previewは重みを公開しない独自のホスト型モデルとして提供される。これはオープンな配布から商業的なマネタイズサービスへの方針転換を意味する。市場環境を見ると、中国発オープンモデルのグローバルオープンモデル利用シェアは2024年末の約1.2%から2025年末には約30%にまで急拡大しており、その成長をQwenシリーズが牽引してきた背景がある。現在もアクティブな開発が続いており、今後のイテレーションでさらなる改善が予定されている。
