---
date: "2026-07-01T02:40:55+09:00"
title: "Spring AI 2.0正式リリース——Java向けAIアプリ基盤が成熟、Spring Boot 4.1もgRPC・SSRF対策を追加"
description: "Spring AI 2.0がGAとなり、MCP統合やエージェント機能を強化。同時にリリースされたSpring Boot 4.1はgRPC自動設定・SSRF対策・Kotlin 2.3サポートを備える。"
tags:
  - Programming Languages
references:
  - "https://spring.io/blog/2026/06/30/this-week-in-spring-june-30-2026/"
  - "https://visualstudiomagazine.com/articles/2026/06/29/spring-ai-2-0-goes-ga-giving-java-developers-a-more-mature-ai-app-stack.aspx"
  - "https://spring.io/blog/2026/06/12/spring-ai-2-0-0-GA-available-now"
  - "https://spring.io/blog/2026/06/21/spring-boot-41-and-spring-batch"
  - "https://github.com/spring-projects/spring-boot/releases/tag/v4.1.0"
  - "https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-4.1-Release-Notes"
---

## Spring AI 2.0 GAの概要

Spring AI 2.0が2026年6月12日に正式リリース（GA）となり、Maven Centralから利用可能になった。Spring Boot 4.0/4.1およびSpring Framework 7.0を前提とし、Javaエコシステム向けのAIアプリケーション開発基盤として大きく成熟した。Jackson 3へのアップグレードによりJSONシリアライゼーションが改善され、JSpecify注釈による完全なNull安全性も導入されている。オプション処理はビルダーパターンとイミュータブル設計で大規模にリファクタリングされ、コードの予測可能性が高まった。

対応するAIプロバイダーはOpenAI・Anthropic・Amazon Bedrock・Google GenAI・Mistral AI・DeepSeek・Ollamaなど多岐にわたり、各プロバイダーはSDK単一バージョンに統一されて依存関係が整理されている。Azure CosmosDBとのベクター検索統合もサポートされ、RAG（Retrieval-Augmented Generation）パターンの実装が容易になった。

## エージェント機能とMCP統合

Spring AI 2.0ではエージェント開発向けの機能が強化された。`ToolCallingAdvisor`がアドバイザーチェーンに統合され、ツール呼び出しの全ラウンドトリップを一元管理できる。`ToolSearchToolCallingAdvisor`は数百ものツールへのスケーリングを可能にし、大規模なエージェント設計を支援する。また`StructuredOutputValidationAdvisor`は自動修正機能付きの構造化出力バリデーションを提供し、LLMの出力を型安全に扱うユースケースで活用できる。

Model Context Protocol（MCP）はAI統合の共通プロトコルとして定着しつつあり、Spring AIはMCP Java SDK 2.0.0を搭載した。`@McpTool`などの注釈駆動プログラミングモデルが利用可能で、既存のSpringコンポーネントをMCPツールとして公開する作業が大幅に簡略化されている。コミュニティからはElevenLabsを使った音声統合、自己修正型の構造化出力、エージェントスキル構築に関するコンテンツも公開されており、実用事例の蓄積が進んでいる。

## Spring Boot 4.1の主な新機能

Spring Boot 4.1も同時期にリリースされ、多数の機能追加とCVEパッチが含まれている。注目すべき新機能の一つがgRPCの自動設定で、NettyバックのスタンドアロンサーバーとHTTP/2上でのServlet統合の両方に対応する。これまでgRPCをSpring Bootと組み合わせるには手動設定が必要だったが、スターター依存関係と少量のプロパティ設定だけで動作するようになった。

セキュリティ面ではSSRF（Server-Side Request Forgery）対策として`InetAddressFilter`が追加された。リアクティブおよびブロッキング両方のHTTPクライアントで特定アドレスへの送信リクエストをブロックでき、クラウド環境のメタデータエンドポイントへの意図しないアクセスを防ぐのに役立つ。その他のセキュリティ改善としてLDAP組み込みサーバーへのLDAPS（SSL）サポートやRabbitMQ StreamsへのSSL自動設定も含まれている。

## MongoDB連携とKotlin 2.3サポート

Spring Boot 4.1の目玉機能の一つがSpring BatchのMongoDBバックエンド対応だ。新たに追加された`spring-boot-starter-batch-data-mongodb`により、これまでバッチ処理のメタデータ保存にJDBCデータベースが必須だった制約が解消された。MongoDBのみで運用するチームが別途リレーショナルDBを維持する必要がなくなり、インフラの簡素化が期待できる。ただしMongoDBのトランザクションサポートのためにレプリカセット構成が前提となる点は注意が必要だ。

Kotlin対応ではKotlin 2.3.21とKotlin Serialization 1.11.0が採用された。また`spring.datasource.connection-fetch=lazy`プロパティによる遅延DataSource接続の設定が可能になり、不必要な接続初期化を避けてリソース消費を抑制できる。GraalVMネイティブイメージ向けのサポートも改善され、Spring Batchコンポーネントでランタイムヒントが自動登録されるようになった。一方でDerbyデータベースのサポートは非推奨化され、H2またはHSQLへの移行が推奨されている。

## セキュリティリリースの加速と今後の展望

「This Week in Spring」でJosh Longは、2026年を通じてCVEパッチのリリース頻度が劇的に増加していることを強調した。AIが脆弱性の特定プロセスを大幅に効率化したことで、従来の月1〜2件から大量のCVEが報告されるようになっており、アプリケーションのアップグレードをMaven Centralへのパッチ反映後すみやかに行う重要性が増している。Spring AI 2.0とSpring Boot 4.1のリリースにより、JavaエコシステムはAI時代のアプリケーション開発に向けた成熟した基盤を持つこととなった。
