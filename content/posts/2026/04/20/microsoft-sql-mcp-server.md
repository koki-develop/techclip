---
date: "2026-04-20T02:17:42+09:00"
title: "MicrosoftがSQL MCP Serverをオープンソース公開、PostgreSQL・MySQL・Azure DBなど6種類に対応"
description: "MicrosoftがAIエージェントから複数DBへの横断的な問い合わせを可能にする「SQL MCP Server」をオープンソースで公開した。"
tags:
  - OSS
  - Cloud
references:
  - "https://www.publickey1.jp/blog/26/postgresqlmysqlsql_serversql_mcp_server.html"
---

## 概要

Microsoftは2026年4月、AIエージェントが複数のデータベースに対してModel Context Protocol（MCP）経由で横断的に問い合わせを実行できる「SQL MCP Server」をオープンソースで公開した。PostgreSQL・MySQL・SQL Serverといった主要なデータベースから、Azure SQL Database・Azure SQL Data Warehouse・Azure Cosmos DBといったMicrosoftのマネージドサービスまで、6種類のデータベースへの同時接続に対応している。

## 技術的な詳細

SQL MCP ServerはMicrosoftのオープンソースプロジェクト「Data API builder for Azure Databases」の一部として提供される。Data API builderは、各種データベースに対してRESTful API・GraphQL・MCPの3つのアクセス手段を統一的に提供するプラットフォームであり、SQL MCP ServerはそのMCPサポートを担うコンポーネントとして位置づけられる。

オープンソースであるため、オンプレミス環境はもちろん、Microsoft AzureやAWSなど任意のクラウド環境でも無償で利用・展開できる。複数データベースへの同時接続をサポートしているため、AIエージェントが異なる種類のデータベースをまたいで情報を収集・統合するユースケースにも対応する。

## 背景と意義

MCPはAnthropic社が提唱したオープンプロトコルで、AIエージェントが外部ツールやデータソースと標準化された方法でやり取りするための仕様だ。MicrosoftがSQL MCP Serverを公開したことで、企業の既存データベース資産をAIエージェントから直接活用しやすくなり、MCPエコシステムのデータ活用領域がさらに拡充された形となる。Data API builderを通じてGraphQLやRESTによるアクセスも同時に提供されるため、AIエージェント以外のユースケースとも統一的なインフラとして機能する点も注目される。
