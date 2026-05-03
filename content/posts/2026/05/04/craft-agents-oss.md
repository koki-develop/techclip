---
date: "2026-05-04T02:21:41+09:00"
title: "Lukilabsがエージェントフレームワーク「Craft Agents」をApache 2.0でOSS公開、GitHubで5.7kスター獲得"
description: "Lukilabsが複数LLMプロバイダーとMCPサーバー統合を備えたデスクトップ向けエージェントフレームワーク「Craft Agents」をApache License 2.0でオープンソース公開し、公開直後にGitHubトレンド入りした。"
tags:
  - OSS
  - AI
references:
  - "https://github.com/lukilabs/craft-agents-oss"
---

## 概要

Craft DocsのLukilabsが、デスクトップアプリケーションとエージェントワークフロー環境を統合したフレームワーク「Craft Agents」をApache License 2.0のもとでオープンソース公開した。公開後すぐにGitHubのトレンドに入り、スター数は5,700件超、フォーク数は762件に達するなど、開発者コミュニティから広く注目されている。Craft AgentsはAnthropicのClaude Agent SDKを中核として構築されており、「エージェントネイティブソフトウェア原則」に基づいた直感的なマルチタスク処理、外部API・サービス接続、セッション共有、ドキュメント中心のワークフロー実現を目指している。

## 主な機能と技術スタック

Craft AgentsはElectronとReactによるデスクトップアプリで、ランタイムにはBun、UIフレームワークにはshadcn/uiとTailwind CSS v4を採用している。ソースコードのほぼ90%はTypeScriptで書かれており、モダンなWeb技術スタックで構成されている。

エージェントの権限管理には3段階モードを用意している。読み取り専用の「Explore」、変更前に確認を求める「Ask to Edit」、すべての操作を自動承認する「Auto」の3段階で、用途やリスク許容度に応じて切り替えられる。セッション管理機能としては、マルチセッションの受信箱、Todo・実行中・確認待ち・完了というワークフロー状態の管理、フラグ機能と自動生成タイトルが含まれる。

## データソース接続と対応LLMプロバイダー

外部データソースへの接続面では、MCPサーバーを通じたLinear・GitHub・Notionとの統合、REST API経由でのGoogle・Slack・Microsoft各サービスへの接続、ローカルファイルシステムへのアクセスをサポートしている。

対応するLLMプロバイダーも幅広く、Anthropic（APIキーまたはClaude Max OAuth）、Google AI Studio、ChatGPT Plus、GitHub Copilotへの直接接続に加え、OpenRouter・Vercel AI Gateway・Ollamaといったサードパーティゲートウェイやカスタムエンドポイントも利用可能だ。特定プロバイダーへのロックインを回避しながら多様なモデルを使い分けられる点が特徴となっている。

## 導入方法とライセンス

インストールは以下のワンラインコマンドで行える。

```bash
curl -fsSL https://agents.craft.do/install-app.sh | bash
```

ソースからビルドする場合は、リポジトリをクローンしたうえで`bun install`と`bun run electron:start`を実行すればよい。ライセンスはApache License 2.0で、商用・個人利用ともに自由に利用・改変・再配布できる。ただしClaude Agent SDKの利用にはAnthropicの商用利用規約が適用される点に注意が必要だ。「Craft」および「Craft Agents」の商標はCraft Docs Ltdが保有している。