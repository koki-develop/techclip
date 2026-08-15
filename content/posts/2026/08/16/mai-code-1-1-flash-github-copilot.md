---
date: "2026-08-16T02:03:30+09:00"
title: "GitHub Copilot新モデル「MAI-Code-1.1-Flash」、価格73%引き下げも性能はDeepSeekに劣勢"
description: "MicrosoftがGitHub Copilot向けコーディングAIモデル「MAI-Code-1.1-Flash」を発表、旧モデルより73%安価になったが競合DeepSeekには価格・性能ともに劣るとの指摘が出ている。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-08-11-mai-code-1-1-flash-available-in-github-copilot/"
  - "https://microsoft.ai/news/mai-code-1-1-flash-br-better-faster-at-a-quarter-of-the-cost/"
  - "https://the-decoder.com/microsofts-new-mai-code-1-1-flash-gets-crushed-by-deepseek-on-both-price-and-performance/"
---

## 概要

Microsoftは2026年8月11日、GitHub Copilot向けの新しいコーディングAIモデル「MAI-Code-1.1-Flash」を発表した。前モデル「MAI-Code-1-Flash」の後継として、コーディング品質や命令理解、ツール利用能力を向上させたほか、新たにネイティブな画像理解機能を搭載した。最大の特徴は価格で、旧モデルと比較して73%安価な料金設定を実現している。年間サブスクリプション契約者には0.25倍のプレミアム乗数が適用される。

Copilot CLI、GitHub Copilotアプリ、Visual Studio Code、Visual Studio、JetBrains IDE、Eclipse、Xcodeなど幅広い開発環境で利用可能。Free・Student版では自動的に選択される一方、Pro・Business・Enterprise版ではユーザーが手動で選択することもできる。Enterprise・Business管理者は管理設定で有効化する必要がある。

## 技術的な詳細

Microsoft AIによれば、MAI-Code-1.1-Flashは「より高品質なコード出力を、25%高いトークン効率で、4分の1のコストで」実現しているという。具体的な性能指標として、GitHub Copilot CLI上でのTerminal-Bench 2.1が22%向上、.NET関連タスクで15%の性能向上が確認されたと報告されている。実運用面では、生成コードの生存率が4%上昇し、ユーザーの再訪問率も9%増加したとしている。

効率性の面では、トークン生成速度が25%高速化し、同時にタスク完了に必要なトークン数も25%削減された。Microsoftは数十万規模の強化学習環境を用いてモデルを最適化し、そのコスト削減分をユーザーに還元したと説明している。

## 競合比較と評価

一方で、The Decoderの分析では、MAI-Code-1.1-Flashは競合のDeepSeek-V4-Flashに価格・性能の両面で見劣りするとの指摘がなされている。ベンチマークでは、SWE-bench VerifiedでMAI-Code-1.1-Flashが72.6%を記録した一方、Terminal Bench 2.1ではDeepSeekが82.7%とMicrosoftの62.9%を大きく上回った。価格面でも、DeepSeek-V4-Flashは入力$0.14・出力$0.28であるのに対し、MAI-Code-1.1-Flashは入力$0.20・出力$1.20と、DeepSeekが安価であるとされている。

同記事は、Microsoftがオープンウェイトの優れた代替モデルを採用するのではなく、性能で劣る自社製の非公開モデルに投資している点を問題視している。GitHub Copilotユーザーに自社モデルをデフォルトとして提供することで、市場シェアの囲い込みと利益率の改善を狙う戦略ではないかとの見方を示しており、これは技術的優位性や顧客選択の自由よりもエコシステムの支配を優先する戦略だと分析している。
