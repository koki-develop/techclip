---
date: "2026-08-21T08:04:53+09:00"
title: "xAI「Grok 4.6」がGitHub Copilotに統合、8つの開発環境で利用可能に"
description: "xAIの最新推論モデル「Grok 4.6」がGitHub Copilotに追加され、VS CodeやJetBrains、Xcodeなど8つの開発サーフェスでエージェント型コーディングに利用できるようになった。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-08-14-grok-4-6-is-now-available-in-github-copilot/"
  - "https://x.ai/news/grok-4-6-github-copilot"
  - "https://www.unite.ai/grok-4-6-arrives-in-github-copilot-across-eight-development-surfaces/"
---

## 概要

xAIは8月12日に発表した最新の推論モデル「Grok 4.6」を、その2日後の8月14日にGitHub Copilotへ統合したと発表した。エージェント型コーディングや複雑な多段階のワークフローに向けて設計されたモデルで、VS Code、Visual Studio、Copilot CLI、Copilot cloud agent、Copilot app、JetBrains、Xcode、Eclipseの計8つの開発サーフェス全体で利用できる。対象はCopilot Pro、Pro+、Max、Business、Enterpriseの各プランだが、Business・Enterprise管理者はデフォルトで無効になっているGrok 4.6ポリシーを設定画面で有効化する必要がある。ロールアウトは段階的に進められており、ユーザーはモデルピッカーから「Grok 4.6」を選択することで利用できる。

## 技術的な特徴とベンチマーク

xAIはGrok 4.6を「長時間動作するエージェントや、より野心的なインタラクティブ・ビジュアル作業」向けに設計したとしている。推論・エンジニアリングデータでの追加のファインチューニングと、カーネル最適化やWeb開発、CAD(コンピュータ支援設計)といったエージェント型タスクに焦点を当てた強化学習を組み合わせて訓練された。ベンチマークでは、ターミナル環境での長時間コーディングタスクに強みを見せており、Terminal-Bench v3.0で26%を記録した。これはGPT-5.6 Sol Maxの34.6%には及ばないものの、前世代のGrok 4.5の15.7%からほぼ倍増している。またエージェント型コーディングを測るDeepSWE v1.1では65.9%を記録し、Grok 4.5 Highの54%から大きく向上した。

## 料金体系

Grok 4.6はxAIのAPIを通じて、入力100万トークンあたり2ドル、出力100万トークンあたり6ドルという価格で提供される。これはGPT-5.6 Sol(入力5ドル/出力30ドル)やClaude Opusクラスのモデル(入力5ドル/出力25ドル)と比べて大幅に低い水準であり、性能面では最上位モデルに一歩譲るものの、コスト面での競争力が際立っている。

## 今後の展望

JetBrains、Xcode、Eclipseまで含めた幅広いIDEサポートは、新モデルのローンチとしては異例の広さであり、VS Code中心の開発者層を超えてエンタープライズ開発者への浸透を狙う姿勢がうかがえる。ロールアウトは順次拡大される見込みで、GitHubコミュニティディスカッションを通じてユーザーからのフィードバックも収集されている。
