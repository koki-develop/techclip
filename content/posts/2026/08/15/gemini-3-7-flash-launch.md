---
date: "2026-08-15T02:16:49+09:00"
title: "Google、Gemini 3.7 Flashを電撃発表 コーディング性能が大幅向上、価格は半額に"
description: "GoogleがGemini 3.6 Flashからわずか3週間でGemini 3.7 Flashを発表し、コーディングやドキュメント処理のベンチマークスコアを大幅に改善する一方、上位モデルGemini 3.5 Proの提供遅延は続いている。"
tags:
  - AI
references:
  - "https://9to5google.com/2026/08/13/gemini-3-7-flash-launch/"
  - "https://www.bloomberg.com/news/articles/2026-08-13/google-debuts-new-gemini-flash-while-top-ai-model-still-delayed"
  - "https://siliconangle.com/2026/08/13/google-launches-gemini-3-7-flash-coding-ai-agent-projects/"
---

## 概要

Googleは8月13日、新モデル「Gemini 3.7 Flash」を発表し、Gemini Sparkを通じて160カ国以上で即時展開を開始した。前モデルのGemini 3.6 Flashからわずか3週間というハイペースでの投入となり、開発者からのフィードバックとアルゴリズム面の革新を反映した「実質的な改善」がもたらされているという。Googleはコーディングと自律型ビジネスワークフロー向けのモデルと位置付けており、ソフトウェア開発やデバッグ性能の向上を強調している。一方で、上位モデルとなるGemini 3.5 Proの提供は依然として遅延が続いている。

## 性能とベンチマーク

Gemini 3.7 Flashはソフトウェアエンジニアリング関連のベンチマークで顕著な向上を見せた。DeepSWE v1.1では49.0%から65.3%へ、FrontierCode 1.1では34.4%から43.6%へとスコアが上昇している。とりわけFrontierCode 1.1 Mainのテストでは、単なるコード生成だけでなくバグ修正への対応やプロジェクト固有のスタイルガイド遵守も評価対象となる100件のプログラミングタスクにおいて、AnthropicやOpenAIの競合モデルを上回る結果を示したという。

ウェブ開発の分野では、より少ないプロンプトで機能的かつ完成度の高いアプリケーションを生成できるようになり、Arena.aiのWebDev ArenaにおけるEloスコアは1538から1588へと向上した。ユーザーインターフェース生成能力も強化されており、アップロード済みの参考画像に基づいて適切なレイアウトを設計できる。処理能力の面では、最大100万トークン分の画像・動画・テキストをプロンプトとして扱い、最大64,000トークンのテキスト応答を生成できるとしている。

知識集約型のタスクでも改善が見られ、ドキュメント理解を測るGDP.pdfベンチマークでは22.0%から34.0%へ、AutomationBenchでは17.0%から30.4%へとそれぞれ上昇した。GDP.pdfのテストではClaude Sonnet 5やGPT-5.6 Terraを上回る性能を記録したとされ、Googleは同モデルが複数のAIエージェントからなる「エージェント群」を動かすことも可能だとしている。

## 価格体系と提供範囲

Googleは2026年末まで導入価格を適用し、入力トークンが100万あたり0.75ドル、出力トークンが100万あたり3.75ドルと、前モデル比で50%引きの水準に設定した。提供先はGemini Spark（AI Pro/Ultraサブスクリプションが必要）のほか、Google Antigravity、AI Studio、Android Studio、Enterprise Agent Platformと幅広い。またCBRN(化学・生物・放射線・核)関連やサイバー脅威への対策として、セーフガードも更新されたという。

## 上位モデルの遅延という背景

今回のGemini 3.7 Flashの投入は、上位モデルであるGemini 3.5 Proの提供遅延が続くさなかに行われた点が注目される。エントリーレベルモデルの高速なアップデートサイクルによって競合他社に対する優位性を維持しつつ、フラッグシップモデルの遅れを補う狙いがあるとみられる。
