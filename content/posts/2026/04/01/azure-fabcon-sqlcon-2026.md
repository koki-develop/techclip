---
date: "2026-04-01"
title: "FabCon/SQLCon 2026：MicrosoftがFabricとSQLを統合する単一データプラットフォームの新機能を多数発表"
description: "MicrosoftはFabCon/SQLCon 2026で、OneLakeを中心にデータベース・分析・AIを統合するDatabase Hub、Fabric IQ、MCP対応など多数の新機能を発表した。"
tags:
  - Cloud
references:
  - "https://azure.microsoft.com/en-us/blog/fabcon-and-sqlcon-2026-unifying-databases-and-fabric-on-a-single-data-platform/"
---

## 概要

第3回FabConと初開催のSQLConがアトランタ（ジョージア州）で合同開催され、約8,000名が参加した。Microsoftはこの場で「SQL Serverは置き換えられるのではなく、格上げされる」というメッセージを軸に、SQL Server・Azure SQL・Microsoft FabricをAI対応の統一データプラットフォームへ収斂させる方針を明確に打ち出した。FabricはGA（一般提供開始）から約2年半で31,000社以上に採用されており、Microsoftのデータプラットフォーム史上最速の成長を記録している。SQL Server 2025の採用速度も前バージョンの2倍に達しているという。

## 新機能の詳細

今回の発表で中心的な位置を占めるのが**Database Hub in Fabric**（アーリーアクセス）だ。Azure SQL、Azure Cosmos DB、Azure Database for PostgreSQL、SQL Server（Azure Arc経由）、Azure Database for MySQL、Fabric databasesなど、エッジ・PaaS・Fabric全体のデータベースを一元管理するUXを提供する。探索・監視・ガバナンス・最適化をひとつの画面から実行できる。

**OneLakeセキュリティ**は数週間以内のGA（一般提供）が予告された。行・列レベルのアクセス制御と統合権限モデルを備え、Sparkノートブックや Power BIレポート、Fabric data agentなど全アナリティクス経験を横断して権限を自動適用する。ショートカット・ミラーリング機能によりAWS、Google Cloud、Oracle、オンプレミス、SAP、Snowflake、Azure Databricksへのゼロコピー・ゼロETL接続も可能になる。

分析データと運用データ（テレメトリ・時系列・グラフ・地理空間データ）を統合するセマンティックフレームワーク**Fabric IQ**も注目の発表だ。テーブルやスキーマではなくビジネスエンティティ・関係・プロパティ・ルール・アクションのオントロジーで操作でき、近日中にMCPサーバー（プレビュー）として公開予定。AIエージェントがセマンティックレイヤーを発見・理解・操作できるようになる。

## AIエージェント連携とMCP対応

**Fabric MCP（Model Context Protocol）**では2種類のサーバーが用意された。**Fabric local MCP**はすでにGAしており、GitHub CopilotなどAIコーディングアシスタントをFabricに直接接続するOSSローカルサーバーとして提供される。既存のRBACに準拠しながら権限管理やワークスペース作成、定義の活用が可能だ。一方の**Fabric remote MCP**はパブリックプレビューで、AIエージェントや自動化ツールがFabric内で認証済みアクションを実行できるセキュアなクラウドホスト実行エンジンを提供する。

**Power BI: Translytical Task Flows**がGAとなり、レポートから直接ワークフローをトリガーしてデータ課題を解決できるようになった。手動でのリクエスト提出が不要になり、分析と運用の融合を体現する機能として位置づけられている。また、Azure Data Factory・Synapse Analytics・Azure SQL向けの**移行アシスタント**（パブリックプレビュー）も発表され、AI支援の互換性チェックによりパイプライン・ノートブック・DBスキーマをFabricへ移行できるようになった。

## 今後の展望

OneLakeセキュリティのGAや Fabric IQ MCPサーバーのプレビュー公開が直近の予定として示されており、データプラットフォームとAIエージェントの統合はさらに加速する見通しだ。次回のFabCon/SQLConはヨーロッパ大会として2026年9月28日〜10月1日にスペイン・バルセロナで開催される予定。
