---
date: "2026-08-08T02:15:16+09:00"
title: "Anthropic、独自AIチップ開発チームを正式始動 元OpenAIエンジニアが技術リード"
description: "Anthropicがハードウェアとモデルの共同設計により推論コストを半減させることを目指す社内チップ設計チームの発足を確認し、元OpenAI・Tesla出身のエンジニアを迎えて採用を本格化させている。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/08/05/anthropic-is-hiring-an-ai-chip-design-team/"
  - "https://www.techtimes.com/articles/323238/20260805/anthropic-confirms-house-chip-team-co-design-bet-could-cut-claude-inference-costs-half.htm"
  - "https://www.forbes.com/sites/jonmarkman/2026/08/06/anthropic-enters-the-ai-chip-race-with-in-house-chip-team/"
---

## 概要

Anthropicは、Claudeモデル向けの独自AIチップを設計する社内チームの立ち上げを正式に確認した。狙いはハードウェアとモデルの「共同設計(co-design)」によって、トークンあたりの推論コストを約半分に削減することだ。Anthropicはこれを単なる研究プロジェクトではなく、事業戦略の中核に位置づけている。技術リーダーには、OpenAIの独自チップチームで2番目のハードウェアエンジニアとして採用され、同社のBroadcom設計推論アクセラレータ「Jalapeño」の開発に約2年半携わったClive Chan氏を迎えた。同氏はTeslaのAutopilot向けディープラーニング基盤やML学習用ASIC開発にも従事した経験を持つ。

## 採用と技術的アプローチ

Anthropicは半導体エンジニアの採用を本格化しており、求人では「完成したチップ設計を出荷した経験」を持つ人材に対し年俸32万〜48.5万ドルを提示、「大きな組織の後ろ盾なしに重要な意思決定を下せる」人物を求めている。同社の方針はNvidiaやGoogleのTPUといった既存の外部サプライヤーを置き換えるのではなく、AWS・Google・Nvidia・AMDとのパートナーシップを維持しつつ、チップとAIモデルを一体で最適化する「共同設計」によって効率を引き上げるというものだ。実際、4月にはGoogle・Broadcomとのパートナーシップを拡大し、2027年稼働予定のTPU容量3.5ギガワットに加え、2026年内にも追加で1ギガワット分の確保を発表している。7月には製造委託先としてSamsungとの協議も報じられた。

## 背景

この動きの背景には、Anthropicの急成長がある。年間経常収益(ARR)は2025年末時点の約90億ドルから、現在は300億ドルの水準まで3倍に伸びており、年間100万ドル以上を支出する法人顧客も1,000社を超える。急拡大する需要をまかなうコンピュート基盤の確保が経営上の最優先課題となっている。また、同業他社との競争も要因の一つだ。OpenAIは2026年6月にBroadcomと共同開発した推論向けチップ「Jalapeño」を発表済みで、Google DeepMindは自社のTPUを、MetaもMTIAアクセラレータをそれぞれ活用しており、大手AI企業の間で外部ベンダー依存から脱却する動きが広がっている。

## 今後の展望

現時点でAnthropicは完成したシリコンの投入時期や具体的な製造契約について明らかにしておらず、発表は主に採用活動を軸としたものにとどまる。ただし、同社はChan氏を中心にハードウェア人材の採用を積極化させている様子がうかがえる。これは、単なるAIモデル開発企業から、自社シリコンを持つ企業へと軸足を広げつつある兆候とも受け取れる。
