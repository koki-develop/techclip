---
date: "2026-08-06T20:42:51+09:00"
title: "Meta、初のAIコーディングエージェント「Muse Code」をベータ公開 OpenAI・Anthropicに対抗"
description: "MetaはCEOのMark Zuckerberg氏を通じて同社初のAIコーディングエージェント「Muse Code」のベータ版を発表し、OpenAIやAnthropicが先行するAIコーディング市場での競争に本格参入した。"
tags:
  - AI
references:
  - "https://www.bloomberg.com/news/articles/2026-08-05/meta-debuts-ai-coding-agent-in-race-with-openai-and-anthropic"
  - "https://techcrunch.com/2026/08/05/meta-launches-muse-code-an-ai-agent-for-large-code-bases/"
  - "https://siliconangle.com/2026/08/05/meta-takes-anthropic-openai-first-ai-coding-agent-muse-code/"
---

## 概要

Meta CEOのMark Zuckerberg氏は8月5日、同社初のAIコーディングエージェント「Muse Code」のベータ版をリリースしたと発表した。ソフトウェア開発タスクを丸ごと担うエージェントで、OpenAIやAnthropicが先行するAIコーディング市場での競争激化を狙った動きとなる。Muse Codeはターミナル上で動作するコーディングエージェントで、大規模なリポジトリを対象に変更の計画立案、コードの記述、結果の検証までを一貫して行う。

## 技術的な詳細

Muse Codeは、Metaが開発したコーディング特化モデル「Muse Spark 1.2」を搭載する。セッション中は専用のバックグラウンドエージェントが稼働し続け、時間の経過とともにコンテキストを蓄積していく仕組みを持つ。作業規模が大きい場合は、独立した作業ツリー(worktree)上で動く複数のサブエージェントに処理を分散させ、並列で機能を構築できる。ユーザーの元の作業コピーには一切手を加えない設計となっており、あるテストではひとつのゲームに対して6つの機能を同時に構築させたところ、エージェント間の衝突は発生しなかったという。

## 価格体系と提供方法

Metaは価格面での差別化も打ち出している。開発者は通常の従量課金制APIのほか、利用データの提供と引き換えにコストを9割以上(競合比10倍以上安い水準)抑えられる「コントリビューター階層」を選択できる。データ共有を望まないプライバシー重視の利用者向けには、上位の有料プランも用意されている。Muse CodeはMeta自社のAPIに加え、DeepSeekやMoonshot AIなど中国系ラボのオープンウェイトモデルもホストするプラットフォーム「OpenRouter」経由でも提供される。

## 背景と今後の展望

Muse Codeは、Meta Superintelligence Labsを率いるAI責任者Alexandr Wang氏のもとで手掛けられた主要リリースの一つだ。同氏は2025年6月、低迷していたMetaのAI戦略を立て直す中心人物として入社した経緯がある。コーディング領域は生成AIの中でも収益性が高く企業導入を牽引する分野とされており、今回の投入はMetaが数千億ドル規模で積み増してきたAIインフラ投資の回収を図る狙いもあるとみられる。OpenAIやAnthropicが強さを見せるAIコーディング市場に、Metaがどこまで食い込めるかが今後の焦点となる。
