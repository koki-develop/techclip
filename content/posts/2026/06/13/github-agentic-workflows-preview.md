---
date: "2026-06-13T02:49:00+09:00"
title: "GitHub Agentic Workflowsがパブリックプレビューへ昇格、PAT不要でActionsにAIエージェント自動化を統合"
description: "GitHubがAgentic Workflowsをパブリックプレビューへ移行し、自然言語のMarkdownでIssueトリアージやCI失敗分析などの推論タスクをGitHub Actions内で自動化できるようになった。個人アクセストークン（PAT）も不要になり、組み込みのGITHUB_TOKENで運用できる。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-06-11-github-agentic-workflows-is-now-in-public-preview/"
  - "https://github.blog/changelog/2026-06-11-agentic-workflows-no-longer-need-a-personal-access-token/"
---

## 概要

GitHubは2026年6月11日、Agentic Workflowsをパブリックプレビューへと昇格させた。これにより、IssueのトリアージやCI失敗の分析、ドキュメントの更新といった推論ベースの繰り返しタスクを、GitHub Actions内のAIコーディングエージェントで自動化できるようになった。ワークフローは自然言語のMarkdownファイルで定義でき、標準的なActions YAMLへ自動コンパイルされる仕組みのため、既存のランナーグループやポリシー制約をそのまま活用できる。

同時に、Agentic Workflowsで従来必要だった個人アクセストークン（PAT）が不要になったことも発表された。代わりにGitHub Actionsの組み込み`GITHUB_TOKEN`が利用可能になり、長期存続するPATの管理コストとセキュリティリスクを削減できる。

## 技術的な詳細

Agentic Workflowsはサンドボックス環境内で実行され、セキュリティ面では多層的な保護機構が備わっている。Agent Workflow Firewall、safe outputsプロセス、threat detection jobが組み合わさっており、エージェントはデフォルトで読み取り専用の権限で動作する。GitHubコンテンツへのアクセス時にはintegrity filterルールが尊重される。

PAT不要化にあたっては、組織所有リポジトリで利用する際にいくつかの設定変更が必要となる。具体的には「Allow use of Copilot CLI billed to the organization」ポリシーを有効化し、ワークフローのMarkdownの権限セクションに`copilot-requests: write`を追加する。また、CLIを最新版へアップグレードするには`gh extension upgrade aw`コマンドを実行する。コスト管理の観点では、コストセンターの設定により複数組織への費用配分やワークフロー単位でのトークン使用量監視・上限設定も可能だ。

## 導入事例と利用可能なプラン

すでに複数の企業が本機能を採用しており、Marks & Spencerは「何時間もかかっていた繰り返し作業が数分で自動完了できるようになった」と報告。CarvanaやHud.ioも事例として挙げられており、開発生産性の向上と信頼性確保の両立が評価されている。Agentic WorkflowsはCopilotのFreeからEnterpriseまで全プランで利用可能。公式のクイックスタートガイドやGitHubNextの事前構築済みワークフロー例も提供されており、導入の敷居は低い。
