---
date: "2026-08-24T02:04:01+09:00"
title: "GitHub Copilot for JetBrains、企業向け一元管理設定でプラグインやMCPサーバー接続を統制可能に"
description: "GitHub CopilotのJetBrains向けプラグインに企業向け一元管理設定機能が追加され、管理者がプラグイン許可やMCPサーバー接続、OpenTelemetry設定を集中管理できるようになった。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-08-18-enterprise-managed-settings-in-github-copilot-for-jetbrains/"
---

## 概要

GitHubは8月18日、JetBrains向けGitHub Copilotプラグインに企業向けの一元管理設定機能を追加したと発表した。これまで各開発者の端末ごとに個別設定されていたCopilotの挙動を、組織の管理者が集中的にコントロールできるようになり、エンタープライズ環境でのセキュリティとガバナンスの強化を狙った機能となっている。利用するには最新版のJetBrains向けGitHub Copilotプラグインが必要で、詳細な設定項目はエンタープライズ管理設定のリファレンスドキュメントで確認できる。

## 管理できる設定項目

新機能では、大きく分けて3つの領域を管理者が制御できる。1つ目はプラグインのガバナンスで、`enabledPlugins`によって特定のプラグインの有効・無効を強制したり、`extraKnownMarketplaces`で追加のプラグイン配布元を承認したり、`strictKnownMarketplaces`で承認済みの配布元以外からのインストールを制限したりできる。2つ目はMCP(Model Context Protocol)サーバーへの接続制御で、`allowedMcpServers`と`deniedMcpServers`を使い、開発者が接続できるMCPサーバーを組織側で一元的に指定し、未承認の接続を防止する。3つ目はOpenTelemetryの設定管理で、コレクターのエンドポイントやプロトコル、サービス名、リソース属性、コンテンツキャプチャのポリシーなどを管理者側から制御できる。管理者が設定した値は開発者側の個別設定より優先され、テレメトリデータが必ず承認済みのコレクターへ送信されるようになる。開発者はこれらの設定内容を「Settings > Tools > GitHub Copilot > Chat > OpenTelemetry」から確認できる。

## 権限モードの制御

このほか、`permissions.disableBypassPermissionsMode`を無効に設定することで、CopilotエージェントがBypass ApprovalsやAutopilotといった、承認プロセスを省略する機能を使用できないようにすることも可能になった。これにより、エージェントが自律的にコードを変更・実行する際にも、組織が定めた承認フローを強制できるようになる。

## 背景と今後

近年、AIコーディングアシスタントの企業導入が進む中で、MCPサーバーとの連携や自律的なエージェント機能の利用が広がっており、組織的なガバナンスの必要性が高まっている。今回のアップデートは、こうした管理ニーズに応えるもので、開発者の生産性を損なわずに組織全体でのポリシー適用を可能にする狙いがある。GitHubはフィードバックの窓口として、製品内フィードバックのほか、Copilot IntelliJ向けのフィードバックリポジトリやGitHub Community discussionsを案内しており、今後も管理機能の拡充が続く見込みだ。
