---
date: "2026-09-29T18:15:32+09:00"
title: "Anthropic「Claude Sonnet 5.5」発表、同一価格でTerminal-Bench 70.6%とOpus級サイバー対策を実現"
description: "AnthropicがClaude Sonnet 5.5を発表し、価格据え置きのまま出力速度30%以上向上とタスク単価最大30%削減を達成、Sonnetとして初めてOpus級のサイバーセキュリティ対策も搭載した。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/09/28/anthropic-releases-sonnet-5-5-which-it-calls-a-significantly-cheaper-faster-work-partner/"
  - "https://www.anthropic.com/claude-sonnet-5-5"
  - "https://venturebeat.com/technology/anthropic-launches-claude-sonnet-5-5-with-30-cost-reduction-per-task-due-to-faster-speeds-and-fewer-tool-calls"
---

## 概要

Anthropicは9月28日、Claude 5.5ファミリー第2弾となる「Claude Sonnet 5.5」を発表した。API価格は入力100万トークンあたり2ドル、出力100万トークンあたり10ドルとSonnet 5から据え置きつつ、出力速度を30%以上高速化し、ツール呼び出し回数や使用トークン数の削減によって実タスクあたりのコストを最大30%圧縮した。Claude Platform、AWS、Google Cloud、Microsoft Azure、Claudeアプリで提供が始まっており、モデルIDは`claude-sonnet-5-5`。ゼロデータ保持オプションにも対応する。

## ベンチマークと性能

エージェント型コーディングを測るTerminal-Bench 4.0では70.6%を記録し、前モデルのSonnet 5(10.3%)を大幅に上回るだけでなく、上位モデルのOpus 5.5(66.4%)も超えた。CursorBench 4.0でも55.5%(Sonnet 5は34.1%、Opus 5.5は57.8%)、知識労働系のGDPval-AAでは1,844(Opus 5.5は1,846)とOpusにほぼ匹敵するスコアを示している。VentureBeatによれば、Low/Medium effort設定時にはSonnet 5.5がSonnet 5の最高スコアをタスク単価の約10分の1で上回るケースもあるという。ツール呼び出しをまとめて実行する挙動が強化されており、実行ステップ数と失敗率の低下につながっているとAnthropicは説明する。

## 企業導入事例とツール呼び出し効率化

Box、Zendesk、Slack、Epic Games、Atlassian、Balyasny Asset Managementなど複数の企業が導入結果を公表した。Boxは処理速度2.4倍・総トークン数12%減、Zendeskはチケット処理が20%高速化、Slackはオフライン評価で出力トークンが約14%減少したと報告している。金融のBalyasny Asset Managementは2,441件の業務タスクで使用トークン数がSonnet 5の497,000から121,000へ大幅に減少しつつ精度も向上したという。Atlassianは自社のRovoエージェントがSonnet 5.5により「最大30%高速化した」としている。こうした結果は、単純な出力速度の向上だけでなく、少ないツール呼び出しとステップ数で同等以上の成果を出す設計がタスク単価削減に直結していることを裏付けている。

## サイバーセキュリティ対策とセーフガード

Sonnet 5.5はSonnetモデルとして初めてOpus 5.5と同等のサイバーセキュリティ対策を搭載した。高リスクと判断されたタスクは自動的にSonnet 5にフォールバックする一方、通常のソフトウェア開発作業には影響しない設計となっている。承認を受けたサイバー防御担当者向けにはCyber Verification Programを通じた段階的アクセスも用意される。加えて、推論プロセスの抽出を防ぐ新しい分類器がSonnetとして初めて搭載されたほか、既存の「preserved thinking」の仕組みも拡張され、思考過程の情報が元のアカウントから切り離されて悪用されることを防ぐ。生物分野のセーフガードはSonnet 5と同水準で、有害な依頼を防ぎつつ大半の研究・臨床用途は妨げない設計を維持している。

## 市場での位置づけと今後

VentureBeatは、Sonnet 5.5の価格がOpenAIのGPT-6 Sol(入力2ドル/出力10ドル)と同水準である一方、GoogleのGemini 3.8 Flash(導入価格で入力0.75ドル/出力3.75ドル)よりは高いと指摘しつつ、Anthropicがトークン単価よりもタスク全体のコストを重視する姿勢を強調していると伝えている。TechCrunchによれば、OpenAIが前週にSolとLunaの改良版を、Metaがスマートグラス向け新モデルをそれぞれ発表するなど、モデル競争が激化する中での投入となった。Anthropicは数週間以内に「Claude Haiku 5.5」も投入する計画を明らかにしており、Sonnet 5.5は日常的なコーディングやドキュメント作成、長時間にわたる知識労働タスクにおいて、Opus 5.5を補完する低コストな主力モデルと位置付けられている。
