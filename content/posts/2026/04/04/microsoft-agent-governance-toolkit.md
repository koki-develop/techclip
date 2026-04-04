---
date: "2026-04-04T18:11:41+09:00"
title: "MicrosoftがAIエージェント向けランタイムセキュリティOSS「Agent Governance Toolkit」を公開、OWASP全10リスクに対応"
description: "MicrosoftがAIエージェントのランタイムセキュリティを提供するオープンソースプロジェクト「Agent Governance Toolkit」を公開し、7つのパッケージでOWASP Agentic Top 10の全リスクに対応する。"
tags:
  - AI
  - OSS
references:
  - "https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/"
---

## 概要

Microsoftは2026年4月2日、AIエージェント向けのランタイムセキュリティフレームワーク「Agent Governance Toolkit」をオープンソースとして公開した。フライト予約やコード実行、インフラ管理など自律的に動作するAIエージェントの普及に対し、ガバナンスの仕組みが追いついていないという課題に応えるもので、MITライセンスのもとGitHubで提供される。2025年12月に公開された「OWASP Top 10 for Agentic Applications」が示すゴールハイジャックやツール悪用、サプライチェーンリスクなど10のリスクすべてに対応するよう設計されており、EU AI Act（2026年8月施行）やコロラド州AI法（2026年6月施行）といった規制要件への対応も視野に入れている。

## 7パッケージ構成のアーキテクチャ

Agent Governance ToolkitはPython・TypeScript・Rust・Go・.NETに対応した7つのパッケージで構成され、`pip install agent-governance-toolkit[full]`で一括インストール、または個別に導入できる。各パッケージの役割は次のとおりだ。

- **Agent OS**: すべてのエージェントアクションを実行前にインターセプトするステートレスなポリシーエンジン。p99レイテンシは0.1ms未満。YAML・OPA Rego・Cedarのポリシー言語に対応。
- **Agent Mesh**: Ed25519暗号化による分散型識別子（DID）を用いたエージェントID管理と、エージェント間信頼プロトコル（IATP: Inter-Agent Trust Protocol）を実装。0〜1000スケールの動的トラストスコアリングで5段階の信頼ティアを管理する。
- **Agent Runtime**: CPUの特権レベルにヒントを得た動的実行リングと、マルチステップトランザクション向けのサガオーケストレーション、緊急エージェント停止機能を備える。
- **Agent SRE**: SLO・エラーバジェット・サーキットブレーカー・カオスエンジニアリングなど、SREのプラクティスをエージェントに適用。
- **Agent Compliance**: EU AI Act・HIPAA・SOC2への対応状況を自動検証し、OWASP Agentic AI Top 10のエビデンスも収集。
- **Agent Marketplace**: Ed25519署名によるプラグインのライフサイクル管理とサプライチェーンセキュリティを担う。
- **Agent Lightning**: 強化学習トレーニングにおいてポリシー違反ゼロを実現するポリシー強制ランナーと報酬整形機能を提供。

## 幅広いフレームワークとの統合

既存のエージェントフレームワークをリライトすることなく統合できる点が特徴で、LangChain・CrewAI・Google ADK・Microsoft Agent Framework・OpenAI Agents SDK・LangGraph・PydanticAI・LlamaIndexなどに向けたアダプターやプラグインが提供されている。またAzure Kubernetes Service（AKS）へのサイドカーコンテナとしての展開、Microsoft Foundry Agent ServiceやAzure Container Appsへの統合もサポートされている。

## 設計思想と今後の方向性

設計の柱として、カーネルやサービスメッシュ・SREの既存知見の活用、セキュリティをデフォルトとした実行パスへの組み込み、水平スケーリングと監査可能性を実現するステートレスアーキテクチャ、そして静的な信頼ではなく動的トラストスコアリングの4点が挙げられている。リポジトリには9,500件以上のテストが整備されており、ClusterFuzzLiteによる継続的ファジング、SLSA準拠のビルドプロベナンス、OpenSSF Scorecardによるセキュリティスコア追跡なども実装されている。Microsoftは将来的にOWASP・Linux Foundation AI & Data Foundation・CoSAIといったコミュニティ団体のもとにプロジェクトを移管することを目指しており、「エージェントガバナンスは単一ベンダーが管理するには重要すぎる」とコメントしている。
