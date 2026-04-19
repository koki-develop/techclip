---
date: "2026-04-19T18:15:11+09:00"
title: "Hermes Agent v0.10.0がTool Gatewayを導入、追加APIキー不要でWeb検索・画像生成・音声合成に対応"
description: "Nous ResearchのオープンソースAIエージェント「Hermes Agent」がv0.10.0をリリースし、Nous Portalサブスクライバー向けにWeb検索・画像生成・音声合成・ブラウザ自動操作を一括提供する「Tool Gateway」機能を搭載した。"
tags:
  - OSS
  - AI
references:
  - "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.4.16"
  - "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.4.13"
---

## Tool Gatewayで外部ツール連携を一元化

Nous Researchは2026年4月16日、オープンソース自己進化型AIエージェント「Hermes Agent」のv0.10.0をリリースした。今回のリリースの中核となるのが「Nous Tool Gateway」機能で、Nous Portalの有料サブスクライバーに対して、追加のAPIキー取得や設定不要でさまざまな外部ツールへのアクセスを自動提供する。

Tool Gatewayが提供するツールは、Firecrawlを利用したWeb検索、FAL / FLUX 2 ProによるAI画像生成、OpenAI TTSを使ったテキスト音声合成、そしてBrowser Useによるブラウザ自動操作の4種類だ。ユーザーは`hermes model`コマンドを実行してNous Portalを選択し、利用するツールを選ぶだけで、既存のサブスクリプションの範囲内でこれらの機能が即座に有効化される。また、従来の隠し環境変数`HERMES_ENABLE_NOUS_MANAGED_TOOLS`はこのサブスクリプションベースの自動検出に置き換えられ廃止となった。v0.10.0には合計180以上のコミットが含まれており、バグ修正やプラットフォームの安定性向上も併せて実施されている。

## v0.9.0でモバイル・マルチプラットフォーム対応を強化

v0.10.0の3日前にあたる4月13日にリリースされたv0.9.0も大規模なアップデートで、487件のコミット、269件のマージPR、167件のIssue解決を含む。このバージョンの最大のテーマは「いたるところで動作する」という哲学に基づいたマルチプラットフォーム対応の拡充だ。

モバイル環境ではTermux経由でのAndroidネイティブ実行に対応し、TUIモバイル画面向けの最適化も施されている。メッセージングプラットフォームの統合も大幅に拡張され、BlueBubblesを通じたiMessage連携、iLink Bot APIによるWeChat連携、WeCom Callbackモードによる企業向けアプリ連携が追加され、合計16のメッセージングプラットフォームをサポートするようになった。AIモデルの面では、OpenAIおよびAnthropicのファストティア向け優先ルーティングを行う「Fast Mode」、xAI（Grok）ネイティブプロバイダー、Xiaomi MiMoプロバイダーが追加されている。

## セキュリティ強化と開発者向けツール

v0.9.0ではセキュリティ面の改善も注目される。Twilio webhook署名検証によるSMS RCE対策、シェルインジェクション・Gitの引数インジェクション防止、SSRFリダイレクト保護、パストラバーサル防止など、エージェントが外部との通信を広範に行う性質を踏まえた多層的なセキュリティ強化が行われた。

開発者向けの機能としては、ブラウザベースのローカルWebダッシュボードが追加され、設定管理・セッション監視・スキル閲覧・ゲートウェイ管理をターミナルやコンフィグファイルを編集することなく実施できるようになった。また`hermes backup`と`hermes import`コマンドによる全設定のバックアップ・復元機能、`/debug`スラッシュコマンドや`hermes debug share`を使ったデバッグレポート共有機能も導入されている。さらにプラグイン可能なコンテキストエンジン、SOCKS対応の統合プロキシ、マルチアーキテクチャ（amd64+arm64）Dockerイメージのサポートも追加された。
