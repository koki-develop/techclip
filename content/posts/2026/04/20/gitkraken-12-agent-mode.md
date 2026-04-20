---
date: "2026-04-20T18:33:14+09:00"
title: "GitKraken Desktop 12.0、AIエージェントの並列管理を一元化する「Agent Mode」を搭載"
description: "GitKraken Desktop 12.0がリリースされ、Claude CodeやCopilotなど複数のAIコーディングエージェントをワークツリー単位で一元管理できる「Agent Mode」が搭載された。"
tags:
  - OSS
references:
  - "https://www.prnewswire.com/news-releases/gitkraken-desktop-12-0-introduces-agent-mode-gives-developers-ultimate-control--visualization-while-scaling-parallel-agent-workflows-302745055.html"
---

## 概要

GitKrakenは2026年4月16日、Git管理ツールの最新版「GitKraken Desktop 12.0」を正式リリースし、複数のAIコーディングエージェントを並列で管理できる「Agent Mode」を新たに搭載した。これまで開発者がAIエージェントを並列実行する際には複数のターミナルウィンドウを開いて管理する必要があったが、Agent Modeによってすべてのエージェントセッションを単一のパネルから確認・操作できるようになった。Claude Code、Codex CLI、GitHub Copilot、Gemini CLI、OpenCodeといった主要なAIエージェントに対応している。

## 主な機能と技術的な詳細

Agent Modeの中核となるのは、アクティブなすべてのエージェントとそれに関連するワークツリーを一覧表示する「Agent Panel」だ。各セッションが「実行中」「入力待ち」「完了」のいずれの状態にあるかをリアルタイムに示すステータスインジケーターが表示され、コンテキストの切り替えなしに全体の進捗を把握できる。また、拡張されたコミットグラフにより、すべてのアクティブなワークツリーが可視化され、エージェントが作業中の場所・コミット・コードベース全体との関係を直感的に確認できる。

エージェントの起動フローも大幅に簡略化されており、ブランチ名を選択してエージェントを選び「Start」をクリックするだけでセッションを開始できる。ワークツリーの作成、セットアップコマンドの実行、エージェントの起動までが自動化される。作業完了後はワンクリックでワークツリーを削除できる。

## 背景と意義

GitKrakenのCEO Matt Johnstonは「新しい時代に勝利する開発者は、最高のコードを書く者でも最高のプロンプトを入力する者でもなく、マルチエージェントの出力を最大化しながら制御を維持できる者だ」とコメントしている。Agent Modeはシニアエンジニアだけでなく、コマンドラインに不慣れなジュニア開発者も並列AIワークフローに参加できるよう設計されており、チーム全体での生産性向上を狙っている。

また、GitKraken Insightsとの連携により、コミット頻度やサイクルタイム、エージェント支援による成果物などのチーム全体のメトリクスを追跡することも可能となっている。

