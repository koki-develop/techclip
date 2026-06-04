---
date: "2026-06-05T02:55:55+09:00"
title: "GitHub Copilot SDKが一般提供開始、6言語対応でアプリへのエージェント機能組み込みが可能に"
description: "GitHubはCopilot SDKの一般提供（GA）を発表し、Node.js/TypeScript・Python・Go・.NET・Rust・Javaの6言語向けに安定版APIを公開した。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-06-02-copilot-sdk-is-now-generally-available/"
---

## 概要

GitHubは2026年6月2日、GitHub Copilot SDKの一般提供（GA）開始を発表した。開発者は自前のアプリケーションやサービスにGitHub Copilotのアジェントエンジンを組み込めるようになり、プランニング・ツール呼び出し・ファイル編集・ストリーミングといったエージェントランタイム機能を活用できる。対応言語はNode.js/TypeScript・Python・Go・.NET・Rust・Javaの6言語で、各言語向けのパッケージマネージャー経由でインストール可能だ。

## 対応言語とインストール方法

各言語のインストールコマンドは以下の通り。Node.js/TypeScriptは`npm install @github/copilot-sdk`、Pythonは`pip install github-copilot-sdk`、Goは`go get github.com/github/copilot-sdk/go`、.NETは`dotnet add package GitHub.Copilot.SDK`で導入できる。RustとJavaはGA時に新たに追加された言語で、JavaはMavenおよびGradle経由で利用可能となっている。

## 主な機能と技術的詳細

SDKが提供する主要機能として、カスタムツールの定義、Model Context Protocol（MCP）サーバーへの接続、システムプロンプトの細粒度カスタマイズが挙げられる。そのほかにも、OpenTelemetryによるトレーシング、柔軟な認証オプション、クラウドセッション管理、フック機構への対応が含まれており、本番環境での運用を見据えた機能セットが整っている。

## 背景と利用可能性

SDKはパブリックプレビュー段階から開発者によって活用されており、CI/CDアシスタントや社内開発ツール、顧客向けのAI機能構築などの用途で実績を積んできた。GAへの移行により、APIの安定性が保証され、より本番環境への採用が進むと見られる。利用資格は既存のCopilotサブスクライバー（無料プランを含む）およびBYOK（Bring Your Own Key）ユーザーに開放されており、追加費用なく今日から利用を開始できる。
