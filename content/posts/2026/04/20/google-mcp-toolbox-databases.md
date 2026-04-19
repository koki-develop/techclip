---
date: "2026-04-20T02:17:42+09:00"
title: "Google MCP Toolbox for Databases v1.0、40以上のデータソースに対応しModel Context Protocolを正式サポート"
description: "GoogleのデータベースアクセスOSSであるMCP Toolbox for DatabasesがModel Context Protocolに正式対応し、v1.0としてリリース。AlloyDBやSpanner、Oracle、MongoDBなど40以上のデータソースをAIエージェントから安全に利用できる。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/ai-machine-learning/mcp-toolbox-for-databases-now-supports-model-context-protocol"
  - "https://medium.com/google-cloud/mcp-toolbox-v1-0-the-open-source-framework-for-secure-agentic-data-access-3c2199546ba8"
  - "https://github.com/googleapis/mcp-toolbox"
---

## 概要

Googleは2026年4月、オープンソースのデータベース連携フレームワーク「MCP Toolbox for Databases」がModel Context Protocol（MCP）に正式対応し、バージョン1.0としてリリースされたことを発表した。旧称は「Gen AI Toolbox for Databases」で、今回のリリースを機に名称もMCPとの統合を反映したものへ変更された。MCP（Model Context Protocol）はAnthropicが策定したAIシステムと外部データソースを接続するためのオープン標準であり、AIモデルと外部ツール間のユニバーサルインターフェースとして機能する。このプロトコルがLinux Foundation傘下のAgentic AI Foundation（AAIF）に参加したことで、業界標準としての地位が確立されつつある。

## 対応データソースとSDK

v1.0では40以上のデータソースへのネイティブ接続が可能となった。Googleクラウドのデータベース群（AlloyDB、Spanner、BigQuery、Cloud SQL for PostgreSQL/MySQL/SQL Server、Bigtable）に加え、Oracle、MongoDB、Snowflake、自己ホスト型のPostgreSQLやMySQLといったサードパーティシステムも幅広くサポートする。クライアントSDKはPython、Go、TypeScript/JavaScript、および今回新たに追加されたJavaの4言語で提供されており、LangChain、LlamaIndex、Agent Development Kit（ADK）との深い統合も実現している。

## セキュリティと可観測性の設計

本フレームワークの設計思想の中核にあるのは、「確率的なLLMと決定論的な本番データベースの間の信頼ギャップを埋める」という考え方だ。AIエージェントに生のデータベースアクセスを直接与えることの危険性を回避するため、宣言的な設定ファイル（`config.yaml`）でアクセス可能なアクションを明示的に定義する。テナントIDなどの機密パラメータはサーバー側でランタイムに注入され、言語モデルの制御外に置かれる。また、OAuth 2.1リソースサーバーとして機能し、自動ディスカバリーと厳密なトークン検証によるアクセス制御を実現する。可観測性の面ではOpenTelemetryを統合し、エージェントとデータベース間のすべてのインタラクションをトレース・メトリクス・ログとして記録できる。

## 今後の展望

v1.0の安定版リリースにより、開発チームはアップストリームの破壊的変更を心配せずにMCP Toolboxを基盤としたエージェント型アプリケーションを構築できるようになる。今回の正式リリースはGoogle Cloud Next 2026（ラスベガス）でも取り上げられる予定で、「Power Intelligent Agents with AI-Native Databases」セッションにて詳細が紹介される見込みだ。プロジェクトはGitHub上でオープンソースとして開発が続けられており、コミュニティへの参加も積極的に歓迎されている。
