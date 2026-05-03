---
date: "2026-05-04T02:21:41+09:00"
title: "MCPがLinux Foundationへ移管――AAIF設立でAnthropicら主要AI企業が中立ガバナンスを構築"
description: "Linux FoundationがAgentic AI Foundation（AAIF）を設立し、AnthropicのMCPをはじめとするAIエージェント関連プロジェクトが中立的なオープンガバナンス下に置かれた。"
tags:
  - OSS
  - AI
references:
  - "https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation"
  - "https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/"
---

## 概要

Linux Foundationは2025年12月9日、**Agentic AI Foundation（AAIF）**の設立を発表した。AIシステムが会話型アシスタントから自律的なエージェントへと急速に進化するなか、透明性と相互運用性を担保する中立プラットフォームの必要性に応える形での設立となる。初期プロジェクトとして、AnthropicのModel Context Protocol（MCP）、BlockのオープンソースAIエージェントフレームワーク「goose」、OpenAIが提案するAIコーディングエージェント向け仕様「AGENTS.md」の3プロジェクトが寄贈された。プラチナム会員にはAmazon Web Services、Anthropic、Block、Bloomberg、Cloudflare、Google、Microsoft、OpenAIが名を連ね、主要AIプレイヤーが共同でガバナンスを担う体制が整った。

## MCPが解決してきた課題

MCPはAnthropicが開発したオープン標準で、AIモデルが外部ツールやデータソースと安全に接続するためのプロトコルを定義している。登場以前、AIエージェント開発者は「n×m統合問題」に悩まされていた。5つのAIクライアントが10の内部システムと連携するだけで、認証やエラー処理の異なる50通りの個別実装が必要になる計算だ。MCPはこの問題をスキーマ駆動のインターフェース（JSON Schema）、OAuth対応のセキュアなリモート接続、予測可能なツール呼び出し、長時間タスクのサポートといった仕様を統一することで解消した。現在は10,000以上のMCPサーバーが公開されており、Claude、Cursor、Microsoft Copilot、Geminiをはじめとする主要AIプロダクトで採用が進んでいる。

## 急速な普及とLinux Foundation移管の意義

2025年のGitHub Octoverse報告によれば、LLM SDKをインポートするリポジトリは113万件に達し、AIリポジトリの新規作成は69万3,000件を記録した。MCPは公開から8か月足らずで3万7,000スターを獲得し、月間インストール数は9,700万件に及ぶ。Linux FoundationへのMCP移管は、開発者にとって長期的な安定性、企業規模を問わない平等な参加、互換性の保証、エンタープライズ向けのオープンスタンダードガバナンスといった実質的な恩恵をもたらす。この位置づけはKubernetesやSPDXといったクリティカルインフラと並ぶものとして評価されている。

## 今後の展望

AAIFはLinux Foundationの中立的な管理のもと、各プロジェクトの独立性と透明性を確保しながら標準策定を進める。MCP Dev Summitなどのコミュニティイベントも開催予定で、エコシステム全体での協調開発が加速する見通しだ。開発者は1つのMCPサーバーを複数のAIクライアントで再利用でき、テスト・デバッグが容易な標準化されたツール連携の恩恵を享受できる。独占的なプロプライエタリ解決策ではなく、契約ベースのオープン標準としてAIエージェント統合の基盤が確立されつつある。
