---
date: "2026-07-03T02:36:16+09:00"
title: "AnthropicのClaude Sonnet 5が正式公開、Opus 4.8に迫る性能を低コストで提供しエージェント市場を狙う"
description: "AnthropicがエージェントワークフローにOPTIMIZEDなClaude Sonnet 5を正式リリースし、Opus 4.8に近い性能をより低価格で提供するとともにGitHub CopilotでもGA提供を開始した。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/06/30/anthropic-launches-claude-sonnet-5-as-a-cheaper-way-to-run-agents/"
  - "https://github.blog/changelog/2026-06-30-claude-sonnet-5-is-generally-available-for-github-copilot/"
---

## 概要

Anthropicは6月30日、中規模モデルの最新版である**Claude Sonnet 5**を正式リリースした。同社はこのモデルを「計画を立て、ブラウザやターミナルなどのツールを使いながら自律的に動作できる」エージェント向けモデルとして位置づけており、複雑なマルチステップのタスクを途中で停止することなくエンドツーエンドで完遂する能力が特徴だ。6月30日からAnthropicのFree・Proプランにおけるデフォルトモデルとなり、GitHub CopilotでもGA（一般利用可能）提供が開始された。

## 性能と価格

ベンチマーク結果では、エージェント的なコーディング評価で63.2%のスコアを記録した。これはOpus 4.8の69.2%には及ばないものの、前世代のSonnet 4.6（58.1%）を大幅に上回る。また、知識作業の特定ベンチマークではOpus 4.8をわずかに超える場面もある。

価格面では、8月31日までの期間限定で入力100万トークンあたり2ドル、出力100万トークンあたり10ドルと設定されており、Opus 4.8やOpenAIのGPT-5.5、Google Gemini 3.1 Proより安価である（ただしGemini 3.5 Flashよりは高め）。9月1日以降は入力3ドル・出力15ドルへ値上がりする予定だ。

## エージェント向け機能と安全性

Sonnet 5の特徴の一つは、明示的な指示なしに自身のアウトプットを検証する**自己チェック機能**だ。さらに、悪意のあるリクエストへの拒否率の向上やハルシネーションの低減など、前世代より安全性指標も改善されている。業界全体でエージェント機能が基本的な期待値となりつつある中、Anthropicは能力よりもコスト効率と信頼性を競争軸に据えたモデルで市場シェアの拡大を図っている。

## GitHub Copilotでの展開

GitHub CopilotでのClaude Sonnet 5のGA提供は、Copilot Pro・Pro+・Max・Business・Enterpriseの各プランが対象となっている。Visual Studio Code、Visual Studio、JetBrains、Xcode、EclipseなどのIDE、さらにCopilot CLI、GitHub Mobile（iOS/Android）、github.comなど幅広いプラットフォームのモデルピッカーから選択できる。他のSonnetモデルと同様にゼロデータ保持（ZDR）下で動作し、Business/Enterpriseの管理者はモデルポリシー設定で組織内での利用可否を制御できる。段階的なロールアウトが予定されているため、すぐに利用できない場合もある。
