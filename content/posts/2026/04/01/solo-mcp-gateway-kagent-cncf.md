---
date: "2026-04-01"
title: "Solo.ioがkagentをCNCFに寄贈、AIエージェント向け「MCP Gateway」も発表"
description: "Solo.ioはKubeCon Europe 2026でKubernetes向けAIエージェントフレームワーク「kagent」のCNCFサンドボックス入りと、MCPに対応する新ツール「MCP Gateway」を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://thenewstack.io/solo-io-donates-kagent-to-cncf-introduces-mcp-gateway/"
  - "https://www.globenewswire.com/news-release/2026/03/25/3261972/0/en/Solo-io-Introduces-the-agentevals-Open-Source-Project-to-Bridge-the-Production-Reliability-Gap-for-Agentic-AI.html"
  - "https://cloudnativenow.com/kubecon-cloudnativecon-europe-2026/solo-io-launches-agentevals-open-source-project-contributes-agentregistry-to-cncf/"
---

## 概要

Solo.ioは2026年3月25日、アムステルダムで開催されたKubeCon + CloudNativeCon Europe 2026において、Kubernetes上でAIエージェントを実行するオープンソースフレームワーク「kagent」のCNCF（Cloud Native Computing Foundation）サンドボックスプロジェクトへの寄贈を正式に発表した。あわせて、AnthropicのModel Context Protocol（MCP）に対応した新ツール「MCP Gateway」も披露された。kagentはリリースからわずか1週間でCNCFのランドスケープ登録に必要な300 GitHubスターを達成し、最速クラスで成長しているCNCFサンドボックスプロジェクトの一つとなっている。

## kagentとMCP Gatewayの技術詳細

kagentは、AIエージェント・ツール・モデル設定をすべてKubernetes CRD（カスタムリソース定義）として管理するKubernetesネイティブなAIエージェントフレームワークである。Solo.ioがOSSとして公開してから100日間で100名以上のコントリビューター（85%以上が外部）と1,000以上のGitHubスターを獲得した。

MCP GatewayはAI開発で広く採用が進むMCPプロトコルに対応した新ツールで、複数のMCPツールサーバーを単一の安全なエンドポイントに集約（フェデレーション）する機能を持つ。Solo.io共同創業者兼CEOのIdit Levine氏はKubeCon基調講演でその意義を「すべてのツールサーバーを単一エンドポイントに統合できる」と説明した。MCP Gatewayはkgatewayとのタイトな統合が特徴で、上席OSS担当ディレクターのLin Sun氏は「kgatewayをMCP Gatewayプロキシのコントロールプレーンとして捉えることができる」と述べている。

## Solo.ioのアジェンティックインフラ戦略

Solo.ioはkagentのCNCF寄贈と並行して、AIエージェントインフラ全体をカバーするOSSエコシステムを構築している。その主要な4つの柱は以下のとおりである。

- **kagent** — KubernetesネイティブなAIエージェント構築・実行のためのCNCFサンドボックスプロジェクト
- **agentgateway** — MCPおよびA2A（Agent-to-Agent）プロトコルを完全サポートするLinux Foundation傘下のAIネイティブデータプレーン
- **agentregistry** — AIエージェント・MCPツール・エージェントスキルの一元的なCNCFレジストリ。KubeCon Europe 2026でCNCFへの寄贈が発表された
- **agentevals** — OpenTelemetryを活用してAIエージェントの動作を継続的に評価・スコアリングする新OSSプロジェクト

CEO Levine氏は「評価（evaluation）はアジェンティックインフラにおける最大の未解決問題だ」と述べ、agentevalsがプロダクション環境での信頼性確保を担う重要な位置づけにあることを強調した。

## 今後の展望

kagentはCNCFサンドボックスでインキュベーション申請が進行中であり、最新のCNCFテクノロジーレーダーのアジェンティックAI部門でも取り上げられている。agentregistryはKubernetes、AWS AgentCore、Google Vertex AIとの統合や、未統制のエージェントを検出するランタイムディスカバリ機能を備え、エンタープライズ規模でのAIガバナンスの基盤となることが期待される。KubeCon Europe 2026では「Agentics Day: MCP + Agents Hosted by CNCF」と題したハーフデイイベントも開催されるなど、KubernetesとAIエージェントの融合は急速に進んでいる。
